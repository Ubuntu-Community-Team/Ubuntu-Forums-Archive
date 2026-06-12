---
title: "advise me please - Want to Learn Commands"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Peeta on 2009-12-26
hello everyone 

i have no knowledge of linux or any commands in linux, but i want to learn it properly, Now my problem is that i did bought two books actually 3 books on linux but i think they are not for fresh newbie like myself, i need to start from scratch totally from 0. Getting to know GUI in GNOME is not a big deal. but i wanna learn hard way through command line. 
Can anyone suggest any such books or on line tutorials which explains from start.

---

### Post by candtalan on 2009-12-26
> **Peeta said:**
> hello everyone 

i have no knowledge of linux or any commands in linux, but i want to learn it properly, Now my problem is that i did bought two books actually 3 books on linux but i think they are not for fresh newbie like myself, i need to start from scratch totally from 0. Getting to know GUI in GNOME is not a big deal. but i wanna learn hard way through command line. 
Can anyone suggest any such books or on line tutorials which explains from start.

Welcome!

I have been using Ubuntu for years now, I do not use Windows at all, and I have almost never used the command line, it is not needed.

However, if you use, say, Ubuntu, you can use a terminal to examine commands in command line with the man command (think of instructions Manual).

For example
In a terminal type
man lspci

hth

---

