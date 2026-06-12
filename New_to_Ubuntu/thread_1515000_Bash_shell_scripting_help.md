---
title: "Bash shell scripting help"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by Crazedpsyc on 2010-06-21
Hello, I'm writing a shell script to make the terminal look and function like a windows command prompt (disgusting, but requested). So far everything has been pretty fun and easy, like getting the color command to work, but how do I make it do these two things:

1: Get prev command on up arrow
2: Put a C:\ at the beginning of `pwd`

on number two, I have
```

prompt=$(pwd | sed "s/\//\\\\/g" | sed "s/\\\\home/C:\\\\Users/g")
read -e -p "$prompt>" comand mod1 mod2 mod3

```
which shows C:\Users\me\Desktop> when I am in my desktop or anything else in /home, but shows just \whatever when I am in /whatever

but for number 1, I have no ideas. the complete script is below
```

#!/bin/bash
# Stuff that happens before the prompt
printf "\n"
myfgcolor=$(cat ~/.cmdcolors | grep "fgcolor=" | sed "s/fgcolor=//g")
mybgcolor=$(cat ~/.cmdcolors | grep "bgcolor=" | sed "s/bgcolor=//g")
if [ "$myfgcolor" = "" ]
then
myfgcolor="7"
fi
if [ "$mybgcolor" = "" ]
then
mybgcolor="0"
fi
printf " \b"
tput setaf $myfgcolor
tput setab $mybgcolor
printf " \b"
printf " \b"
slashstuff=$(ls)
prompt=$(pwd | sed "s/\//\\\\/g" | sed "s/\n\\\\/C:\\\\/g" | sed "s/\\\\home/C:\\\\Users/g")
read -e -p "$prompt>" comand mod1 mod2 mod3
if [ "$comand" = "help" -a "$mod1" = "" ]
then
echo "
#the win help (exluded bcuz of length)
elif [ "$comand" = "ping" ]
then
ping -c 4 -s 24 $mod1
elif [ "$comand" = "color" -a "$mod1" = "" ]
then
printf ""
elif [ "$comand" = "color" -a "$mod1" = "/?" ]
then
echo "Sets the default console foreground and background colors.

COLOR [attr]

  attr        Specifies color attribute of console output

Color attributes are specified by TWO hex digits -- the first
corresponds to the background; the second the foreground.  Each digit
can be any of the following values:

    0 = Black       8 = Gray
    1 = Blue        9 = Light Blue
    2 = Green       A = Light Green
    3 = Aqua        B = Light Aqua
    4 = Red         C = Light Red
    5 = Purple      D = Light Purple
    6 = Yellow      E = Light Yellow
    7 = White       F = Bright White

If no argument is given, this command restores the color to what it was
when CMD.EXE started.  This value either comes from the current console
window, the /T command line switch or from the DefaultColor registry
value."
read -s -e -p "Press any key to continue..." -n 1
echo "The COLOR command sets ERRORLEVEL to 1 if an attempt is made to execute
the COLOR command with a foreground and background color that are the
same.

Example: \"COLOR fc\" produces light red on bright white"
elif [ "$comand" = "color" -a "$mod1" != "" -a "$mod1" != "/?" ]
then
## Copy an "elif" section and replace the color codes like "70" and "07" as well as the values for '$myfgcolor' and '$mybgcolor' to add new colors ##
# White on Black
    if [ "$mod1" = "07" ]
    then
    mybgcolor="0"
    myfgcolor="7"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmdcolors
clear
# Black on White
    elif [ "$mod1" = "70" ]
    then
    mybgcolor="7"
    myfgcolor="0"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmdcolors
clear
# etc...
    fi
elif [ "$comand" = "start" ]
then
~/Desktop/start $mod1
else
$comand $mod1 $mod2 $mod3
fi
~/Desktop/cmd.exe

```

---

### Post by lkjoel on 2010-06-21
I don't understand what you mean, but I received another error.
I think it is on these lines:
```
bgcolor=$mybgcolor" > ~/.cmdcolors
clear
# etc...
    fi
elif [ "$comand" = "start" ]
then
~/Desktop/start $mod1
else
$comand $mod1 $mod2 $mod3
fi
~/Desktop/cmd.exe
```84-end.
Do you mean on line 84
```
bgcolor=$mybgcolor" > ~/.cmdcolors[COLOR=Red]**"**[/COLOR]
```

---

### Post by Crazedpsyc on 2010-06-22
the point is to make all the most useful DOS commands work in a linux terminal, so windows users are happier. the error was just that I forgot a ] in one spot and a then in another spot, I don't know what youre talking about on the second code spot, that is just where i set the bgcolor in a text file so it resumes in that color each time.

---

### Post by ibuclaw on 2010-06-22
OK... prejudice aside about the whole ethos of your help question. Only one thing strikes me as not quite right.
  
> **Crazedpsyc said:**
> "s/\\\\home/C:\\\\Users/g"
Why lie about the directory you are in?

---

### Post by Crazedpsyc on 2010-06-23
lol, there is not home directory in Windows, but the users directory is about the same, and it makes windows users feel comfier. as you can see that is the only thing that is different. I have also now added an option to change that part in the setup script

---

### Post by bodhi.zazen on 2010-06-23
> **Crazedpsyc said:**
> lol, there is not home directory in Windows, but the users directory is about the same, and it makes windows users feel comfier. as you can see that is the only thing that is different. I have also now added an option to change that part in the setup script

I do not know any windows users who are comfortable with the command prompt.

:lolflag:

---

### Post by Crazedpsyc on 2010-06-23
I think this will help capture keys and use them as events , but I have to add it to the read prompt as well:
```

#!/bin/ksh
AWK=gawk
[ -x /bin/nawk ] && AWK=nawk
ECHO="print"
ECHO_N="print -n"

tty_save=$(stty -g)

function Get_odx
{
    od -t o1 | $AWK '{ for (i=2; i<=NF; i++)
                        printf("%s%s", i==2 ? "" : " ", $i)
                        exit }'
}

# Grab terminal capabilities
tty_cuu1=$(tput cuu1 2>&1 | Get_odx)            # up arrow
tty_kcuu1=$(tput kcuu1 2>&1 | Get_odx)
tty_cud1=$(tput cud1 2>&1 | Get_odx)            # down arrow
tty_kcud1=$(tput kcud1 2>&1 | Get_odx)
tty_cub1=$(tput cub1 2>&1 | Get_odx)            # left arrow
tty_kcub1=$(tput kcud1 2>&1 | Get_odx)
tty_cuf1=$(tput cuf1 2>&1 | Get_odx)            # right arrow
tty_kcuf1=$(tput kcud1 2>&1 | Get_odx)
tty_ent=$($ECHO | Get_odx)                      # Enter key
tty_kent=$(tput kent 2>&1 | Get_odx)
tty_bs=$($ECHO_N "\b" | Get_odx)                # Backspace key
tty_kbs=$(tput kbs 2>&1 | Get_odx)

# Some terminals (e.g. PuTTY) send the wrong code for certain arrow keys
if [ "$tty_cuu1" = "033 133 101" -o "$tty_kcuu1" = "033 133 101" ]; then
    tty_cudx="033 133 102"
    tty_cufx="033 133 103"
    tty_cubx="033 133 104"
fi

stty cs8 -icanon -echo min 10 time 1
stty intr '' susp ''

trap "stty $tty_save; exit"  INT HUP TERM

count=0
while :; do
    [ $count -eq 10 ] && break
    count=$((count+1))

    keypress=$(dd bs=10 count=1 2> /dev/null | Get_odx)

    $ECHO_N "keypress=\"$keypress\""

    case "$keypress" in
        "$tty_ent"|"$tty_kent") $ECHO " -- ENTER";;
        "$tty_bs"|"$tty_kbs") $ECHO " -- BACKSPACE";;
        "$tty_cuu1"|"$tty_kcuu1") $ECHO " -- KEY_UP";;
        "$tty_cud1"|"$tty_kcud1"|"$tty_cudx") $ECHO " -- KEY_DOWN";;
        "$tty_cub1"|"$tty_kcub1"|"$tty_cubx") $ECHO " -- KEY_LEFT";;
        "$tty_cuf1"|"$tty_kcuf1"|"$tty_cufx") $ECHO " -- KEY_RIGHT";;
        *) $ECHO;;
    esac
done

stty $tty_save

```
I know, its a bit messy, but it's not my fault, I didn't write it

