---
title: "how powerful is the terminal?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-26
I was just curious how powerful can the terminal be?

the only thing i know so far is that:

you can use the terminal to fix things/trouble shoot inside of the os. 
force a different architecture file to install inside the os. 

actually, i met this nerdy girl inside a bookstore. and she told me she has a mac ibook G4. and she uses the bash command line to connect wirelessly to a projector for a presentation for her school. (when she didn't have the wire to connect it.) I thought that was amazing.

how powerful is the terminal? what other things can you do inside the terminal?

---

### Post by atngplusultra on 2008-12-26
try this

sudo apt-get install emacs

emacs -batch -l dunnet

craziest text-based game ever.
I'm kinda being silly, but, it's really incredible, I sometimes wonder why I bother even using Ubuntu, if the average level of programming intelligence can understand that game, cuz at points, I get lost.

---

### Post by crazyness003 on 2008-12-26
the power of the terminal is only limited to your knowledge of BASH.
If you come from a windows background, the terminal is like the "cmd" in windows.
Back before the NT systems came out [noparse](up to win98)[/noparse], windows ran on top of the "cmd" or DOS as it was.

In the Linux world, the same applies: The Desktop Manager (DM, in your case, mos likely Gnome) runs on top of the Linux kernel, which can be controlled by the terminal (in this case an emulator of the terminal)

Basically all this means is that in reality, everything you do is run through a terminal...you just dont see it, since the gui's that all the good boys and girls put together, make it look seamless. But when you take that bad-boy out and start issuing your own commands, you're only limited by your knowlege, the power of yourmachine, and the hardware/infrastructure you run on.

So yeah, that "nerdy girl" that can "hijack" the projector, can do it through the terminal. But if someone took the time, they could make a nice gui to run on top of her commands, then anyone who can point and click can run wireless presentations to the projector.

Hope this gives you some insight at the power of the terminal. Besides, the terminal is not dangerous until you you start doing what you dont understand. 
[SIZE=4][COLOR=Red]**EXAMPLE: DO NOT TRY THIS**[/COLOR][/SIZE]
```
sudo rm -rf
```Heres a [youtube video]("http://www.youtube.com/watch?v=wWOjmvWPRvQ") someone made to demo what the above command does in one line. (It deletes EVERYTHING. Including the operating system. so yeah, dont do it)

---

### Post by wd5gnr on 2008-12-26
I always find it amusing that Linux as become synonymous with X11 since I've been using Unix since the 7th edition. Back then EVERYTHING was the shell. The GUI (X11) is an add on to Unix (and Linux has a very similar structure).

So in short, just about anything you can do in Linux you can do from the command line. I use it all the time just to launch GUI programs (rarely use a start menu kind of thing). Even thing you think of as GUI only (reading PDFs, or playing music) have command line alternatives if you want. A lot of programs (e.g., emacs) have dual modes and will use the GUI if present and won't if it doesn't have it.

Don't get me wrong, I use 90% GUI programs (Firefox, Thunderbird, OpenOffice, glade, Amarok -- even Code::Blocks sometimes). But the real power to the shell is not to run text-only word processors or e-mail programs. Rather it is how you can expressively tell the computer what you want to do and then automate it through scripting.

So for example, suppose you have a directory structure like this:

/home/al/school/classes/ee4043
/home/al/school/classes/ee4213
/home/al/school/classes/ee4931

Each class directory has a file called calendar.txt.

Suppose you are at the /home/al/school/classes directory and you want a file with all the calendars in it. You could say:

cat */calendar.txt >allcal.txt

Or what if it were more complex? Suppose you had 3 sections in each class (sectionA, sectionB, and sectionC) and each had a calendar.txt file. You might want calendars for A and B only:

cat */section[AB]/calendar.txt > cal-ab-only.txt

If you wanted to search all the calendars for the midterm dates you might say:

grep -i midterm */*/calendar.txt

Of course, your integrated calendars would be "sorted" by class. But the sort command could put the lines in whatever order you wanted. Tools like awk and perl could manipulate the files in lots of complex ways.

So you can select and process arbitrarily complicated selection criteria (yes, some GUI file managers can do that too, but many can't -- especially spanning multiple directories like the above example). Then using pipelines you can string together simple "verbs" to do things. So you might have:

grep -i midterm */*/calendar.txt | sort {some options here to sort on the date field} | lpr

To print a sorted list of the midterm dates.

for will let you process a bunch of items one at a time. The find command lets you scan through directory trees in various interesting ways.

Of course, when you have a GUI crash (new NVidia drivers didn't work) knowing the command line will let you fix the system easily using a console or a serial terminal.

Once you know what you want to do, you can write "scripts" that automate things. So you might make a script called printcal so when you wanted the midterms you could write:

printcal AB midterm

(or printcal ABC final) 

The above is just off the top of my head and not tutorial in nature. But start here:
[http://linuxcommand.org/](http://linuxcommand.org/)

Someone once said you don't have to know how an engine works to drive a car. But all the best drivers know how an engine works. Same goes for any computing system. You don't have to know the command line (or how to write C code, or what an MMU is, or what the advantage of two-level microcode is, or what a CMOS inverter looks like in silicon). But the more you know, the better off you'll be ;-)

On a related note, many people don't understand how flexible X is either. You can use X to run programs across the network. So you can launch a compile job on a remote machine, or start a movie playing from your computer to the screen down the hall if you master its intricacies. It isn't like Windows where the screen is married to your computer and getting the data across the network to another screen requires a hack.

---

### Post by twiz86 on 2008-12-26
Terminal is God.

---

### Post by kerry_s on 2008-12-26
the terminal is only limited by your imagination.
i often prefer to use a terminal file manager to manage my system and edit text, check resources, etc...

most people prefer straight command line or mc, i prefer the older smaller deco for my cli file manager. see pic

---

### Post by dmizer on 2008-12-26
I have a server with no keyboard, mouse, or monitor attached and I [control it all remotely](http://en.wikipedia.org/wiki/Ssh) (from anywhere in the world) by command line. From that server's command line, I can remotely [turn on](http://en.wikipedia.org/wiki/Wake-on-LAN) or turn off any computer on my network, [install and configure systems](http://en.wikipedia.org/wiki/Virtual_machine), [boot computers with no hard disk or CDROM drive](https://help.ubuntu.com/community/ThinClientHowto), [proxy a remote support session](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/), [stream my music](http://www.gnu.org/software/gnump3d/) to my smartphone or my office computer, and of course ... [host a website](http://en.wikipedia.org/wiki/LAMP_(software_bundle)). And, I've only begun to scratch the surface of what I can do with Linux on the command line.

Anything you do in the GUI can be done in the command line, but there are tons of things that can be done in the command line that can't be done in a GUI.

---

### Post by enoughsaid05 on 2008-12-26
in my opinion, it is very very powerful, more powerful than gui. you can do something specifically via terminal that is out of reach for gui. one thing though, using gui is less taxing on the brain, because as a newbie i have to think before i type in command or create configuration file. if the syntax is wrong, you have to read the manual which is extremely wordy(well based on my experience trying to configure mutt)

---

### Post by sportscrazed2 on 2008-12-26
i just use it to add/remove apps because i don't have to wait for add/remove to check for new apps everytime and all that crap

---

### Post by inxygnuu on 2008-12-26
Extremely. It can do anything you tell it to with commands. I just wish you could delete everything when you use rm -rf / (It would be cool to see things start to disappear, like the gnome interface, and eventually your system would just blow up because of some error:P) Overall, I can do more things in terminal than I can in a GUI.

---

### Post by akelsall on 2008-12-26
I think you should be starting to see just how powerful the terminal can be. Here are a few more examples of what you can do easily from the terminal:

You can rotate or resize images "in batches" (i.e. you could easily resize hundreds of images in a folder with one command, all from the command line).

You can move files easily using terminal commands. Let's say you have a directory that has a mix of photos. Some have the word *house* in them, some have the word *mountain*, and some have the word *action*. You could move all the images with *house* in them to a directory named house using the command "mv *house*.jpg /housepics/". You could use the same method to move all the images with the *mountain* in them via "mv *mountain*.jpg /mountains/" and, the last batch (*action pics*)via "mv *actin*.jpg /actionpics/"). 

I use a script file to copy all my important system files (e.g. /etc/network/interfaces, /etc/resolv.conf to name a few) to my slave drive. I have all the commands stored in a singe file, then make that file executable by changing permissions to 700, then run it. 

Other people have said it, and I'll say it as well. The possibilities are endless. Just experiment, pick up a book or two, and you'll find many other uses for the terminal (a.k.a. command line).

Andy

---

### Post by scorp123 on 2008-12-26
This is based on a joke that some guys and me came up with on the Mint forums ... it was at the time one of the "Star Wars" movies was released ("Episode III" I think?) and the various advertisements made a big deal of Annakin Skywalker falling to the "dark side" (like we didn't know that already after watching the first three original "Star Wars" movies? :D ) ... So here we go:


[INDENT]**The Sith... ^H^H^H Shell Code**

GUI's are a lie, they're just front-ends to the shell.
Through the shell, I gain sudo.
Through sudo, I gain power.
Through power, I gain root.
Through root, my chains are broken.
uid=0 shall free me.[/INDENT]

---

### Post by Kosimo on 2008-12-26
I'm starting to love terminal more and more :)

---

### Post by crazyness003 on 2008-12-26
If i knew all the terminal commands, id nix gnome altogether. Just run the X server and use xterm to get all my work done. But i lack the knowledge to do that. I tried it once, but had a panic attack.

Hooray black background and white writing!

---

### Post by bodhi.zazen on 2008-12-26
See this link : 

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by shiningkenmonster on 2008-12-27
wow, thanks guys. is there an ebook i could download somewhere? because i don't have an internet connection at home.

---

### Post by shecky on 2008-12-27
This might be a good start: [http://www.gnu.org/software/bash/manual/](http://www.gnu.org/software/bash/manual/)

Also, never forget you get a lot of command line options from using "--help" or "-h" after a command, or using the manpages, which are automatically added with their corresponding package.
```
ls --help
man paste
```

---

### Post by obsrv on 2008-12-27
In terminal we trusted, in terminal we trust. -- Adomas Bosanova and Evelina Jaskelevi&#269;i&#363;t&#279;

---

### Post by niteshifter on 2008-12-27
Hi,

Top of [this page]("http://tldp.org/guides.html"). (The Linux Documentation Project):
Bash Guide for Beginners
Advanced Bash-Scripting Guide

Enjoy!

---

### Post by Sorivenul on 2008-12-27
LinuxCommand has already been mentioned.
See also: 
[Ubuntu Cheat Sheet]("http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/")

If you open a terminal and are looking for something to do, learn the "whatis" and "apropos" commands. 
Examples:
```
sorivenul@mainframe ~ $ whatis ifconfig
ifconfig (8)         - configure a network interface

```

```
sorivenul@mainframe ~ $ apropos alsa
aconnect (1)         - ALSA sequencer connection manager
alsactl (1)          - advanced controls for ALSA soundcard driver
alsamixer (1)        - soundcard mixer for ALSA soundcard driver, with ncurse...
amidi (1)            - read from and write to ALSA RawMIDI ports
amixer (1)           - command-line mixer for ALSA soundcard driver
aplay (1)            - command-line sound recorder and player for ALSA soundc...
arecord (1)          - command-line sound recorder and player for ALSA soundc...
aseqdump (1)         - show the events received at an ALSA sequencer port
aseqnet (1)          - ALSA sequencer connectors over network
asoundconf (1)       - utility to read and change the user's ALSA library con...
speaker-test (1)     - command-line speaker test tone generator for ALSA

```

These two commands give brief descriptions of terminal commands and more, along with their corresponding "man" pages.
Example:
```
man sudo
```

You shouldn't need a network connection, as all the documentation for what you have should already be available. :D

Good luck! Cheers!

---

