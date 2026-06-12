---
title: "New Guy...How Do I Install Things"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by pappasaa on 2008-12-17
First day useing anything like linux ubuntu...I want to know how to install things. I am trying to install xnee but i have no clue where to start.

Do i need to run somthing like a command promp thing to get this installed or what. I dont even know where to start so if anyone could tell me a step by step to installing programs or scripts...not even sure what they are called that would be great. I dont even know what files to put my programs in....

what i would need is like:

click system > admin..> ect. because i am not sure what is going on with this. I love it...and i can pic things up quick...thanks in advance

---

### Post by llamakc on 2008-12-17
The GUI way is to use either "Add/Remove Programs" or "Synaptic".

Synaptic is found in the GNOME menu by navigating to 

SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER

When you start Synaptic it will prompt you for YOUR password. Enter it.

Next, in the "Quick Search" window, type xnee

It will return two packages. On the checkbox to the far left, left-click and choose 'mark for installation'.

Now, click "Apply".

All done.

In the terminal you could type:

```

sudo aptitude install xnee

```

---

### Post by snova on 2008-12-17
xnee? That doesn't sound very useful... what do you want to do? I get the feeling that's the wrong program.

Either way, try Applications -> Add/Remove.

Or, System -> Administration -> Synaptic Package Manager, which is closer to the underlying system.

---

### Post by adult swim on 2008-12-17
i think you will need to go to system>administration>software sources and make sure that the first four boxes are checked before you follow llamakc's good advice.

---

### Post by aysiu on 2008-12-17
> **snova said:**
> xnee? That doesn't sound very useful... what do you want to do? I get the feeling that's the wrong program. I get that same feeling.

Here's a description of the *xnee* package: > Xnee is a suite of programs with recording, replaying and 'distribution' capabilities for the X Window System protocol. 

---

### Post by anjilslaire on 2008-12-17
1. Open Synaptic from the menu (I'm on Xubuntu, so can't point you exactly where. System, most likely)
2. in th search field, enter xnee
3. Select it when it's found as "Mark for installation". It will automatically select anything else it requires also.
4. Click Apply.
6. Done. It will show up in the menu somewhere

Alternately, open a terminal and do:
```

sudo apt-get install xnee

```

Doh! Too slow!!

---

### Post by halitech on 2008-12-17
I think llamakc was just using xnee as an example program since the OP didn't list any specific program they wanted to install :)

---

### Post by DannStarr on 2008-12-17
Ok, i'm in the same boat as pappasaa above, and when I go in to the synaptic package manager, I put in my password and then I get the following error msg...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I manually run this dpkg thing?

---

### Post by xjcannonx on 2008-12-17
Easiest way to start off is by ways of the GUI(graphical user interface) and navigate to System-->Administration-->synapticpackage manager
In there are a whole bunch of stuff to install (repo's) im not at my ubuntu but i don't think xnee  is in there?<--EDIT:I stand corrected. After you get a hang of things it way become easier to install from the terminal- Applications-->Preferences-->terminal
```
sudo apt-get install whatever
```
here is a help guide
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")
Some programs need to be compiled, usually there is a readme inside the tar file with instructions(usually ```
./configure
make
sudo make install
```...no executables in linux...if there is an option to download a .deb or .tar, .deb are easier...

---

### Post by halitech on 2008-12-17
> **DannStarr said:**
> Ok, i'm in the same boat as pappasaa above, and when I go in to the synaptic package manager, I put in my password and then I get the following error msg...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I manually run this dpkg thing?

open a terminal and run the command

```
sudo dpkg --configure -a
```

---

### Post by snova on 2008-12-17
> **halitech said:**
> I think llamakc was just using xnee as an example program since the OP didn't list any specific program they wanted to install :)

> **pappasaa said:**
> First day useing anything like linux ubuntu...I want to know how to install things. I am trying to install xnee but i have no clue where to start.

Nope. :)

> **DannStarr said:**
> Ok, i'm in the same boat as pappasaa above, and when I go in to the synaptic package manager, I put in my password and then I get the following error msg...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I manually run this dpkg thing?

Open a terminal- Applications -> Accessories -> Terminal, and type

```
sudo dpkg --configure -a
```

And hope it works.

---

### Post by pappasaa on 2008-12-17
wow...that was quick...thanks for getting back to me so fast. I am going to test it out and let you know how it goes...

PS...i know what xnee is and I need this program for a few things i do. I used a windows based program before but I wanted to see what linux was all about....i think its better then windows and i have only had it on my system for two hours now...thanks again

---

### Post by Therion on 2008-12-17
A general primer on how to install software in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by halitech on 2008-12-17
>  Originally Posted by halitech  View Post
I think llamakc was just using xnee as an example program since the OP didn't list any specific program they wanted to install 

> **snova said:**
> Nope. :)