---

### Post by ibuclaw on 2010-06-23
> **Crazedpsyc said:**
> lol, there is not home directory in Windows, but the users directory is about the same, and it makes windows users feel comfier. as you can see that is the only thing that is different. I have also now added an option to change that part in the setup script

Why not use [GoboLinux]("http://www.gobolinux.org/index.php?lang=en_US&page=at_a_glance") instead?

---

### Post by Crazedpsyc on 2010-06-23
because ubuntu is better, and I am adding windows commands as well. Besides, it wouldn't make sense to switch Lini (plural linux) just for that! I am considering looking at the linux that is almost exactly like windows (can't remember what its called)

---

### Post by ibuclaw on 2010-06-24
> **Crazedpsyc said:**
> I am considering looking at the linux that is almost exactly like windows (can't remember what its called)

A Wolf wrapped in Sheep clothing is still a wolf. It won't bleat when you give it a treat, it won't change it's diet habit to be  bit more omnivorous in spite, and it certainly still won't be any more domesticated than your resident Fox.

---

### Post by Zeike on 2010-06-24
> **Crazedpsyc said:**
> 1: Get prev command on up arrow
The linux terminal should do this automatically.

> 2: Put a C:\ at the beginning of `pwd`
I strongly urge you to convince whoever requested this 'feature' of you to change their mind.  It is only deceptive and will cause future confusion and lead to issues.

---

### Post by Crazedpsyc on 2010-06-24
OOOOOOOOokay... I get the idea. I don't care.

---

### Post by lkjoel on 2010-06-27
I just found an equivalent of what you are doing: DOSEmu

---

### Post by Crazedpsyc on 2010-06-28
Thanks! that looks great! I also need to know how to decompile ELFs under linux. (I have tried Boomerang and it didn't work for me, just sat there for a long time) I am trying to make the wine cmd.exe work better, but C++ is not really my favorite programming lang (even perl is more fun for me)

---

### Post by lkjoel on 2010-06-28
Decompiling EXE's is very hard.
You usually do not know what language it was compiled in.

---

### Post by Crazedpsyc on 2010-06-29
Ummmm, ok, Archive Manager can decomile windows .exes but I need something to decompile LINUX executables which as far as I know are always ELFs
Archove manager cannot decompile wine .exes because they are not the same

---

### Post by lkjoel on 2010-06-29
> **Crazedpsyc said:**
> Ummmm, ok, Archive Manager **can** decomile windows .exes but I need something to decompile LINUX executables which as far as I know are always ELFs
Archove manager **cannot** decompile wine .exes because they are not the same
You mean Archive Manager can **and** cannot decompile exes?
I don't think I get you.
What is the difference between EXEs which are made for windows, and run with wine?
Does WINE change them?

---

### Post by Crazedpsyc on 2010-06-29
I don;t know either, but I tried decompiling wine's cmd.exe and got .reloc .rsrc and .text. all of which are compiled files compressed into a exe (doesn't make sense) but when I decompiled an actual windows exe (open source one) it came up with things you'd expect like main.c and blah.h

---

### Post by lkjoel on 2010-06-29
Oh I get it.
Did you open the files to read them?

---

### Post by Crazedpsyc on 2010-06-29
I guess you don't know what compiled files are lol! they are in binary, which means gedit cannot open them and cat displays lots of things like diamonds with question marks inside and a lot of other odd symbols. With a binary file viewer, everything would be 1s and 0s

---

### Post by ibuclaw on 2010-06-29
> **Crazedpsyc said:**
> Ummmm, ok, Archive Manager can decomile windows .exes but I need something to decompile LINUX executables which as far as I know are always ELFs
Archove manager cannot decompile wine .exes because they are not the same
Depends what you mean by "decompile"...
> **Crazedpsyc said:**
> I don;t know either, but I tried decompiling wine's cmd.exe and got .reloc .rsrc and .text. all of which are compiled files compressed into a exe (doesn't make sense) but when I decompiled an actual windows exe (open source one) it came up with things you'd expect like main.c and blah.h
Probably because WINE's cmd.exe's object format is laid out in a way the decompiler can't interpret. Just get the source code and save yourself a trying to do something relatively simple the hard way. :)

---

### Post by Crazedpsyc on 2010-06-30
Yeah, speaking of which, is there a way to get source code through Synaptic? Some source repo?

---

### Post by ibuclaw on 2010-06-30
> **Crazedpsyc said:**
> Yeah, speaking of which, is there a way to get source code through Synaptic? Some source repo?

In 'Software Sources' ensure that Source Code is checked, then you can run:
```
apt-get source **name-of-application**
```
in a terminal.

Note that I **do not** use 'sudo'.

---

### Post by Crazedpsyc on 2010-06-30
Thanks!

---

### Post by stderr on 2010-06-30
Seen as quite how many people have already commented on it, I'm going to control myself and refrain from saying what you know I want to about your terminal amendments ;) That said, you've got some interesting stuff in your script.

I don't understand what you're trying to achieve with your EXE/ELF analysis...

"Extracting" EXEs with Archive Manager is != dissassembly. Like you say, your output frmo Archive Manager is just a collection of binary code sections, which means you haven't decompiled/disassembled anything. In this regard, you may find **objdump** to be of some assistance. For example, the -x flag gives header info, including info on the sections that you see in the Archive Manager "extractions". I'd advise looking over the help info

```
objdump -H
```

You'll notice that disassembly can be performed with -d/-D. If you can give us a clue what you're trying to achieve with your ELF analysis, maybe we can be of more assistance.

---

### Post by Crazedpsyc on 2010-07-01
Thanks, i'm looking into the GUI for it (dissy). != it fun to be able to talk to other geeks in shell script lang lol! read answer; if [ "$answer" = "y" -o "$answer" = "Y" -o "$answer" = "yes" -o "$answer" = "Yes" ]; then; echo "Yeah geeks are so fun!"; elif [ "$answer" = "n" -o "$answer" = "N" -o "$answer" = "No" -o "$answer" =  "no" ]; then; echo "Why don't you think so weirdo? else; echo "What's that mean?"; fi

---

