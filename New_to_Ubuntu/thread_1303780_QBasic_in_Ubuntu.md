---
title: "QBasic in Ubuntu?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by six30two on 2009-10-28
... So, I know people are going to scoff at me for asking this. There's all kinds of posts like this all over the internet, but none of them answer my question. So I need to ask it.

First of all, let me begin by saying I KNOW Basic is pretty much a Windows language. I've only recently seen the light that is the glory of Linux, and believe me when I say I'd switch to strictly Linux if I could, but I can't right now.

As it stands, I know very little about Linux. I'm a total noob. I'm just beginning to get into it and learn it and understand it. 

What I'm wondering is if there is a way to get Visual Basic Express 2008 to run through Wine. Or another Basic compiler that uses the exact same keywords/identifiers/commands etc. as VBE2008. I need it for a class, and it'd make life easier if I could use it on my Linux-only laptop (screw dual booting - I like Linux too much ). I've tried a few other programs that are supposed to emulate Basic, or are Basic-like languages, but I need something that is exactly like VBE2008 for one of my classes.

On a side note, I have Gambas installed, but... I don't think it's similar enough to VBE.

Is this at all possible? :(

---

### Post by SteveDee on 2009-10-28
To be honest, if you are serious about writing MS VB code you need to do it on a system running MS Windows. Wine is not going to give you a perfect environment to develop and test your software. I have an IDE drive caddy which I slot in when I need to do something on Win2000 (their best version!).

But if you still want to proceed, look at the reviews at WineHQ. Here is one I quickly found for VB 2005: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4679](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4679)

Gambas is a closer match to VB.classic (i.e. V5/6). If you just like working with Basic (as I do) then Gambas is a good way to go on Linux.

---

### Post by OffAxis on 2009-10-28
Kbasic might do it for you.

[http://www.kbasic.com/](http://www.kbasic.com/)

---

### Post by rCXer on 2009-10-28
Since QBasic is a dos program it can be run in a dos emulator such as DOSBox.  See [this thread](http://ubuntuforums.org/showthread.php?t=608535).

You could also try [FreeBasic](http://www.freebasic.net/) which was inspired by qbasic and has a linux version. Just [download](http://www.freebasic.net/index.php/download) and unpack the regular linux version (not standalone) to "/home/username/FreeBASIC" and execute this in the terminal

```

cd /home/YourUsername/freebasic/
sudo ./install.sh -i
	
#Download and install "getlibs-all.deb".
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb	

#Install libraries
sudo getlibs -p libxpm-dev
sudo getlibs -p libxrandr-dev
sudo getlibs -p libxrender-dev
sudo getlibs -p libncurses5-dev
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev

```

---

### Post by sisco311 on 2009-10-28
mono
[https://help.ubuntu.com/8.04/programming/C/other-programming-languages.html]("https://help.ubuntu.com/8.04/programming/C/other-programming-languages.html")

---

