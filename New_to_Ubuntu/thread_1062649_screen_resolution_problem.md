---
title: "screen resolution problem"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Ross Martin on 2009-02-07
I am new and have never used, I am having problems with my screen resolution after installing my driver for the graphics card, when I change the resolution through the software it works fine. But after starting the computer again after shutdown or restart is reverts back to 800 x 600 how can I save it so that I do not have to reset it every time to a higher resolution. I am using a nvidia geforce 2 mx400 card the computer is about 10 years old.

---

### Post by konqueror7 on 2009-02-07
you could try replacing you driver using [Envy]("http://albertomilone.com/nvidia_scripts1.html"), this what i use installing my nvidia driver...or you could try edit you xorg.conf...

---

### Post by theinnercityhippy on 2009-02-07
Hello. I note you said you're a complete beginner so I'm going to try and talk you through a few steps so that we can try and diagnose the problem.

First things first, we need to open a terminal (command line) as this is by far the quickest way to get the information we need. Don't worry about this, we are just using it to print some information to the screen at this point so there is no danger in you causing any further problems at this stage. Linux is set up in such a way that you will be unable to change any system settings unless you give the command the privilege to do so so by entering your password, hence it is more secure than many other operating systems.

So, to open the terminal, go to 

Applications > Accessories > Terminal

then we need to enter a few commands to get some information that I would like you to post here so that we can help you further.

First, in the terminal please type the following command

```
gedit /etc/X11/xorg.conf
```

Gedit is a simple text editor that is included as standard with Ubuntu. If you select everything in this file, either by pressing CTRL+A or with the mouse, then copy it by pressing CTRL+C or going to the menu option. Then paste the contents as a reply to this thread.

Don't worry if you accidentally change or delete something in this file at this point, as you have not given it superuser privileges with your password, it will not let you save the modified version.

Then, could you possibly do the same with the following command immediately after a reboot

```
dmesg
```
This command basically tells you what the kernel is doing at any point, including error messages (in a basic sense). Therefore, if there is any problems with the graphics driver, this should tell us.

Will rty my best to give you a quick reply if I can but entertaining my gf's 6 year old today which is a mammoth task :-)

-JimDog*-

---

### Post by Ross Martin on 2009-02-07
Thanks for the help I am at work at the moment and will have to try this when i get home, i spend my whole day sorting pc's running xp and server 2003 using dos and am do not have a clue about linux/ubuntu at all so that info is a great help.

---

### Post by Ross Martin on 2009-02-07
I am at home now and have put in the code and all that I get is a blank text screen with no info.

---