### Post by lkjoel on 2010-07-01
> **Crazedpsyc said:**
> Thanks, i'm looking into the GUI for it (dissy). != it fun to be able to talk to other geeks in shell script lang lol! read answer; if [ "$answer" = "y" -o "$answer" = "Y" -o "$answer" = "yes" -o "$answer" = "Yes" ]; then; echo "Yeah geeks are so fun!"; elif [ "$answer" = "n" -o "$answer" = "N" -o "$answer" = "No" -o "$answer" =  "no" ]; then; echo "Why don't you think so weirdo? else; echo "What's that mean?"; fi
Why do you want a GUI?
I know that it is quite easier, but it is much faster from the command line.

---

### Post by stderr on 2010-07-01
> **lkjoel said:**
> Why do you want a GUI?
I know that it is quite easier, but it is much faster from the command line.

Probably answered your own question there :) Whilst I'm completely with you on using CLI when possible, at the same time, trying to sift through tens of thousands of lines of interleaved assembler on the CLI is pretty daunting to most! (Somewhat depending on what you're trying to do)

@Crazedpsych: I was all too tempted to reply by saying that double square brackets are recommended in more recent versions of BASH :lolflag:

Let us know how you find Dissy - it's been so long since I fired it up that I cannot even recall what the UI looks like.

---

### Post by lkjoel on 2010-07-01
Yeah, I agree with you on that, but can't you do
```
yourapp --help | less
```
or
```
yourapp --help | more
```

---

### Post by lkjoel on 2010-07-02
I don't think you need to decompile DOSemu!
I found a way for your bash script to work!
**Script Updated**
```
#!/bin/bash
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ x > 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read command
$command
done
```This was based on a script here
[http://ubuntuforums.org/showthread.php?p=9538272#post9538272](http://ubuntuforums.org/showthread.php?p=9538272#post9538272)

---

### Post by Crazedpsyc on 2010-07-03
great idea, but did I do it right? it doesn't work! here's what I did:
```

#!/bin/bash
# Stuff that happens before the prompt
printf "\n"
myfgcolor=$(cat ~/.cmd/.cmdcolors | grep "fgcolor=" | sed "s/fgcolor=//g")
mybgcolor=$(cat ~/.cmd/.cmdcolors | grep "bgcolor=" | sed "s/bgcolor=//g")
if [ "$myfgcolor" = "" ]
then
myfgcolor="7"
fi
if [ "$mybgcolor" = "" ]
then
mybgcolor="0"
fi

tput setaf $myfgcolor
tput setab $mybgcolor
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ x > 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read comand
done

# this creates the history file
if [ "$comand" != "" ]
...

```
it gives me the C:/... prompt but when I try a command it just exits and reenters (makes a newline and reshows the prompt)

---

### Post by lkjoel on 2010-07-03
> **Crazedpsyc said:**
> great idea, but did I do it right? it doesn't work! here's what I did:
```

#!/bin/bash
# Stuff that happens before the prompt
printf "\n"
myfgcolor=$(cat ~/.cmd/.cmdcolors | grep "fgcolor=" | sed "s/fgcolor=//g")
mybgcolor=$(cat ~/.cmd/.cmdcolors | grep "bgcolor=" | sed "s/bgcolor=//g")
if [ "$myfgcolor" = "" ]
then
myfgcolor="7"
fi
if [ "$mybgcolor" = "" ]
then
mybgcolor="0"
fi

tput setaf $myfgcolor
tput setab $mybgcolor
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ x > 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read comand
done

# this creates the history file
if [ "$comand" != "" ]
...

```it gives me the C:/... prompt but when I try a command it just exits and reenters (makes a newline and reshows the prompt)
Ok, I think I need to give a walkthrough of the commands.
```

# this is a useful function, so then people used to quit can type it.
 quit() {
exit
}
# a variable for the forever loop
x=6
# Windows users type "command.exe" instead of "./command.exe"
PATH=$PATH:./
PATH=$PATH:.
# THIS IS THE BUG!
# this does a forever loop, so put ALL of your code inside it.
while [ x > 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read comand
# put your code here
done
# not here
```

---

### Post by Crazedpsyc on 2010-07-05
Oh, alright now that works except when I try to cd to anything outside of /home/me/, when I try to cd to /home/ or /bin/ or anything like that it says:
```


/home/me/.cmd/cmd.exe: line 23: 5: Permission denied
/home/me/.cmd/cmd.exe: line 23: 5: Permission denied

```
any idea why?

---

### Post by lkjoel on 2010-07-05
Yes I do know why.
First, the script I gave you was influenced by Terminal Enhancements (in my sig)
And Terminal Enhancements, one of its future features is to eliminate the need for boring commands, as the one I will give you.

Type:
```
chmod +x cmd.exe
```
chmod +x makes a file execuatable.
Also, you just need to type:
```
cmd.exe
```
instead of
```
./cmd.exe
```
A cool feature of Terminal Enhancements.

Once your script is finished, could you post it, then I will give you an installation manual.

---

### Post by Crazedpsyc on 2010-07-05
Ya, i know all that but that isn't the problem. cmd.exe is executable. also i just type "cmd" because I have a C++ program to call cmd.exe, which also does some other fun stuff. I'm not that much of a noob lol. (I've been shell scripting for about 4 months and using the terminal frequently for about 4 years

---

### Post by lkjoel on 2010-07-05
Oops! I checked it carefully, and I saw the mistake:
```
rm 5
```There, now try it.;)

EDIT:

Change the file to this:
```

quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ $x -gt 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read comand
done
```

---

### Post by mobilediesel on 2010-07-05
> **lkjoel said:**
> Oops! I checked it carefully, and I saw the mistake:
```
rm 5
```There, now try it.;)

EDIT:

Change the file to this:
```

quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ $x -gt 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read comand
done
```

Why the fake MSDOS prompt?

---

### Post by lkjoel on 2010-07-05
> **mobilediesel said:**
> Why the fake MSDOS prompt?
Someone wants to have a windows-like Terminal.

---

