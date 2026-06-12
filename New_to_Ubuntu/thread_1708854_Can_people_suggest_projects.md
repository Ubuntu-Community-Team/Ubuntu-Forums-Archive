---
title: "Can people suggest projects?"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by B3ntleg on 2011-03-17
Ok here is the deal I am rubbish with linux but am trying to get better.  But I have been using windows for that long I cannot really remember how to use a computer properly.  

I know I am capable I used an Amstrad when I was under 8 and played around with the file system commands alot.  Used to do alot of command stuff in RISC OS.  And I wrote a 4 line piece of code in Pascal to bypass my 6th form lockouts on thier Windows NT 4.0 systems.

But I haven't done anything real with a computer in like 10 years and am pretty ashamed.  I have been booting up Windows and on rare occasion having to be a power user but even that is pretty rudimentry stuff.

So I am trying to regain a firm grasp of linux to re-educate myself.  I have been reading some tutorials and such.  But in order for me to learn I need to actually be figering out how to do stuff.  My most recent thing I have been compiling some source code. 

My main problem is that I can not get a firm grasp of the file structure more specficly when it comes to multiple drives in the terminal enviorment.  I know this must seem like the most newbie problem ever but their we go.

So I was hoping if anybody could suggest some projects for me to do that will force me into using the terminal?

And I really want projects that will have me using multiple drives in the terminal, but any other project that will just give me an all round firm grasp would be appericated.

---

### Post by ironic.demise on 2011-03-17
> **B3ntleg said:**
> Ok here is the deal I am rubbish with linux but am trying to get better.  But I have been using windows for that long I cannot really remember how to use a computer properly.  

I know I am capable I used an Amstrad when I was under 8 and played around with the file system commands alot.  Used to do alot of command stuff in RISC OS.  And I wrote a 4 line piece of code in Pascal to bypass my 6th form lockouts on thier Windows NT 4.0 systems.

But I haven't done anything real with a computer in like 10 years and am pretty ashamed.  I have been booting up Windows and on rare occasion having to be a power user but even that is pretty rudimentry stuff.

So I am trying to regain a firm grasp of linux to re-educate myself.  I have been reading some tutorials and such.  But in order for me to learn I need to actually be figering out how to do stuff.  My most recent thing I have been compiling some source code. 

My main problem is that I can not get a firm grasp of the file structure more specficly when it comes to multiple drives in the terminal enviorment.  I know this must seem like the most newbie problem ever but their we go.

So I was hoping if anybody could suggest some projects for me to do that will force me into using the terminal?

And I really want projects that will have me using multiple drives in the terminal, but any other project that will just give me an all round firm grasp would be appericated.

ok, Not sure about a project...
How about this?

Harddrives can be  found with```
fdisk -l
```
to find out more about fdisk type ```
man fdisk
``` press q to quit the manpage

to mount a hard drive type ```
mkdir /media/diskname (where discname is whatever you want the directory to be called, and you can make this anywhere, not just under /media i.e. /home/user/discname
```
```
sudo mount (device from fdisk, i.e. /dev/sdc) (directory specified in mkdir)
```

For more information on any commands type ```
man (command)
```
because I'm not sure I specified EVERYTHING needed for the mount command.

---

### Post by Vi3tHoneyX on 2011-03-17
> **B3ntleg said:**
> My main problem is that I can not get a firm grasp of the file structure more specficly when it comes to multiple drives in the terminal enviorment.  I know this must seem like the most newbie problem ever but their we go.

If you let Ubuntu mount the drive (by just clicking the drive) it will mount it under ```
/media/(drive goes here)
```

Navigating using Nautilus is a good way to get familiar with file structure on your system. :)

---

### Post by Grenage on 2011-03-17
> **B3ntleg said:**
> Ok here is the deal I am rubbish with linux but am trying to get better.  But I have been using windows for that long I cannot really remember how to use a computer properly.  

I know I am capable I used an Amstrad when I was under 8 and played around with the file system commands alot.  Used to do alot of command stuff in RISC OS.  And I wrote a 4 line piece of code in Pascal to bypass my 6th form lockouts on thier Windows NT 4.0 systems.

But I haven't done anything real with a computer in like 10 years and am pretty ashamed.  I have been booting up Windows and on rare occasion having to be a power user but even that is pretty rudimentry stuff.

So I am trying to regain a firm grasp of linux to re-educate myself.  I have been reading some tutorials and such.  But in order for me to learn I need to actually be figering out how to do stuff.  My most recent thing I have been compiling some source code. 

My main problem is that I can not get a firm grasp of the file structure more specficly when it comes to multiple drives in the terminal enviorment.  I know this must seem like the most newbie problem ever but their we go.

So I was hoping if anybody could suggest some projects for me to do that will force me into using the terminal?

And I really want projects that will have me using multiple drives in the terminal, but any other project that will just give me an all round firm grasp would be appericated.

If you have a spare machine and a masochistic urge, try and get a mapserver or something working.  You undoubtedly have no need for such a thing, but getting it to work when you have little experience will be... educational.

---

### Post by B3ntleg on 2011-03-17
> **Vi3tHoneyX said:**
> If you let Ubuntu mount the drive (by just clicking the drive) it will mount it under ```
/media/(drive goes here)
```Navigating using Nautilus is a good way to get familiar with file structure on your system. :)

