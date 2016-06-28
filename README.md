# Cheat Sheet

This document is a dump of information written to help people getting into software development overcome some of the hurdles.

## In the Beginning

There are a few important things to know about computers and your interactions with them.

### Binary Data

Everything in a computer, at it's lowest level, is a bunch of 1s and 0s.  **[Everything](https://en.wikipedia.org/wiki/Binary_data#In_computer_science)**.  All else is built on top of that principle.  To go from 1s and 0s to higher level information requires the use on an [encoding system](https://en.wikipedia.org/wiki/Code).  One such example of this is [ASCII](https://en.wikipedia.org/wiki/ASCII).  ASCII is used to represent a small set of characters (alphanumeric and some symbols).  Using ASCII, the capital letter `A` is stored in a computer as `00101001`.

#### Encodings

There are many different types of encodings.  Text can be stored as [ASCII](https://en.wikipedia.org/wiki/ASCII) or [UTF-8](https://en.wikipedia.org/wiki/UTF-8).  Colors can be stored as [RGB](https://en.wikipedia.org/wiki/RGB_color_model) in [hex](https://en.wikipedia.org/wiki/Hexadecimal). (Teal is `#00FFFF`, which is `0000 0000 1111 1111 1111 1111` in binary)  It is not important to know all the different kinds of encodings, just that they exist, that they can be layered on top of each other, and that at the very bottom is _always_ binary.

### Computers are DUMB

Not in a coolness factor way, in an intelligence way.  They have an IQ of 0.  _But Joe, I've seen a lot of really complex things on computers! They're smart!_ No, they aren't.  A **HUMAN** wrote very complex code that is impressive, they computer is just reading a bunch of 1s and 0s.  *Most* problems you will encounter as a developer are a result of a computer not understanding you.  You may find yourself saying "The computer isn't doing what I'm telling it!", but that is never true.  The correct statement is "The computer isn't doing what I _want_ it to do.", and that's because you're not telling it what to do correctly.

### Storing Information

Permanent information stored on your [hard drive](https://en.wikipedia.org/wiki/Hard_disk_drive) is made up of files and folders (also commonly known as "directories").  Directories can have other directories and files within them.  These files and directories are saved as binary data onto the disk, and it's important to keep in mind that all information on a computer is a bunch of files and directories when you're working with it later.

## Interfacing with a Computer

There are many different ways to interface with a computer.  There are two levels of interfacing: hardware and software.  Most commonly people use a monitor, keyboard, and mouse as their hardware.  On the software side, most people use a [desktop environment](https://en.wikipedia.org/wiki/Desktop_environment), which if you're coming from OS X or Windows you may just call "the desktop".  This is a [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) built on top of a computer's [operating system](https://en.wikipedia.org/wiki/Operating_system).  But, there are other ways.

### Shells

The desktop environment previously mentioned is a GUI [shell](https://en.wikipedia.org/wiki/Shell_(computing\)).  The name is picked for a reason, as it's a wrapper around the operating system, also called the [kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system\)).  It is common among experienced programmers to use a CLI shell because it is closer to the kernel beneath it, making it more powerful and capable than any GUI.  While it will take some time to learn, you will eventually be able to do far more than any GUI would allow you to do.

To run a CLI shell, you will often times do this within a GUI shell.  This may seem kind of silly, but it is common practice.  OS X comes with [Terminal](https://en.wikipedia.org/wiki/Terminal_(OS_X)) pre-installed to allow you to do this, though [iTerm2](https://www.iterm2.com/) is considered superior by many.  If you're just getting started out, you can use either one.

###### Popular CLI shells:

* [sh](https://en.wikipedia.org/wiki/Bourne_shell) - The Bourne Shell
* [bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell\)) - **B**ourne **A**gain **SH**ell
* [fish](https://en.wikipedia.org/wiki/Friendly_interactive_shell)
* [zsh](https://en.wikipedia.org/wiki/Z_shell) - "The last shell you'll ever need"

#### The Prompt

![](http://news.softpedia.com/images/reviews/large/bash_tutorial-img1-large.png)

With a GUI shell (or desktop), you click on things, drag them around, type in text boxes.  With a CLI shell, you are just given a "[prompt](https://en.wikibooks.org/wiki/Guide_to_Unix/Explanations/Shell_Prompt)".  Put simply, this is a space where you can type in text, tell the computer to process that text (usually be pressing the Enter key), and then have it spit back out information.

There are a few key things to know about the prompt.  First, there is the `PS1`. This is a few pieces of information about you, the computer you are connected to, and where are *are*.  For example, mine says `joseph.pintozzi@JPINT1ML1 ~`.  `joseph.pintozzi` is the user name that I am logged in as.  Then the `@` symbol tells me the next bit of information is where I am "at", the computer's hostname. `JPINT1ML1` is the name of my laptop.  The last piece, `~`, tells me where my prompt/shell is currently on my hard drive.  `~` is shorthand notation for "my user's home directory".  On OS X, this is `/Users/USER_NAME_HERE`, so for me `~` means `/Users/joseph.pintozzi`.  A `PS1` can be changed, though most users leave theirs as the default.

Second, the prompt has a "current working directory".  When you start a shell, by default it will start in your home directory, mentioned above.  If you run a command or program, it will be default use information within the directory you are in, though you can move around by issuing commands to the shell.

Lastly, there are pieces of information contained within a shell known as [environment variables](https://en.wikipedia.org/wiki/Environment_variable).  You can see these by running the command `export` on OS X.  Each line is one environment variable, with the name of the variable on the left of the `=`, and the value for that variable to the right.  Common variables you should be able to see are `HOME`, `PWD`, and `USER`.

#### CLI Programs

Just like there are GUI programs (Google Chrome, Microsoft Word, etc), there are CLI programs.  To run them, you type them into your prompt, press enter, and see the results.  You can open up `Terminal.app` and type these things in to run them.

###### Common CLI Programs

* [cd](https://en.wikipedia.org/wiki/Cd_(command\)) - **C**hange **D**irectory
* [ls](https://en.wikipedia.org/wiki/Ls) - **L**i**S**t the files and directories of where you are
* [pwd](https://en.wikipedia.org/wiki/Pwd) - **P**rint **W**orking **D**irectory
* [curl](https://en.wikipedia.org/wiki/CURL) - **C**lient for **URL**s
* [wget](https://en.wikipedia.org/wiki/Wget) - **W**orld Wide Web **GET**

#### The PATH

`PATH` is an environment variable (mentioned above) that is primarily used as a **search path** for when you're submitting commands to the shell.  Specifically, `PATH` is a string of colon (`:`) separated locations that the prompt should look for files and binaries when you run a command.  An example `PATH` is `/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin`.

When a prompt executes a command, it first looks in the current directory to see if it can find a program there it should run.  If it fails to do that, it falls back to the `PATH` and checks each directory (**IN ORDER!**) to see if it can find a program that the name you typed it.  What this means, is that when you type `ls` into your prompt (using the example `PATH` from above), it first checks in your current directory to see if it can find a program named `ls`, then it checks `/usr/local/bin`, then it checks `/usr/bin`, etc, all the way until it _finds_ `ls` and then executes it.


#### RTFM

When looking for help, or asking someone online, you may encounter the anagram [RTFM](https://en.wikipedia.org/wiki/RTFM), which stands for "read the fucking manual".  This may sound harsh, but is a wise piece of advice.  Most CLI programs come with a [manual](https://en.wikipedia.org/wiki/Man_page), accessed by running `man OTHER_PROGRAM_NAME_HERE`.  If you wanted to read the manual for `cd`, you would run `man cd`, and it would give you all of the important information related to `cd`.

##### Exiting

Most CLI programs run for a while, and then exit automatically, spitting out the information you were looking for.  Some programs don't and only quit when you tell them to (such as `tail`, `watch`, and `less`).  This is typically done through either pressing `Q` (for quit) or `Ctrl + C`.


-------
* Command history
* Rubber Ducky debugging
* Useful links (rubular, explainshell)