### Post by Crazedpsyc on 2010-07-06
Thanks, i did notice that this morning, but silly me couldn't figure out why it did that bcuz I have been using C++ where that <i>is</i> how you do it. thanks! now it works great! if only I could get that up arrow history working... it is already running inside a c++ app, so maybe someone knows how to do it from there? all it does now it say entering Windows Command Prompt Simulator, runs system(~/.cmd/cmd), and when it exits it says Exiting blahblahblah... and catches the error code.
oh here's the code in cmd.exe:
```

#!/bin/bash
# Stuff that happens before the prompt
printf "\n"
myfgcolor=$(cat ~/.cmd/.cmdcolors | grep "fgcolor=" | sed "s/fgcolor=//g")
mybgcolor=$(cat ~/.cmd/.cmdcolors | grep "bgcolor=" | sed "s/bgcolor=//g")
if [ "$myfgcolor" = "" ]
then
myfgcolor="7"
fi
if [ "$mybgcolor" = "" ]
then
mybgcolor="0"
fi

tput setaf $myfgcolor
tput setab $mybgcolor
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ $x -gt 5 ]

do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd | sed "s/\//\\\\/g" | sed "s/home/Users/g"
echo -n "> "
read comand mod1 mod2 mod3 mod4 mod5 mod6 mod7 mod8 mod9 mod10

# this creates the history file
if [ "$comand" != "" ]
then
    comnum=$(cat ~/.cmd/.comnum | grep "comnum=" | sed "s/comnum=//g")
    if [ "$comnum" = "" ]
    then
    comnum=0
    echo "comnum=0" > ~/.cmd/.comnum
    else
    let comnum=$comnum+1
    echo "comnum=$comnum" > ~/.cmd/.comnum
    fi
comnum=$(cat ~/.cmd/.comnum | grep "comnum=" | sed "s/comnum=//g")
echo "$comnum $comand $mod1 $mod2 $mod3 $mod4 $mod5 $mod6 $mod7 $mod8 $mod9 $mod10" >> ~/.cmd/history.dll
#and this uses it for the history command
if [ "$comand" = "history" -a "$mod1" = "" ]
then
cat ~/.cmd/history.dll
elif [ "$comand" = "comnum" -a "$mod1" = "" ]
then
echo "$comnum"
elif [ "$comand" = "comnum" -a "$mod1" = "-r" ]
then
echo "comnum=0" > ~/.cmd/.comnum
elif [ "$comand" = "history" -a "$mod1" = "-c" ]
then
echo "" > ~/.cmd/history.dll
elif [ "$comand" = "help" -a "$mod1" = "" ]
then
echo "
For more information on a specific command, type HELP command-name
ASSOC          Displays or modifies file extension associations.
ATTRIB         Displays or changes file attributes.
BREAK          Sets or clears extended CTRL+C checking.
BCDEDIT        Sets properties in boot database to control boot loading.
CACLS          Displays or modifies access control lists (ACLs) of files.
CALL           Calls one batch program from another.
CD             Displays the name of or changes the current directory.t
CHCP           Displays or sets the active code page number.
CHDIR          Displays the name of or changes the current directory.
CHKDSK         Checks a disk and displays a status report.
CHKNTFS        Displays or modifies the checking of disk at boot time.
CLS            Clears the screen.
CMD            Starts a new instance of the Windows command interpreter.
COLOR          Sets the default console foreground and background colors.
COMP           Compares the contents of two files or sets of files.
COMPACT        Displays or alters the compression of files on NTFS partitions.
CONVERT        Converts FAT volumes to NTFS.  You cannot convert the
               current drive.
COPY           Copies one or more files to another location.
DATE           Displays or sets the date.
DEL            Deletes one or more files.
DIR            Displays a list of files and subdirectories in a directory.
DISKCOMP       Compares the contents of two floppy disks.
DISKCOPY       Copies the contents of one floppy disk to another.
DISKPART       Displays or configures Disk Partition properties.
DOSKEY         Edits command lines, recalls Windows commands, and
               creates macros.
DRIVERQUERY    Displays current device driver status and properties.
ECHO           Displays messages, or turns command echoing on or off.
ENDLOCAL       Ends localization of environment changes in a batch file.
ERASE          Deletes one or more files.
EXIT           Quits the CMD.EXE program (command interpreter).
FC             Compares two files or sets of files, and displays the
               differences between them.
FIND           Searches for a text string in a file or files.
FINDSTR        Searches for strings in files.
FOR            Runs a specified command for each file in a set of files.
FORMAT         Formats a disk for use with Windows.
FSUTIL         Displays or configures the file system properties.
FTYPE          Displays or modifies file types used in file extension
               associations.
GOTO           Directs the Windows command interpreter to a labeled line in
               a batch program.
GPRESULT       Displays Group Policy information for machine or user.
GRAFTABL       Enables Windows to display an extended character set in
               graphics mode.
HELP           Provides Help information for Windows commands.
ICACLS         Display, modify, backup, or restore ACLs for files and
               directories.
IF             Performs conditional processing in batch programs.
LABEL          Creates, changes, or deletes the volume label of a disk.
MD             Creates a directory.
MKDIR          Creates a directory.
MKLINK         Creates Symbolic Links and Hard Links
MODE           Configures a system device.
MORE           Displays output one screen at a time.
MOVE           Moves one or more files from one directory to another
               directory.
OPENFILES      Displays files opened by remote users for a file share.
PATH           Displays or sets a search path for executable files.
PAUSE          Suspends processing of a batch file and displays a message.
POPD           Restores the previous value of the current directory saved by
               PUSHD.
PRINT          Prints a text file.
PROMPT         Changes the Windows command prompt.
PUSHD          Saves the current directory then changes it.
RD             Removes a directory.
RECOVER        Recovers readable information from a bad or defective disk.
REM            Records comments (remarks) in batch files or CONFIG.SYS.
REN            Renames a file or files.
RENAME         Renames a file or files.
REPLACE        Replaces files.
RMDIR          Removes a directory.
ROBOCOPY       Advanced utility to copy files and directory trees
SET            Displays, sets, or removes Windows environment variables.
SETLOCAL       Begins localization of environment changes in a batch file.
SC             Displays or configures services (background processes).
SCHTASKS       Schedules commands and programs to run on a computer.
SHIFT          Shifts the position of replaceable parameters in batch files.
SHUTDOWN       Allows proper local or remote shutdown of machine.
SORT           Sorts input.
START          Starts a separate window to run a specified program or command.
SUBST          Associates a path with a drive letter.
SYSTEMINFO     Displays machine specific properties and configuration.
TASKLIST       Displays all currently running tasks including services.
TASKKILL       Kill or stop a running process or application.
TIME           Displays or sets the system time.
TITLE          Sets the window title for a CMD.EXE session.
TREE           Graphically displays the directory structure of a drive or
               path.
TYPE           Displays the contents of a text file.
VER            Displays the Windows version.
VERIFY         Tells Windows whether to verify that your files are written
               correctly to a disk.
VOL            Displays a disk volume label and serial number.
XCOPY          Copies files and directory trees.
WMIC           Displays WMI information inside interactive command shell.

For more information on tools see the command-line reference in the online help."
elif [ "$comand" = "help" -a "$mod1" = "comnum" ]
then
echo "The \"comnum\" is the sequential number referring to the command.
Each command you enter adds one to the comnum. the current comnum is $comnum"
printf "Available options are:\n\t-r /r    Resets the comnum to 0\ncomnum displays the current comnum when called without any options."
elif [ "$comand" = "help" -a "$mod1" = "history" ]
then
echo "The history command, when called without any options displays
the contents of the history file with each command on a new line 
beginning with it's comnum (see 'help comnum') to emty the contents of the history file use 'history -c'"
elif [ "$comand" = "exit" ]
then
exit 0
elif [ "$comand" = "chkdsk" ]
then
fsck
elif [ "$comand" = "tracert" ]
then
traceroute $mod1
elif [ "$comand" = "chdir" -a "$mod1" = "" ]
then
echo "$prompt"
elif [ "$comand" = "chdir" -o "$comand" = "cd" -a "$mod1" != "" ]
then
cd $mod1
elif [ "$comand" = "ping" -a "$mod1" != "" -a "$mod1" != "/?" -a "$mod1" != "me" -a "$mod1" != "::1" ]
then
ping -c 4 -s 24 $mod1
elif [ "$comand" = "ping" -a "$mod1" = "" -o "$mod1" = "/?" ]
then
echo "
Usage: ping [-t] [-a] [-n count] [-l size] [-f] [-i TTL] [-v TOS]
            [-r count] [-s count] [[-j host-list] | [-k host-list]]
            [-w timeout] [-R] [-S srcaddr] [-4] [-6] target_name

Options:
    -t             Ping the specified host until stopped.
                   To see statistics and continue - type Control-Break;
                   To stop - type Control-C.
    -a             Resolve addresses to hostnames.
    -n count       Number of echo requests to send.
    -l size        Send buffer size.
    -f             Set Don't Fragment flag in packet (IPv4-only).
    -i TTL         Time To Live.
    -v TOS         Type Of Service (IPv4-only).
    -r count       Record route for count hops (IPv4-only).
    -s count       Timestamp for count hops (IPv4-only).
    -j host-list   Loose source route along host-list (IPv4-only).
    -k host-list   Strict source route along host-list (IPv4-only).
    -w timeout     Timeout in milliseconds to wait for each reply.
    -R             Use routing header to test reverse route also (IPv6-only).
    -S srcaddr     Source address to use.
    -4             Force using IPv4.
    -6             Force using IPv6.

"
elif [ "$comand" = "attrib" -o "$comand" = "ATTRIB" ]
then
chmod $mod1 $mod2 $mod3 $mod4 $mod5 $mod6 $mod7 $mod8 $mod9 $mod10
elif [ "$comand" = "ping" -a "$mod1" = "me" ]
then
ping $HOSTNAME -c 4 -s 24
elif [ "$comand" = "ping" -a "$mod1" = "::1" ]
then
ping6 '::1' -c 4 -s 24
elif [ "$comand" = "color" -a "$mod1" = "" ]
then
printf "\n"
elif [ "$comand" = "color" -a "$mod1" = "/?" ]
then
echo "Sets the default console foreground and background colors.

COLOR [attr]

  attr        Specifies color attribute of console output

Color attributes are specified by TWO hex digits -- the first
corresponds to the background; the second the foreground.  Each digit
can be any of the following values:

    0 = Black       8 = Gray
    1 = Blue        9 = Light Blue
    2 = Green       A = Light Green
    3 = Aqua        B = Light Aqua
    4 = Red         C = Light Red
    5 = Purple      D = Light Purple
    6 = Yellow      E = Light Yellow
    7 = White       F = Bright White

If no argument is given, this command restores the color to what it was
when CMD.EXE started.  This value either comes from the current console
window, the /T command line switch or from the DefaultColor registry
value."
read -s -e -p "Press any key to continue..." -n 1
echo "The COLOR command sets ERRORLEVEL to 1 if an attempt is made to execute
the COLOR command with a foreground and background color that are the
same.

Example: \"COLOR fc\" produces light red on bright white"
elif [ "$comand" = "color" -a "$mod1" != "" -a "$mod1" != "/?" ]
then
## Copy an "elif" section and replace the color codes like "70" and "07" as well as the values for '$myfgcolor' and '$mybgcolor' to add new colors ##
# White on Black
    if [ "$mod1" = "0f" ]
    then
    mybgcolor="0"
    myfgcolor="7"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmd/.cmdcolors
clear
# Black on White
    elif [ "$mod1" = "f0" ]
    then
    mybgcolor="7"
    myfgcolor="0"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmd/.cmdcolors
clear
# Light Green on Black
    elif [ "$mod1" = "0A" -o "$mod1" = "0a" ]
    then
    echo "Sorry only black and white are available"
    mybgcolor="0"
    myfgcolor="3"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmd/.cmdcolors
clear
    fi
elif [ "$comand" = "start" -a "$mod1" != "cmd" ]
then
~/.cmd/start $mod1
elif [ "$comand" = "start" -a "$mod1" = "cmd" ]
then
~/.cmd/cmd.exe | sed "s/\/home\/mike\/.cmd\/cmd.exe: line 227/Command/g"
then
echo "Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved."
~/.cmd/cmd.exe | sed "s/\/home\/mike\/.cmd\/cmd.exe: line 227/Command/g"
else
$comand $mod1 $mod2 $mod3 $mod4 $mod5 $mod6 $mod7 $mod8 $mod9 $mod10
fi
fi
~/.cmd/cmd.exe
done

```
also, anybody know how to get rid of or change that annoying bash command not found thing? (without any de- and re-compiling hopefully) I tried using sed to cut it out, but for some reason it didnt work. maybe because of spaces?

