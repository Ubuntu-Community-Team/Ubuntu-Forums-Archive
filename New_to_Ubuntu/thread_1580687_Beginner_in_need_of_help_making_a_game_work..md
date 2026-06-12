---
title: "Beginner in need of help making a game work."
date: 2010-09-23
forum: New to Ubuntu
---

### Post by daxbriggs on 2010-09-23
Hello, and thanks for looking.

I'm completely new to Linux in general.  My friend installed Xubuntu on my computer awhile ago.  I have a patched version of Fallout 1 by Interplay. 

I really like this game, and would love to know how to make it work.

Like I said, I'm completely new to Linux.  I know how to use Windows, and could install it on my old OS.  Windows XP.

But now I'm running Xubuntu, and I really have no idea how it works.

I'm pretty much useless, and I'm tired of asking my friend for help. (Plus, he sleeps all day)

So, time for me to figure it out for myself.

But really, like I don't know anything about Linux.  I know how to open a terminal, and navigate the GUI.  But the only command I know for the terminal is XKILL.  So, starting from scratch.  How do I install this game??

Thank you in advance for your help.  Anything is appreciated.

---

### Post by Lateralis on 2010-09-23
Hi there!  Welcome to Ubuntu and the Ubuntu forums! 

In order to get Windows games to work in Linux you need to use emulation software.  This software emulates a Windows environment, in order to trick the software into running.  Ubuntu comes with such software, known as Wine (**Win**dows **E**mulator).  It is far from foolproof and doesn't work with all Windows applications.  It is, however, still a very useful tool.

[The WineHQ App Database]("http://appdb.winehq.org/") seems to suggest that [Fallout 1]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=43") will work fine in Wine.  To install it in Wine is relatively straightforward.  If you have the installation CD then put in the CD drive and locate the setup executable; will probably be setup.exe or something similar.  Right click on it and chose "Open in Wine".  Wine will then attempt to run the CD.  All being well you should see the installation screen, just as you would in Windows.  

Once the program is installed you should be able to find it in the Applications -> Wine -> Programs menu.

---

### Post by daxbriggs on 2010-09-23
Thank you very much.  I will try this out, and post back if I have any problems.

Appreciate your help!

---

### Post by daxbriggs on 2010-09-24
Hello, a little more help needed.

The Fallout that I have is a .ISO (so, a cd image, as I'm sure you know)

I've figured out how to mount it using Gmount-iso which I downloaded from the Ubuntu Software Centre. 

I created home/daxus/temp as the directory to mount images to.

The first problem I have is when I click mount, after specifying the image to mount, and where to mount it.   Gmount says 

" An error occurred
Murrine configuration option "scrollbar_color" is no longer supported and will be ignored"

Than I click close, and the image is mounted in daxus/temp anyways.

So, I go to the image, there are 3 files I tried running with wine.  the setup.exe didn't do anything.  a terminal opened, than immediately closed.  the install.exe didn't do anything, either.  (to open both these I just right clicked and chose 'open with wine')

But the autorun.exe opens the games autorun menu, but when I click "Install"

well, it says; 

"Sorry, this version of Windows is not supported with this product."

I lol'd. 

And that's all. 

I'm stuck... :(

---