### Post by Stunts on 2009-12-26
I would recommend that you start here:
[http://linuxcommand.org/](http://linuxcommand.org/)

Have fun on the CLI! It's a whole new world of amazement!

---

### Post by CaptainMark on 2009-12-26
Hows your general computer knowledge, if your new to computers in general id start with a beginners guide to using computers rather than linux specific, make sure you understand how the insides of your pc work too, that helps a lot.  If your not new to computers just switching over from windows or such like, your best way to learn is to play around, see what you can do and when you do something wrong, (which you will, i have) learn how to fix it. its a diy crash course

---

### Post by L Campbell on 2009-12-26
> **Peeta said:**
> hello everyone 

i have no knowledge of linux or any commands in linux, but i want to learn it properly, Now my problem is that i did bought two books actually 3 books on linux but i think they are not for fresh newbie like myself, i need to start from scratch totally from 0. Getting to know GUI in GNOME is not a big deal. but i wanna learn hard way through command line. 
Can anyone suggest any such books or on line tutorials which explains from start.

You might find this to be helpful :-

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by QLee on 2009-12-26
> **Peeta said:**
> hello everyone 

i have no knowledge of linux or any commands in linux, but i want to learn it properly, Now my problem is that i did bought two books actually 3 books on linux but i think they are not for fresh newbie like myself, i need to start from scratch totally from 0. Getting to know GUI in GNOME is not a big deal. but i wanna learn hard way through command line. 
Can anyone suggest any such books or on line tutorials which explains from start.

One thing you might want to look at is Linux from scratch, after you have built a system that way you will know quite a lot.
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

---

### Post by NFblaze on 2009-12-26
I cant really think of any particular books that are easy with the command line. You have to play with it, I suppose you can prefer to play around with it. That's really the number one thing to do. Though, I was very minimally familiar with the CLI, but this is the website tutorial I started with 

[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

BASH is a shell environment that is the default CLI for Ubuntu. Basically, I would view the tutorials and follow along in your OS.

Also, the programs **man, info**, and **apropos** are definitely your friends when learning the commandline.

After that, you can take it to the next level and read some Linux System Administration books, which usually are really focused on the commandline maintenance.

---

### Post by Peeta on 2009-12-26
Hello Friends, 

i really appreciate your valuable advise and thanks pointing me in right direction. 

cheers

---

### Post by falconindy on 2009-12-26
Force yourself to use it. If you can't find a command to do something, use 'man -k <searchterm>' to find a relevant command.

> I have been using Ubuntu for years now, I do not use Windows at all, and I have almost never used the command line, it is not needed.
There are many people who feel that a GUI is bloat, and that many tasks can be completed more efficiently by use of the command line ('wodim image.iso' to burn a CD, for example). It's also generally useful knowledge to have if you're going to stick with Linux in the long term.

---

### Post by ofb on 2009-12-26
And it's just fun. Exploring the system through he command line is a firm parallel with the old dungeon adventure games, especially the text ones.

Hey Peeta, you've got good advice above. If you don't want to keep a window open for the online references, pick up an old book from the library. When I got into Linux one of the biggest helps was my 1991 Unix Quick by Andrew Feibus. The command set has been expaned since then, but it's largely the same. And those old books are for beginners who didn't have a GUI option -- so they're quite thorough for the newbie.

---

### Post by teage3 on 2009-12-26
The online manuals are excellent as well. In case you are not sure what i am talking about, Just start firefox and the ubuntu startpage opens. This should be the default address setting --->http://start.ubuntu.com/9.10/<---

Just under the search bar there are some options. Click the _*help*_ link and you will get the official ubuntu documents page where you can find all kinds of use full info about ubuntu.

Here is the address for the online manual ---> [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)  <---

There you can find all kinds of commands for specific software in ubuntu. That has been my bread and butter for the command line. I hope this helps you.

---

### Post by fatality_uk on 2009-12-26
[http://linuxmanpages.com/](http://linuxmanpages.com/)

A great resource that provides a lot of detailed information

---

### Post by Chris Edgell on 2009-12-26
[http://ubuntuforums.org/showthread.php?t=1347150](http://ubuntuforums.org/showthread.php?t=1347150)

Hi peeta, I was just asking that not too long ago.  Do you want to go read the thread?  I liked it.

Good luck as  a newb
I am too

---

### Post by Mornedhel on 2009-12-26
> **ofb said:**
> When I got into Linux one of the biggest helps was my 1991 Unix Quick by Andrew Feibus. The command set has been expaned since then, but it's largely the same. And those old books are for beginners who didn't have a GUI option -- so they're quite thorough for the newbie.

Old books have pros and cons.

I have an old Bash O'Reilly book (with a bass -- the fish -- on the front). It's really great in that it explains in detail not only how to do things, but how they work, when you would do a task some way and when you should do it another way, why something is the way it is, etc. Unfortunately, it's for bash 2, so it will use an older syntax, deprecated forms (backticks versus $(), for instance), and won't make any mention of e.g. the new features in bash 4.

Or a UNIX programming book will explain how to work with the GNU standard toolchain, gcc, make, and gdb, and completely skip autotools and other building systems.  It will, however, not skip the gory details of gcc invocation, so you'll know how to use it, instead of blindly clicking around an IDE, never really learning to compile.

Or a generalist Linux book will have you manage library dependencies by hand because it's pre-packaging systems, and using awk to do extensive text manipulation because Perl wasn't as common at the time.

Overall, using old books makes you learn more in-depth skills, but you need to complement them with lighter and most importantly more up to date information.

---

### Post by ken_do_san on 2009-12-26
Hi Peeta, I've attached a jpeg that can be used as wallpaper for your desktop, it has some of the commands you may find useful to start with.  All the best on your journey with Linux (Ubuntu).

Just a quick note, be mindful of the 'rm' command, if you enter it in the wrong directory you can render your system inoperable.

Cheers

---

### Post by k3lt01 on 2009-12-26
Excellent screenshot ken_do_san.

Peeta, we are all newbies at some stage or another and I admire your desire to get into Linux so quickly. I asked for some help a few weeks ago and was advised to get into the Man Pages. They are a difficult thing to get a grip on but persistence will pay off as it eventually becomes like a second language.

Apart from the Man pages which you have been given a link to already there is the Advanced Bash-Scripting Guide, which I think has already been mentioned as well. You could also take a look at the many informative threads in the Tutorial section which often explain what the commands do. If there is anything that you find of interest, for example setting up a server or setting up your own repositories, then you practice using the information from the thread along with information from the Man pages and you learn how to use the CLI as you go.

You could take a look at [The Linux Documentation Project]("http://tldp.org/index.html") and [Full Circle Magazine]("http://fullcirclemagazine.org/") for more information as well.

I was also given another great piece of advice by Bodhi.zazen and that was to ask questions. The community is here to help.

---

### Post by s3a on 2009-12-26
In my opinion, all you need to know is sudo, sudo apt-get install packagename, and sudo apt-get remove packagename for now. Then you can learn more just by browsing the forums and "eavesdropping" on other threads. That's what I did and I know many commands :).

---

### Post by ankspo71 on 2009-12-27
Hi,
I think two good areas to learn first is... 

Working with files and folders, and navigating the system:
*cp, mv, tar, cd, ls, mkdir, rm, rmdir, etc.*
Be careful with remove commands though.

Then working with the package management system:
*apt-get, apt-cache, aptitude, *etc

This would take care of some of the basics... and should be a good learning experience.

To find help in the terminal, you can use the following commands:
*info* command
*man* command
*command* --help

also, using the above three commands works for software names too, and they will tell you the command line options for the software. For example: see ***man brasero*** in the terminal.

Have fun learning commands.:P

---

### Post by Peeta on 2009-12-28
thank you guys 

i was awesome you guys gave me so much information and very useful exactly what i was looking for and Ken that was great wallpaper. Now i am sure i am going to enjoy my xmas break.

actully i should have post my other problem in here. any way i will tell you guys what happening before i did partition on my HDD with at Imac and install ubuntu. now i manage to grab a spare pc and install Ubuntu there and want my Imac HDD restore  as one and remove ubuntu from there. 

boot camp giving me massage which is as follows. 


"The startup disk must be formatted as single mac OS extend ( journald ) volume or already partitioned by boot cam assistant for installing windows"

and it refuse to restore. last time it was ok when i removed partition for windows

Any ideas whats happening 

thnx guys

---

### Post by Tnoty on 2010-01-22
> **Peeta said:**
> hello everyone 
 
i have no knowledge of linux or any commands in linux, but i want to learn it properly, Now my problem is that i did bought two books actually 3 books on linux but i think they are not for fresh newbie like myself, i need to start from scratch totally from 0. Getting to know GUI in GNOME is not a big deal. but i wanna learn hard way through command line. 
Can anyone suggest any such books or on line tutorials which explains from start.
 
Hello Peeta,
I'm also new to linux line commands and BASH scripting. Don't know if you've found what your looking for yet, but here's a link to a site I've been using to bone up on BASH Scripting that may be of use to you. [http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/index.html](http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/index.html)
 
Tnoty

---