---

### Post by lkjoel on 2010-07-06
Ok, there is one problem, before we move on.
"cmd.exe" is a shell script right?
If WINE tries to run it, it won't work right?
> **Crazedpsyc said:**
> Thanks, i did notice that this morning, but silly me couldn't figure out why it did that bcuz I have been using C++ where that <i>is</i> how you do it. thanks! now it works great! if only I could get that up arrow history working... it is already running inside a c++ app, so maybe someone knows how to do it from there? all it does now it say entering Windows Command Prompt Simulator, runs system(~/.cmd/cmd), and when it exits it says Exiting blahblahblah... and catches the error code.
oh here's the code in cmd.exe:
```

#!/bin/bash
# Stuff that happens before the prompt
printf "\n"
myfgcolor=$(cat ~/.cmd/.cmdcolors | grep "fgcolor=" | sed "s/fgcolor=//g")
mybgcolor=$(cat ~/.cmd/.cmdcolors | grep "bgcolor=" | sed "s/bgcolor=//g")
if [ "$myfgcolor" = "" ]
then
myfgcolor="7"
fi
if [ "$mybgcolor" = "" ]
then
mybgcolor="0"
fi

tput setaf $myfgcolor
tput setab $mybgcolor
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ $x -gt 5 ]

do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd | sed "s/\//\\\\/g" | sed "s/home/Users/g"
echo -n "> "
read comand mod1 mod2 mod3 mod4 mod5 mod6 mod7 mod8 mod9 mod10

# this creates the history file
if [ "$comand" != "" ]
then
    comnum=$(cat ~/.cmd/.comnum | grep "comnum=" | sed "s/comnum=//g")
    if [ "$comnum" = "" ]
    then
    comnum=0
    echo "comnum=0" > ~/.cmd/.comnum
    else
    let comnum=$comnum+1
    echo "comnum=$comnum" > ~/.cmd/.comnum
    fi
comnum=$(cat ~/.cmd/.comnum | grep "comnum=" | sed "s/comnum=//g")
echo "$comnum $comand $mod1 $mod2 $mod3 $mod4 $mod5 $mod6 $mod7 $mod8 $mod9 $mod10" >> ~/.cmd/history.dll
#and this uses it for the history command
if [ "$comand" = "history" -a "$mod1" = "" ]
then
cat ~/.cmd/history.dll
elif [ "$comand" = "comnum" -a "$mod1" = "" ]
then
echo "$comnum"
elif [ "$comand" = "comnum" -a "$mod1" = "-r" ]
then
echo "comnum=0" > ~/.cmd/.comnum
elif [ "$comand" = "history" -a "$mod1" = "-c" ]
then
echo "" > ~/.cmd/history.dll
elif [ "$comand" = "help" -a "$mod1" = "" ]
then
echo "
For more information on a specific command, type HELP command-name
ASSOC          Displays or modifies file extension associations.
ATTRIB         Displays or changes file attributes.
BREAK          Sets or clears extended CTRL+C checking.
BCDEDIT        Sets properties in boot database to control boot loading.
CACLS          Displays or modifies access control lists (ACLs) of files.
CALL           Calls one batch program from another.
CD             Displays the name of or changes the current directory.t
CHCP           Displays or sets the active code page number.
CHDIR          Displays the name of or changes the current directory.
CHKDSK         Checks a disk and displays a status report.
CHKNTFS        Displays or modifies the checking of disk at boot time.
CLS            Clears the screen.
CMD            Starts a new instance of the Windows command interpreter.
COLOR          Sets the default console foreground and background colors.
COMP           Compares the contents of two files or sets of files.
COMPACT        Displays or alters the compression of files on NTFS partitions.
CONVERT        Converts FAT volumes to NTFS.  You cannot convert the
               current drive.
COPY           Copies one or more files to another location.
DATE           Displays or sets the date.
DEL            Deletes one or more files.
DIR            Displays a list of files and subdirectories in a directory.
DISKCOMP       Compares the contents of two floppy disks.
DISKCOPY       Copies the contents of one floppy disk to another.
DISKPART       Displays or configures Disk Partition properties.
DOSKEY         Edits command lines, recalls Windows commands, and
               creates macros.
DRIVERQUERY    Displays current device driver status and properties.
ECHO           Displays messages, or turns command echoing on or off.
ENDLOCAL       Ends localization of environment changes in a batch file.
ERASE          Deletes one or more files.
EXIT           Quits the CMD.EXE program (command interpreter).
FC             Compares two files or sets of files, and displays the
               differences between them.
FIND           Searches for a text string in a file or files.
FINDSTR        Searches for strings in files.
FOR            Runs a specified command for each file in a set of files.
FORMAT         Formats a disk for use with Windows.
FSUTIL         Displays or configures the file system properties.
FTYPE          Displays or modifies file types used in file extension
               associations.
GOTO           Directs the Windows command interpreter to a labeled line in
               a batch program.
GPRESULT       Displays Group Policy information for machine or user.
GRAFTABL       Enables Windows to display an extended character set in
               graphics mode.
HELP           Provides Help information for Windows commands.
ICACLS         Display, modify, backup, or restore ACLs for files and
               directories.
IF             Performs conditional processing in batch programs.
LABEL          Creates, changes, or deletes the volume label of a disk.
MD             Creates a directory.
MKDIR          Creates a directory.
MKLINK         Creates Symbolic Links and Hard Links
MODE           Configures a system device.
MORE           Displays output one screen at a time.
MOVE           Moves one or more files from one directory to another
               directory.
OPENFILES      Displays files opened by remote users for a file share.
PATH           Displays or sets a search path for executable files.
PAUSE          Suspends processing of a batch file and displays a message.
POPD           Restores the previous value of the current directory saved by
               PUSHD.
PRINT          Prints a text file.
PROMPT         Changes the Windows command prompt.
PUSHD          Saves the current directory then changes it.
RD             Removes a directory.
RECOVER        Recovers readable information from a bad or defective disk.
REM            Records comments (remarks) in batch files or CONFIG.SYS.
REN            Renames a file or files.
RENAME         Renames a file or files.
REPLACE        Replaces files.
RMDIR          Removes a directory.
ROBOCOPY       Advanced utility to copy files and directory trees
SET            Displays, sets, or removes Windows environment variables.
SETLOCAL       Begins localization of environment changes in a batch file.
SC             Displays or configures services (background processes).
SCHTASKS       Schedules commands and programs to run on a computer.
SHIFT          Shifts the position of replaceable parameters in batch files.
SHUTDOWN       Allows proper local or remote shutdown of machine.
SORT           Sorts input.
START          Starts a separate window to run a specified program or command.
SUBST          Associates a path with a drive letter.
SYSTEMINFO     Displays machine specific properties and configuration.
TASKLIST       Displays all currently running tasks including services.
TASKKILL       Kill or stop a running process or application.
TIME           Displays or sets the system time.
TITLE          Sets the window title for a CMD.EXE session.
TREE           Graphically displays the directory structure of a drive or
               path.
TYPE           Displays the contents of a text file.
VER            Displays the Windows version.
VERIFY         Tells Windows whether to verify that your files are written
               correctly to a disk.
VOL            Displays a disk volume label and serial number.
XCOPY          Copies files and directory trees.
WMIC           Displays WMI information inside interactive command shell.

For more information on tools see the command-line reference in the online help."
elif [ "$comand" = "help" -a "$mod1" = "comnum" ]
then
echo "The \"comnum\" is the sequential number referring to the command.
Each command you enter adds one to the comnum. the current comnum is $comnum"
printf "Available options are:\n\t-r /r    Resets the comnum to 0\ncomnum displays the current comnum when called without any options."
elif [ "$comand" = "help" -a "$mod1" = "history" ]
then
echo "The history command, when called without any options displays
the contents of the history file with each command on a new line 
beginning with it's comnum (see 'help comnum') to emty the contents of the history file use 'history -c'"
elif [ "$comand" = "exit" ]
then
exit 0
elif [ "$comand" = "chkdsk" ]
then
fsck
elif [ "$comand" = "tracert" ]
then
traceroute $mod1
elif [ "$comand" = "chdir" -a "$mod1" = "" ]
then
echo "$prompt"
elif [ "$comand" = "chdir" -o "$comand" = "cd" -a "$mod1" != "" ]
then
cd $mod1
elif [ "$comand" = "ping" -a "$mod1" != "" -a "$mod1" != "/?" -a "$mod1" != "me" -a "$mod1" != "::1" ]
then
ping -c 4 -s 24 $mod1
elif [ "$comand" = "ping" -a "$mod1" = "" -o "$mod1" = "/?" ]
then
echo "
Usage: ping [-t] [-a] [-n count] [-l size] [-f] [-i TTL] [-v TOS]
            [-r count] [-s count] [[-j host-list] | [-k host-list]]
            [-w timeout] [-R] [-S srcaddr] [-4] [-6] target_name

Options:
    -t             Ping the specified host until stopped.
                   To see statistics and continue - type Control-Break;
                   To stop - type Control-C.
    -a             Resolve addresses to hostnames.
    -n count       Number of echo requests to send.
    -l size        Send buffer size.
    -f             Set Don't Fragment flag in packet (IPv4-only).
    -i TTL         Time To Live.
    -v TOS         Type Of Service (IPv4-only).
    -r count       Record route for count hops (IPv4-only).
    -s count       Timestamp for count hops (IPv4-only).
    -j host-list   Loose source route along host-list (IPv4-only).
    -k host-list   Strict source route along host-list (IPv4-only).
    -w timeout     Timeout in milliseconds to wait for each reply.
    -R             Use routing header to test reverse route also (IPv6-only).
    -S srcaddr     Source address to use.
    -4             Force using IPv4.
    -6             Force using IPv6.

"
elif [ "$comand" = "attrib" -o "$comand" = "ATTRIB" ]
then
chmod $mod1 $mod2 $mod3 $mod4 $mod5 $mod6 $mod7 $mod8 $mod9 $mod10
elif [ "$comand" = "ping" -a "$mod1" = "me" ]
then
ping $HOSTNAME -c 4 -s 24
elif [ "$comand" = "ping" -a "$mod1" = "::1" ]
then
ping6 '::1' -c 4 -s 24
elif [ "$comand" = "color" -a "$mod1" = "" ]
then
printf "\n"
elif [ "$comand" = "color" -a "$mod1" = "/?" ]
then
echo "Sets the default console foreground and background colors.

COLOR [attr]

  attr        Specifies color attribute of console output

Color attributes are specified by TWO hex digits -- the first
corresponds to the background; the second the foreground.  Each digit
can be any of the following values:

    0 = Black       8 = Gray
    1 = Blue        9 = Light Blue
    2 = Green       A = Light Green
    3 = Aqua        B = Light Aqua
    4 = Red         C = Light Red
    5 = Purple      D = Light Purple
    6 = Yellow      E = Light Yellow
    7 = White       F = Bright White

If no argument is given, this command restores the color to what it was
when CMD.EXE started.  This value either comes from the current console
window, the /T command line switch or from the DefaultColor registry
value."
read -s -e -p "Press any key to continue..." -n 1
echo "The COLOR command sets ERRORLEVEL to 1 if an attempt is made to execute
the COLOR command with a foreground and background color that are the
same.

Example: \"COLOR fc\" produces light red on bright white"
elif [ "$comand" = "color" -a "$mod1" != "" -a "$mod1" != "/?" ]
then
## Copy an "elif" section and replace the color codes like "70" and "07" as well as the values for '$myfgcolor' and '$mybgcolor' to add new colors ##
# White on Black
    if [ "$mod1" = "0f" ]
    then
    mybgcolor="0"
    myfgcolor="7"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmd/.cmdcolors
clear
# Black on White
    elif [ "$mod1" = "f0" ]
    then
    mybgcolor="7"
    myfgcolor="0"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmd/.cmdcolors
clear
# Light Green on Black
    elif [ "$mod1" = "0A" -o "$mod1" = "0a" ]
    then
    echo "Sorry only black and white are available"
    mybgcolor="0"
    myfgcolor="3"
    tput setaf $myfgcolor
    tput setab $mybgcolor
    echo "fgcolor=$myfgcolor
bgcolor=$mybgcolor" > ~/.cmd/.cmdcolors
clear
    fi
elif [ "$comand" = "start" -a "$mod1" != "cmd" ]
then
~/.cmd/start $mod1
elif [ "$comand" = "start" -a "$mod1" = "cmd" ]
then
~/.cmd/cmd.exe | sed "s/\/home\/mike\/.cmd\/cmd.exe: line 227/Command/g"
then
echo "Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved."
~/.cmd/cmd.exe | sed "s/\/home\/mike\/.cmd\/cmd.exe: line 227/Command/g"
else
$comand $mod1 $mod2 $mod3 $mod4 $mod5 $mod6 $mod7 $mod8 $mod9 $mod10
fi
fi
~/.cmd/cmd.exe
done

```also, anybody know how to get rid of or change that annoying bash command not found thing? (without any de- and re-compiling hopefully) I tried using sed to cut it out, but for some reason it didnt work. maybe because of spaces?

