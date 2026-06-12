---
title: "switching"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-17
ok, i used commands to upgrade from ubuntu desktop  to laptop remix.  after rebotting the remix screwed my computer up.  how can i go back.

---

### Post by HermanAB on 2009-05-17
Hmm, you cannot unscramble an egg.  Re-install from scratch - sorry.

---

### Post by Leshinsky on 2009-05-17
So i will lose all my data right

---

### Post by matrixblue on 2009-05-17
I assume you meant netbook remix. What exactly is screwed up? If you can access a terminal then you can backup your data before the re-install.

---

### Post by blackened on 2009-05-17
Did you do a dist-upgrade or did you simply add the netbook remix packages? If it's the latter, then you could start by trying to remove the netbook stuff.

What exactly is the problem though. Does the machine boot to any sort of interface that takes user input, be it graphical or text?

---

### Post by Leshinsky on 2009-05-17
ok here is what it is doing.  when i get to ubuntu it takes away my desktop for some weird windows 3.11 type program.  which i hate.  my windows dont open right.  like their totally invisable unless i move my mouse over them.  sometimes they dont open at all.  the tool bar on top likes to disappear and my system runs very very slow.  i had ubuntu and wanted to upgrade to the notebook remix because someone said i could use my wireless card (built in) on it.  the commands i used were to install the notebook package then deleate the ubuntu desktop (i can not find that post.)  
More FYI
i went into the package mgr and then (checked for reinstallation) the ubuntu desktop and (checked for total removal ) the remix package.  but it did nothing.  the ubuntu desktop was already installed even tough that command should of knocked it out.  

I found the codes that i used.   they are on the bottom.  if anyone could help me it would be great.    i dont see why i should have to wipe my drive then redo it.  why i cant just do something like this to get ubuntu desktop back. i would even settle for ubuntu server (thats what this computer will become in a month.  as long as i get my desk top back and it dont screw up the windows and i dont have to back up my files.  so let me know.

sudo aptitude install ubuntu-netbook-remix

and then,

sudo aptitude remove ubuntu-desktop

---

### Post by matrixblue on 2009-05-17
If you still get to the login window, try changing the session that you log into

---

### Post by goldblattster on 2009-05-17
You should be able to access the command line interface (Ctrl+Option+F1)

---

### Post by bonkadventure2 on 2009-05-17
I'm not very familiar with Netbook Remix, but here are suggestions.
If you have any other sessions available(KDE, XFCE, etc;), than go into those to try fixing your problem, or remove the Netbook Remix Packages from a terminal. :D

---

### Post by Leshinsky on 2009-05-17
I can get to the system log in screen but im not sure it gives me a choice what system to log into.  Does anyone know the command line commands to uninstall the package for netbook remix since it wont uninstall in package mgr. :popcorn:

---

### Post by matrixblue on 2009-05-17
Do the following:

sudo apt-get remove ubuntu-netbook-remix

sudo apt-get install ubuntu-desktop

---

### Post by Leshinsky on 2009-05-17
When i do that command line it says netbook remix not installed so it could not be removed.  but i still dont have my desktop.  also now when i boot up or shut down it says ubuntu studio instead of ubuntu.

---

### Post by matrixblue on 2009-05-17
Do you get to the Login screen? If so look for available sessions. Also try

sudo apt-get install gnome-desktop-environment 

and

sudo dpkg-reconfigure xserver-xorg

---

### Post by Leshinsky on 2009-05-17
Ok,  that did not work.  i have attached 2 screen shots.  one is of firefox to show you how my three buttons on the right of the program (close maximise and min.) are missing.  the second is a program that fits over the desktop not letting me into my desktop.  it has like places on the right.  quit on the right hand bottom and my program catagories on the left with a space in the center for the icons for that program group in the middle.  i want my buttons back and that black thing to go away.  can anyone help me do this.  Or would i just need to upgrade to server.  let me know.

---

### Post by gashcr on 2009-05-18
ok, I see, you need to:

apt-get remove maximus netbook-launcher go-home-applet human-netbook-theme window-picker-applet

that should restore the normal look and feel of your desktop.

---

### Post by Leshinsky on 2009-05-18
Hey guys just wanted to say that the last one worked.  Thanks for everyones help.  But mostly the last guys whos idea made it work.  I have more questions but i will start a new thingie.

---

### Post by bobbob1016 on 2009-05-18
Just so you know, the black thing you said you had was the netbook remix thing.  It's supposed to bring everything into one menu to make it easier to get to.

Edit:  Mark as [Solved]

---