Thankyou!!! That was actually the problem I could never find it in the terminal.  And forced to use Nautilus to access the drive which didn't help when having to use the terminal.  Like I said new to linux and haven't used a computer properly in 10 years.

---

### Post by QLee on 2011-03-17
[QUOTE=B3ntleg]...
So I am trying to regain a firm grasp of linux to re-educate myself.  I have been reading some tutorials and such.  But in order for me to learn I need to actually be figering out how to do stuff.  My most recent thing I have been compiling some source code. 
...

So I was hoping if anybody could suggest some projects for me to do that will force me into using the terminal?

And I really want projects that will have me using multiple drives in the terminal, but any other project that will just give me an all round firm grasp would be appericated.[/QUOTE]

Ubuntu is a distro designed to be easy to use for the inexperienced user and, as such, it doesn't force you to get past, click on an icon, most of the time. For you to get an in depth instruction it might be advisable for you to do something like LFS, linux from scratch, which takes you through from the ground up. After you have built a GNU/Linux system in that way you will know quite a bit. Another possibility that several forum members favour is the Arch distro, it likely would be easier than LFS.

What could work well, if you have the space for another partition, is keep an install of Ubuntu as your desktop system and use a test system to learn. That way, when you muck things up you can reboot to a working system configured as you want it and research what is wrong. I find that easier than having to use a live CD to fix a broken system. If you have sufficient resources, a virtual solution instead of a separate partition might be a useful way to manage things.

Develop patience, nothing really useful is learned in an instant and you will have to unlearn some things you have accepted for some time, similar to most Windows power users who switch.

---

### Post by Vi3tHoneyX on 2011-03-17
I say it takes about a month or two to fully get adjusted to Ubuntu. Later on down the road if you really feel up to it you can try building your entire OS from scratch like QLee suggested. :) (you might see the distro Gentoo pop up around the forum. Gentoo is a LFS distro. Very challenging but rewarding when you build it correctly)

I personally just stick to Ubuntu because it works well.

---

### Post by TechWiz2100 on 2011-03-17
I like setting up servers on my spare time in VM or on spare machines. Setting up sendmail with gmail smtp is one hell of a job... Oh and Ubuntu server is command line by default so if anything toss that onto a partition and fiddle with that.

---

### Post by GrouchyGaijin on 2011-03-17
I don't know about any projects, but I'm new too.  I've been using Ubuntu for about six months.  Believe it or not, I have migrated to the command line because I'm lazy.

I've found that things really are a lot quicker when the GUI isn't involved.

You could copy or write some really basic scripts to do things you want done and then set an alias for the command to run the script.

Example: ```

#!/bin/bash
cp /home/john/Documents -r /media/Elements/ubuntu/
cp /home/john/scripts -r /media/Elements/ubuntu/
cp /home/john/conkys -r /media/Elements/ubuntu/
cp /home/john/Pictures -r /media/Elements/ubuntu/
cp /home/john/.bash_aliases /media/Elements/ubuntu/

```

This copies all the stuff in those folders plus my .bash_aliases file to a folder called Ubuntu on an external hard drive.

---

### Post by B3ntleg on 2011-03-17
> **GrouchyGaijin said:**
> I don't know about any projects, but I'm new too.  I've been using Ubuntu for about six months.  Believe it or not, I have migrated to the command line because I'm lazy.

I've found that things really are a lot quicker when the GUI isn't involved.

You could copy or write some really basic scripts to do things you want done and then set an alias for the command to run the script.

Example: ```

#!/bin/bash
cp /home/john/Documents -r /media/Elements/ubuntu/
cp /home/john/scripts -r /media/Elements/ubuntu/
cp /home/john/conkys -r /media/Elements/ubuntu/
cp /home/john/Pictures -r /media/Elements/ubuntu/
cp /home/john/.bash_aliases /media/Elements/ubuntu/

```This copies all the stuff in those folders plus my .bash_aliases file to a folder called Ubuntu on an external hard drive.

Yeah thanks this is the kind of thing I was really looking for.  I am trying to find things to that will make me write bash script.  

Also to the other posters I want to thank you all.  And I am going to look into LFS and brick some virtual machines.

---

### Post by QLee on 2011-03-17
[QUOTE=B3ntleg]...I am trying to find things to that will make me write bash script.  
...[/QUOTE]

You might find these useful:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I think someone already mentioned that you can read the manual page for a command by entering, man <commandname>, in a terminal window.

Good luck! Although, it won't be through luck, careful logical work will help you win.

---

### Post by ironic.demise on 2011-03-20
Why not think of a small idea and then start it, In my experience, it WILL grow.

For example, I wrote a script to copy some html files to a server on a regular schedule and backup... That way I never "messed up" my webpage. (Simple html, nothing big, just "hello world" stuff)

That was a few months back, now it manages the structure of the page, adds blog posts and images to the gallery, updates server status and can change the banner image all at the click of a button...

And I never had any trouble or a moment I found I was "trying" to learn... it was just fun.

Needless to say, it also spilled out into other things such as a money manager/logger, games, calendar-esque manager, friend tracker, camera manager.

---