---

### Post by lkjoel on 2010-07-06
Would you like to make this into a project, so then the whole world can enjoy it?
Then a lot of developers can help your project, and the developers don't need to be on Ubuntu Forums.

---

### Post by Crazedpsyc on 2010-07-07
You are correct there, but it should never be run directly, there is the compiled C++ app (cmd) in /bin which can be set as the shell with chsh after it is added to /etc/shells, and then there it the shell script cmd in ~/.cmd/ which runs cmd.exe. I am interested in this "project" idea, could you tell me more?

---

### Post by lkjoel on 2010-07-07
> **Crazedpsyc said:**
> You are correct there, but it should never be run directly, there is the compiled C++ app (cmd) in /bin which can be set as the shell with chsh after it is added to /etc/shells, and then there it the shell script cmd in ~/.cmd/ which runs cmd.exe. I am interested in this "project" idea, could you tell me more?
Yes, it is free in Sourceforge.net, Launchpad.net, and Google code.
But 90% of the time I used to make my projects was used to upload it to web!

---

### Post by lkjoel on 2010-07-08
Would you like me to set it up on Launchpad.net?

---

### Post by Crazedpsyc on 2010-07-08
Yeah, that would be great! you want the two cmd files? (c++ and script)

---

### Post by lkjoel on 2010-07-08
> **Crazedpsyc said:**
> Yeah, that would be great! you want the two cmd files? (c++ and script)Sure

