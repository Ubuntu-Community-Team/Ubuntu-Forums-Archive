---
title: "How to use the terminal"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by aaryan on 2009-09-19
Hi friends, I've installed Ubuntu and have got all drivers etc. working. I am now trying to learn as to how to use the terminal for day 2 day work like say how do I open mozilla which is on my desktop, or if I have a file on my desktop how do I open that from the terminal? Help on this would be deeply appreciated. Also if any 1 would know as to where I could get a good tutorial on shell scripting please do let me know. itried a few sites on google but they are a bit confusing.
Thanks a lot in advance.
Aaryan

---

### Post by esalnoj on 2009-09-19
Keep this command permanently in your .bash_history:

```
cd /home/"username"/Desktop/"rest of path" && ./"file"
```

Replacing what's inside qoutation marks with what indicated. This will run the indicated file.

What type of file do you want to open? You need different apps to run depending on picture, text file, etc. 

If permissions error, place sudo in front of cd.

---

### Post by scragar on 2009-09-19
To run programs you just type the name of the program if it's been installed, so
```
firefox
```will open firefox.
To open a file you'll want to open it using the appropriate program, if you know the name of it. If not you can use gnome-open.

For example here I change to my desktop, then use gnome-open to play a video in VLC:
```
cd De**tab***sktop*
gnome-o**tab***pen* "e**tab***den of the east_e0*1**tab***.mkv*
```Where I've typed **tab** it's where I've used the terminals autocomplete by pressing the tab button to save typing. The italics after it shows what was entered for me.

---

### Post by stderr on 2009-09-19
Just constantly be aware of your present working directory:

```
pwd
```

Change directories with:

```
cd
```

Don't type out complete paths! Use TAB to autocomplete as you go.

List directories with:

```
ls
```

Learn about a command (ls in the below example) with:

```
man ls
```

Use the above to find out what "ls -a" does, and then try that.

To run a script/binary in the directory you're currently in, you need to precede it with: 

```
./
```

The best way to learn, IMO, is to experiment and use "man" a lot! Rule: see what man says before trying something; the shell is very powerful. Respect the power; love the power, but just be aware you can easily wipe all your data with one ill-considered command ;)

---

### Post by scragar on 2009-09-19
> **stderr said:**
> The best way to learn, IMO, is to experiment and use "man" a lot! Rule: see what man says before trying something; the shell is very powerful. Respect the power; love the power, but just be aware you can easily wipe all your data with one ill-considered command ;)

Also known as ALWAYS make backups, never run **rm -rf** without first testing it using **-i** and always check the contents of a file before using >

---

### Post by aaryan on 2009-09-19
what if the file is in a directory does it come as 
cd /home/"username"/Desktop/directory name && ./"file"

---

### Post by aaryan on 2009-09-19
thanks a lot

---

### Post by scragar on 2009-09-19
> **aaryan said:**
> what if the file is in a directory does it come as 
cd /home/"username"/Desktop/directory name && ./"file"

You don't need the /home/username part, there's a shorthand:
```
cd ~/Desktop/dir
```You also start off in your home folder by default, so:
```
cd Desktop/dir
```Works fine.
```
cd
```on it's own will also send you back to your home folder.
```
cd ..
```will send you to the parent folder, so in /home/scragar it would send me to /home

