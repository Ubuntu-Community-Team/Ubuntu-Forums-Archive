---
title: "How do you change webcam drivers?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by complete n00b on 2008-12-30
I posted this a few days ago on the Multimedia board but nobody replied. It's probably a basic question so maybe it belongs here. I am trying to fix my upside-down webcam, which according to lsusb is

Bus 003 Device 002: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s

which is manufactured by SONIX. ASUS installs this webcam upside down so it is a common problem for people with this type of notebook.

When I do: udevinfo --query=all --name=/dev/video0 --attribute-walk

it tells me that the driver I am using is uvcvideo.

Arjos85 has made some patches to flip the camera for the uvcvideo driver but I haven't been able to get them to work. And apparently the stk11xx driver has a vflip option to put the camera the right way up, which uvcvideo doesn't have.

I want to switch my drivers from uvcvideo to stk11xx so I can use the vflip option. If you know how to switch webcam drivers please give me some instructions. I am completely new to Linux and don't know anything.

---

### Post by complete n00b on 2008-12-30
Please, can somebody help???

I am trying to follow these instructions (ignoring the French bits) for installing the stk11xx driver
[http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

however when I rmmod uvcvideo it gets rid of my /dev/video0, and so I can't put stk11xx in charge of /dev/video0!!

Can somebody explain how this all works? I don't have a clue!! I've googled high and low. I seriously need to fix this - my better half is demanding we put Windows back on just because of this stupid upside down webcam!

---

### Post by spiderbatdad on 2008-12-30
did you modprobe the new driver? after that you might need to add the name of the driver to /etc/modules...then try rebooting.

also don't forget the config sudo insmod stk11xx.ko vflip=1 brightness=0xBBBB

I dont see remove mod uvcvideo in those instructions...but I just sort of scanned it.

---

### Post by complete n00b on 2008-12-30
Thank you for replying. I deleted everything from my previous attempt at installing the syntek driver and did rmmod on the uvcvideo driver (which gets rid of the /dev/video0 directory. Now when I get to the sudo make -f Makefile driver step I get:

make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.

I googled this and it is something to do with the kernel source code and headers. I don't know what that means - I thought I had the kernel source code - now if I get it will it kill all my other drivers? I am extremely frustrated. There don't seem to be any clear instructions anywhere on the internet.

---

### Post by hansdown on 2008-12-30
Hi coplete nOOb.
Hopefully this will help...  [http://ubuntuforums.org/showthread.php?p=3437115](http://ubuntuforums.org/showthread.php?p=3437115)

---

### Post by complete n00b on 2008-12-30
Ok, I used google translate on the French, and I had overlooked one step, which explains the problem relating to headers and kernel source.

But now I'm back where I started, the problem is that my /dev/video0 disappears when I remove the uvcvideo driver. It seems that somebody else had the problem of the missing /dev/video0 on the board that hansdown just linked to.

On the French example, when testing the driver, it returns these lines:

stk11xx: Syntek USB2.0 Camera is ready
stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0

which I don't get, because my /dev/video0 is gone when I remove uvcvideo.

What exactly is the /dev/video0? should it exist independently of either driver? is the driver meant to create it when it is installed? do I need to put something into some module directory? I'm totally new to Linux and I find it all very complicated to be honest.

---

### Post by hansdown on 2008-12-31
Hi complete n00b.

Have you tried it with other programs like Cheese, camorama, and skype?  
You can get these in system> administration> synaptic package manager.
Do a search for these programs. Hope this helps.

---

### Post by complete n00b on 2008-12-31
Skype and aMSN work out of the box, nice image but upside down!

Camorama doesn't work and says cannot connect to camera device (/dev/video0)

Cheese just displays a colorful test-pattern sort of thing.

I only need Skype really. I know in the Windows version of Skype you can flip the camera image under options but not in the Linux version.

---

### Post by complete n00b on 2008-12-31
I found a package in Synaptic package manager called gspca-source, which is supposed to provide support for webcams manufactured by Sonix, like mine.
I installed it and followed the instructions, and it has failed quite predictably. The install screen says "bad luck, the kernel headers for the target kernel version could not be found". the kernel headers are right there in /lib/modules!!! Time to have a good scream I think.

---

### Post by hansdown on 2008-12-31
Stick with it complete n00b.

A solution may be near.

---

### Post by complete n00b on 2008-12-31
Holy moly, I actually got it working. I got so annoyed by trying to switch the drivers that I decided to go back to Arjos85's patch and give it another try. I had already thoroughly tried all the patches before, but this time I must have done something different, I don't know what it was, but after trying a million different fiddles I must have somehow fluked it. Great, now my wife won't bite my head off for deleting Windows!!

---

### Post by complete n00b on 2008-12-31
This is where the patches are by the way:

[http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210)

Anyone else who has the same upside down problem, I guess my experience is that even if they don't work at first, just keep at it, and you might just get lucky. Of course I'd still like to know how to switch drivers, just out of curiosity.

---

### Post by hansdown on 2008-12-31
Glad you worked it out complete n00b.

---