---

### Post by lkjoel on 2010-07-08
You need a launchpad account. It is 100% free.
What is the base version? (0.1, 0.0.1, 1.0 etc...)
I'm assuming this is not packaged in Ubuntu.

---

### Post by lkjoel on 2010-07-08
Oh yeah, and you also need another e-mail address specifically for DOSprompt.

---

### Post by Crazedpsyc on 2010-07-09
Another Email? ok, I'll get like [EMAIL="dosprompt@live.com"]dosprompt@live.com[/EMAIL] or something. good name by the way! No, it's not a .deb but I have a .tar.gz with a setup script. the complete package is attached at a .tar. if you don't want to install it just put the files in "files" in ~/.cmd/ (yes i'll change it to .dosprompt eventually) and put the executable dosprompt in /bin. do you think I should have the source of that included for those who don't use elfs?

---

### Post by lkjoel on 2010-07-09
> **Crazedpsyc said:**
> Another Email? ok, I'll get like [EMAIL="dosprompt@live.com"]dosprompt@live.com[/EMAIL] or something. good name by the way! No, it's not a .deb but I have a .tar.gz with a setup script. the complete package is attached at a .tar. if you don't want to install it just put the files in "files" in ~/.cmd/ (yes i'll change it to .dosprompt eventually) and put the executable dosprompt in /bin. do you think I should have the source of that included for those who don't use elfs?
Check setup2.
So is [EMAIL="dosprompt@live.com"]dosprompt@live.com[/EMAIL] set up yet?
Maybe the source of your C/C++ files.
Do you have your Launchpad account set up yet?
And this link might be useful... [https://launchpad.net/dosprompt](https://launchpad.net/dosprompt)

---

### Post by lkjoel on 2010-07-09
BASH syntax is not working...
```
while: command not found.
```
It was the same problem with Terminal Enhancements, until I removed the prompt.
But I don't know how you can fix it.

---

### Post by lkjoel on 2010-07-10
Check this guide out: [http://www.arwin.net/tech/bash.php](http://www.arwin.net/tech/bash.php)
The prompt variable is PS1.
So you can change it to anything, including your C:\> prompt.
BASH syntax will work on it.

---

### Post by Crazedpsyc on 2010-07-13
Thanks! this is all very helpful, but i'm a little busy right now so i'll get working on all that later. No i havn't set up anything yet because I was waiting for you to check that package. Please run history -c from cmd/dosprompt because I forgot to clear my history before giving it to you. also run comnum -r

Thanks for setting that up. did you add helpful comments where I have started working on things? No idea why it can't find while for you, do you have bash installed? is it in /bin/?

---

### Post by spillin_dylan on 2010-07-14
> Wink Re: Bash shell scripting help
I don't think you need to decompile DOSemu!
I found a way for your bash script to work!
Script Updated
Code:

#!/bin/bash
quit() {
exit
}
x=6
PATH=$PATH:./
PATH=$PATH:.
while [ x > 5 ]
do
pwdd=$(pwd)
echo -n "C:"
echo -n $pwdd
echo -n "> "
read command
$command
done

This was based on a script here
[http://ubuntuforums.org/showthread.p...72#post9538272](http://ubuntuforums.org/showthread.p...72#post9538272)


The funniest part about this script for me was how it eliminates tab-completion, just like DOS!!!!

Not saying that's a huge limitation, in fact it is true to the original design, but it sure made me realize how much more I like BASH over DOS.



Also, on a more unrelated note, I haven't been following this thread religiously or anything, but if the goal is to fool people into thinking that they are working in DOS, then you actually have to support the DOS commands, too, don't you?  Not just the "look and feel", but the functionality?  Maybe you're just looking for an OS called FreeDOS instead of a BASH equivalent?  Not saying that it can't (or even shouldn't) be done, but is this really worth the work?  Or is that too many questions in a row..?

---

### Post by lkjoel on 2010-07-14
> **Crazedpsyc said:**
> Thanks! this is all very helpful, but i'm a little busy right now so i'll get working on all that later. No i havn't set up anything yet because I was waiting for you to check that package. Please run history -c from cmd/dosprompt because I forgot to clear my history before giving it to you. also run comnum -r

Thanks for setting that up. did you add helpful comments where I have started working on things? No idea why it can't find while for you, do you have bash installed? is it in /bin/?
In DOSprompt, while is not in there, simply because while is from the BASH syntax, and is not a command to execute.
Also, I am having to type exit n times, until it exits. n=number of commands executed.
Helpful comments where you have started working on things?
Such as the install script?

---

### Post by lkjoel on 2010-07-16
> **spillin_dylan said:**
> The funniest part about this script for me was how it eliminates tab-completion, just like DOS!!!!

Not saying that's a huge limitation, in fact it is true to the original design, but it sure made me realize how much more I like BASH over DOS.



Also, on a more unrelated note, I haven't been following this thread religiously or anything, but if the goal is to fool people into thinking that they are working in DOS, then you actually have to support the DOS commands, too, don't you?  Not just the "look and feel", but the functionality?  Maybe you're just looking for an OS called FreeDOS instead of a BASH equivalent?  Not saying that it can't (or even shouldn't) be done, but is this really worth the work?  Or is that too many questions in a row..?
I think the point with this thread is that people can use the Linux terminal, but with DOS equivalent commands. So they are interacting with Linux, but with a DOS interface. Their commands will be finished either way.
There is no such thing as a stupid project.

---

### Post by Crazedpsyc on 2010-07-22
Thanks all of you and sorry for the long delay lkjoel, [email]dosprompt@live.com[/email] is up and running (I hate that live.com interface though, can't somebody like ubuntu make an e-mail site?).
Do you think i should put dosprompt under the GPL? 
awaiting further instructions...
also changing the names of everything to dosprompt instead of just cmd...
I don't really get what you mean about the while issue, it should work just fine because of the "#!/bin/bash" at the top..
to fix that exit issue just take out the "~/.cmd/cmd.exe" part at the end, sorry about that
well maybe that too, but I think I gave you a version in which I just started the prompt command, so it would be nice to have that part say something about it and how it works (although it doesn't work yet lol)

---

### Post by lkjoel on 2010-07-23
> **Crazedpsyc said:**
> Thanks all of you and sorry for the long delay lkjoel, [EMAIL="dosprompt@live.com"]dosprompt@live.com[/EMAIL] is up and running (I hate that live.com interface though, can't somebody like ubuntu make an e-mail site?).
Do you think i should put dosprompt under the GPL? 
awaiting further instructions...
also changing the names of everything to dosprompt instead of just cmd...
I don't really get what you mean about the while issue, it should work just fine because of the "#!/bin/bash" at the top..
to fix that exit issue just take out the "~/.cmd/cmd.exe" part at the end, sorry about that
well maybe that too, but I think I gave you a version in which I just started the prompt command, so it would be nice to have that part say something about it and how it works (although it doesn't work yet lol)
For the live interface, try Yahoo! or Gmail.
I put my projects under GPL, and it is good for me.

---

### Post by Crazedpsyc on 2010-07-27
Ok so what now? can you put a copying.txt in and copyright 2010 by crazedpsyc? (I hope I don't have to use my name) (if so can I use my unofficial alias?)

---

### Post by lkjoel on 2010-07-28
I am pretty sure that you have to put your real name down.

---

### Post by Crazedpsyc on 2010-08-02
So I can just put initial and last name right? I've seen others do this.

---

### Post by lkjoel on 2010-08-02
Yes.
I would suggest that you should show the source code too.
And do you have your launchpad account yet?

---

### Post by Crazedpsyc on 2010-09-08
Sorry again for the long delay, I believe I do have my launchpad account set up, although I have not logged in yet. It is Crazedpsyc, just like on here.

---

### Post by lkjoel on 2010-09-10
> **Crazedpsyc said:**
> Sorry again for the long delay, I believe I do have my launchpad account set up, although I have not logged in yet. It is Crazedpsyc, just like on here.
Could you confirm the e-mail request sent to [email]dosprompt@live.com[/email]?
And could you confirm your membership?

---

### Post by Crazedpsyc on 2010-09-19
I thought I did, but I'll try again, sorry

---

### Post by lkjoel on 2010-09-19
Once you have confirmed, log in and go to [https://launchpad.net/~dosprompt-dev]("https://launchpad.net/~dosprompt-dev")
Then click on Join this team.
I will make you the Administrator.

---

### Post by Crazedpsyc on 2010-09-21
Sorry, the live.com site is having a very weird problem (IT'S MICROSOFT [just kidding]) and I can't log in today :( i'll try again tomorrow

---

### Post by lkjoel on 2010-09-22
Can you log into Launchpad?
If so, follow the instructions indicated in my last post.

---

### Post by Crazedpsyc on 2010-09-23
Ok, the trouble is, I forgot the password for both. I also used something about "I don't use security questions" for the answer to the security question. And the worst part is, the captcha won't load for either. No idea what the problem is there, but it makes it so I can't make new accounts or do the forgot my password thing.

---

### Post by CharlesA on 2010-09-23
What browser are you using?

---

### Post by lkjoel on 2010-09-23
> **Crazedpsyc said:**
> Ok, the trouble is, I forgot the password for both. I also used something about "I don't use security questions" for the answer to the security question. And the worst part is, the captcha won't load for either. No idea what the problem is there, but it makes it so I can't make new accounts or do the forgot my password thing.
Type this in a Terminal:
```
sudo apt-get install ubuntu-restricted-extras

```
Now try getting a new account.

---

### Post by CharlesA on 2010-09-23
> **lkjoel said:**
> Type this in a Terminal:
```
sudo apt-get install ubuntu-restricted-extras

```
Now try getting a new account.

For that matter, they could even try to recover their password.

That should load the CAPCHA.

---

### Post by Crazedpsyc on 2010-09-24
I still get Loading...
where the captcha is supposed to be

---

### Post by CharlesA on 2010-09-24
I tried accessing that page on my Lucid VM, with no extra stuff installed. It loaded fine.

You could try accessing it from a livecd and see if it does the same thing.

---

### Post by Crazedpsyc on 2010-09-25
I know it used to work, and yes it does probably work live, but before trying that let me try rebooting and waiting a little bit.

---

### Post by Crazedpsyc on 2010-09-27
Ok, still nothing, Now i'll try to find my live dvd and run it...

---

### Post by Crazedpsyc on 2010-09-27
Alright now I am officially there and following your instructions!

edit: Or not, I thought I was logged in but I wasn't so I went to reset my password at launchpad, and everything worked except I didn't get the email. Is there a delay? I'll check back soon.

EDIT2: Still nothing. I checked junk too and there's nothing. Any clues?

---

### Post by Crazedpsyc on 2010-10-04
Ok you should probably know I am not just wasting my time during all this. I am now trying to convert the script to python. There is still no email from launchpad, so I will try the recovery thing again.

Still nothing.

---