Also spaces in file names should be quoted, so:
```
cd Desktop/dir with a space in it
```won't work, but```
cd "Desktop/dir with a space in it"
```works fine. You could also escape the spaces, which you'll see if you start using the tab complete a lot:```
cd Desktop/dir\ with\ a\ space\ in\ it
```

---

### Post by aaryan on 2009-09-19
> **scragar said:**
> Also known as ALWAYS make backups, never run **rm -rf** without first testing it using **-i** and always check the contents of a file before using >
how do i close the file that is open from the terminal should I use kill?

---

### Post by stderr on 2009-09-19
... and just to waste your time, one of my (well, many people's) all-time favourite commands:

```
fortune
```

You'll probably need to install it first:

```
sudo apt-get install fortunes
```

But you wouldn't install something without knowing what it was, would you?

```
apt-cache show fortunes
```

---

### Post by scragar on 2009-09-19
> **aaryan said:**
> how do i close the file that is open from the terminal should I use kill?

kill is great, but it requires the knowledge of the process ID.
There are a lot of other choices:
```
xkill
```is a graphical kill, giving you the option to click a window to close.
```
pkill
```kills all processes that match a pattern(use -f for the full command, so ```
pkill -f movie.flv
```will close any processes that were opened with movie.flv as an argument)
```
killall
```is the most common solution, it kills all processes who's name exactly match the argument.

---

### Post by aaryan on 2009-09-19
> **stderr said:**
> ... And just to waste your time, one of my (well, many people's) all-time favourite commands:

```
fortune
```

you'll probably need to install it first:

```
sudo apt-get install fortunes
```

but you wouldn't install something without knowing what it was, would you?

```
apt-cache show fortunes
```
how do i close an open file from the terminal?

---

### Post by stumbleUpon on 2009-09-19
> **aaryan said:**
> Also if any 1 would know as to where I could get a good tutorial on shell scripting please do let me know. itried a few sites on google but they are a bit confusing.
Thanks a lot in advance.
Aaryan

There are many many tutorials and books. Google around to find them. Here are a few

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)

[http://www.faqs.org/docs/air/tsshell.html](http://www.faqs.org/docs/air/tsshell.html)

[http://freebookcentre.net/UnixCategory/Free-Unix-Shell-Programming-Books-Download.html](http://freebookcentre.net/UnixCategory/Free-Unix-Shell-Programming-Books-Download.html)

Shell Scripting Recipes - A Problem-Solution Approach, CHRIS F. A. JOHNSON

Mastering Unix Shell Scripting,  Randal K. Michael



A forum where you can ask questions and search for the already existing answers to common problems

[http://www.bashscripts.org/forum/](http://www.bashscripts.org/forum/)

A repository of scripts

[http://www.zazzybob.com/bin.html](http://www.zazzybob.com/bin.html)

---

### Post by aaryan on 2009-09-19
so that helps me close the files that I'd have opened, but what if i need to close a directory, is there a separate function for that?

---

### Post by scragar on 2009-09-19
> **aaryan said:**
> how do i close an open file from the terminal?

Maybe you can explain that better, I gave a few options for how to kill off processes, but maybe if you explain the problem more we'll be able to actually answer it.

---

### Post by scragar on 2009-09-19
> **aaryan said:**
> so that helps me close the files that I'd have opened, but what if i need to close a directory, is there a separate function for that?

Are you talking about the file manager or something? The file manager is called nautilus.
If you changed to a directory you can return to your home folder by typing```
cd
``` on it's own.

---

### Post by stumbleUpon on 2009-09-19
I suggest you download and read the freely available book here

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

This will give you a good flavor of ubuntu (and linux in general) and will get you the basics of working with files, folders ..etc

---

### Post by earthpigg on 2009-09-19
> **aaryan said:**
> how do i close an open file from the terminal?

```
ps -A | grep word-here-that-is-probably-part-of-the-program-name
```

example, if pidgin was frozen and i wanted to kill it but couldn't remember exactly how the heck it was spelled:

```
[chris: ~]$ ps -A | grep pid
   45 ?        00:00:00 kacpid
 3754 ?        00:01:57 pidgin # <--- there it is! i KNEW it started with 'pid' and had something to do with birds...
[chris: ~]$ kill -9 3754 # <-- die, pidgin!
[chris: ~]$ ps -A | grep pid # <-- confirm that i killed it
   45 ?        00:00:00 kacpid