ok, I guess I missed that when I was reading the original post :(

---

### Post by DannStarr on 2008-12-17
Hmmm, that was my first terminal experience!

It spent some time loading something, then told me a flash player 10 was not intalled, and the synaptic package manager still has the same error

---

### Post by tbuss on 2008-12-17
> First day useing anything like linux ubuntu...I want to know how to install things. 

**pappasaa,**

This link might be useful. 

**Complete Guide to Software Installation in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=781352]("http://ubuntuforums.org/showthread.php?t=781352")

Welcome to Ubuntu!

---

### Post by pappasaa on 2008-12-17
ok...i tried to find xnee in all the GUI ways all of you listed but cant seem to find xnee. 

I downloaded and extracted all files to my desktop. Is there a better location to download this file too... Thank you again

---

### Post by adult swim on 2008-12-17
> **adult swim said:**
> i think you will need to go to system>administration>software sources and make sure that the first four boxes are checked before you follow llamakc's good advice.
did you do this?

---

### Post by snova on 2008-12-17
> **pappasaa said:**
> ok...i tried to find xnee in all the GUI ways all of you listed but cant seem to find xnee. 

I downloaded and extracted all files to my desktop. Is there a better location to download this file too... Thank you again

It's in universe. Do you have universe repositories enabled?

Because you're going the hard way... and, being new, we're going to try to spare you that. :)

---

### Post by pappasaa on 2008-12-17
> **adult swim said:**
> did you do this?


yes...

---

### Post by pappasaa on 2008-12-17
> **snova said:**
> It's in universe. Do you have universe repositories enabled?

Because you're going the hard way... and, being new, we're going to try to spare you that. :)

never heard of it so i am not sure if i do or not...how do i find out

---

### Post by adult swim on 2008-12-17
go to applications>accessories>terminal and enter in ```
sudo apt-get update
``` it will ask for your password, type that in and hit enter, let it run until its done and then enter in ```
sudo apt-get install xnee
``` and post the output that is returned.

---

### Post by snova on 2008-12-17
> never heard of it so i am not sure if i do or not...how do i find out

If you checked those four boxes, they are.

Try refreshing the package list from Synaptic. Just in case it hasn't been done already...

---

### Post by pappasaa on 2008-12-17
> **adult swim said:**
> go to applications>accessories>terminal and enter in ```
sudo apt-get update
``` it will ask for your password, type that in and hit enter, let it run until its done and then enter in ```
sudo apt-get install xnee
``` and post the output that is returned.



here is what i got...think it may have worked but not sure...

```
desktop:~$ sudo apt-get install xnee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xnee
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 1053kB of archives.
After this operation, 3154kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid/universe xnee 3.02-0ubuntu1 [1053kB]
Fetched 1053kB in 3s (279kB/s)
Selecting previously deselected package xnee.
(Reading database ... 125938 files and directories currently installed.)
Unpacking xnee (from .../xnee_3.02-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up xnee (3.02-0ubuntu1) ...

```

---

### Post by snova on 2008-12-17
Yep. It's done.

You could have gone through the GUI, I suppose, but it's been installed, one way or another.

Basically, it:

[LIST=1]
[*]Read its database
[*]Told you there were some extra packages you could remove if you pleased (I suggest leaving them)
[*]Gave a report of all actions that would be taken (in this case, install one package)
[*]Reported how much disk space would be used afterwards
[*]Downloaded packages
[*]Unpacked them
[*]Did a little setup
[/LIST]

Quite transparent.

---

### Post by pappasaa on 2008-12-17
nice...now i just neet to find out how to open it and use it...lol...thanks for your help. I will RTM a bit more tonight...thanks to all of you

---

### Post by adult swim on 2008-12-17
you got it.  it looks like it doenst install any shortcuts to menus.  if you go to /usr/share/xnee/xnee.txt there is a manual for it.  you can launch a GUI for it if you press alt+f2 and type in ```
gnee
```
it also looks like you can add a xnee applet to your panel if you right click your taskbar, select add to panel and then scroll down to "pnee"

---

### Post by pappasaa on 2008-12-17
> **adult swim said:**
> you got it.  it looks like it doenst install any shortcuts to menus.  if you go to /usr/share/xnee/xnee.txt there is a manual for it.  you can launch a GUI for it if you press alt+f2 and type in ```
gnee
```
it also looks like you can add a xnee applet to your panel if you right click your taskbar, select add to panel and then scroll down to "pnee"

yes it did...man...i love this site...just makes the OS that much better...great support from the community. I hope to get better at this so i can pay it forward...thanks

---