[chris: ~]$ 
```

this would also accomplish that task:

```
killall pidgin
```

"O noes! my whole system is frozen!"

want to bet it's only the graphical user interface that is dead?

press ctrl+alt+F5. or ctrl+alt+any-F-key-from-1-to-7.

login.

```
sudo killall _X_org
```

then, ctrl+alt+F7 to get back to the tty you came from. you will almost certainly be looking at your graphical login screen.

this stuff is important because the first and, *in my opinion*, the most important use of the command line in most typical home computer uses is getting your graphical interface back up and running without completely restarting your computer.

install htop and learn to work it without a mouse (use a different tty to test this).... just read what is on the screen and do what it says:

```
sudo apt-get install htop
```
to run it:
```
htop
```

couple other commands everyone should be familiar with that haven't been mentioned yet:

free (usually used as 'free -m')
df (usually used as 'df -Th' or 'free -Th -x tmpfs')

---

### Post by scragar on 2009-09-19
Adding to EarthPigg if your system's graphical interfact ever does freeze and you're working on something important you can freeze that application in the hopes that it doesn't die itself when you close the graphical server(but unfortnately it's likely to do so when you resume because the Xserver changed, but not all aps do):
```
killall -STOP pidgin
sudo killall Xorg
killall -CONT pidgin
```

---

### Post by earthpigg on 2009-09-19
also, consider installing VirtualBox and installing Ubuntu within VirtualBox.

use that as your testing ground to do whatever completely nutty things you want to try with_out_ risking damage to your actual Ubuntu install.

remember that any time you type 'sudo', you had better know exactly what the command is going to do.

---

### Post by stderr on 2009-09-19
> **aaryan said:**
> so that helps me close the files that I'd have opened, but what if i need to close a directory, is there a separate function for that?

You'll need to actually explain what you mean by this... 

In programming, you typically open a file and get a **file handle** back. Then, you can use this file handle to read from and write to the file, until you decide to close the file (and lose the file handle).  A file is therefore open between the FH=open() and close() system calls. 

To "close a file" is really the responsibility of the program that opened it. To "close an application/script" is likely the responsibility of the user, as the user probably instigated it, and that's what the kill command does: kill a process (read: application/script). Note that applications/scripts may have opened files during their execution.

To "close a directory"... well, you never really "open" a directory; not in such a way as you'd need to "close" it, anyhow. 

I'm really not sure what you mean; are you getting confused?

```
cd path/from/my/home/directory/to/a/text/file
gedit mytextfile
```

Now the application gedit has opened the file /home/MY_USERNAME/path/from/my/home/directory/to/a/text/file/mytextfile. You can't kill the file mytextfile per se, but you can kill the gedit process, using one of the methods described above (e.g. kill `pidof gedit`). And there's no directory left open after this that you need to kill...

---

### Post by aaryan on 2009-09-19
Well what I meant was that say I have a directory named AARYAN on the desktop which has a file say aaryan.doc. I have closed the file aaryan.doc using pkill, but how do i close the directory AARYAN?

---

### Post by DrugCoder on 2009-09-19
are there any commands to manage firefox?
i mean surfing the internet without mouse

---

### Post by aaryan on 2009-09-19
well I guess you are right. Since we dont 'open' a directory in the real sense there is also no closing it.:)

---

### Post by lisati on 2009-09-19
> **aaryan said:**
> Well what I meant was that say I have a directory named AARYAN on the desktop which has a file say aaryan.doc. I have closed the file aaryan.doc using pkill, but how do i close the directory AARYAN?

OK I think I'm beginning to understand..... Are you using a program like Nautilus to browse the directory? If so, the usual way is to click on the "x" at the top right of the screen.

---

### Post by stderr on 2009-09-19
> **aaryan said:**
> well I guess you are right. Since we dont 'open' a directory in the real sense there is also no closing it.:)

Indeed :)

When you open a terminal (e.g. Applications->Accessories->Terminal) it at all times has a "**p**resent **w**orking **d**irectory". At the start, it's set to your home directory by default (/home/YOUR_USERNAME). You can query it with 

```
pwd
```

You change the PWD with the command "cd" (change directory). To exit the terminal, you use the command "exit", and that's the shell gone, along with its PWD. 

Here's another example. When you run

```
gedit myfile.txt
```

the shell (probably bash: the file /bin/bash) shoots off to find the program gedit: it actually resides at /usr/bin/gedit. The shell will open that application file (which is a binary file), and that application will run as a new process. That process will then open the file myfile.txt... until you close gedit, which will close myfile.txt, along with /usr/bin/gedit, dropping you back to the shell (/bin/bash). When you then type exit, the shell process will end, and the file /bin/bash may also close.

---

### Post by earthpigg on 2009-09-19
> **DrugCoder said:**
> are there any commands to manage firefox?
i mean surfing the internet without mouse

how about a terminal-based web browser?

```
sudo apt-get install lynx
```

then, go ahead and:

```
lynx ubuntuforums.org
```

also, since you are trying to hang out in the shell more:

-use nano instead of gedit.
-use htop or top instead of gnome-system-monitor.
-etc.... google search 'command line alternatives linux'

---

### Post by scragar on 2009-09-19
> **earthpigg said:**
> how about a terminal-based web browser?

```
sudo apt-get install lynx
```

then, go ahead and:

```
lynx ubuntuforums.org
```

also, since you are trying to hang out in the shell more:

-use nano instead of gedit.
-use htop or top instead of gnome-system-monitor.
-etc.... google search 'command line alternatives linux'
w3m is installed by default and looks prettier.
```
w3m google.com
```
q to **q**uit, g to **g**o to a url...

---

### Post by DrugCoder on 2009-09-23
GREAT! Just what i needed! Thanks! =)

---

