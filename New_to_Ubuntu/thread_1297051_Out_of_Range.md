---
title: "Out of Range"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Alan1 on 2009-10-21
I know there have been several posts already on this topic but I can't seem to find an answer that works for me.
 
I am new to Linux and this is my first attempt at installing Ubuntu.  I currently run XP, my graphics card is a radeon X300 and I have a plug&play TFT monitor.
 
I have attempted to do the demo install from the CD but after a short while the screen goes blank and I get an 'Out of Range' error message.
 
Ctrl+Alt+F1 gets me to the Ubuntu command line but from there I'm completely stuck.  
 
Can anyone offer a step by step guide to resolve this issue?

---

### Post by QIII on 2009-10-21
Does Ubuntu work in a live session from the LiveCD?

Could you post the entire text of the error message?

(I hope this doesn't double post.  It didn't seem to appear the first time!)

---

### Post by LowSky on 2009-10-21
the issue is your graphics card. ATI doesn't release drives for card older than their HD2000 Line, but the community should still offer some support.

I know what I'm telling you make little sense but hopefully someone has dealt with this before

Can you please give us a bit more information about your PC.

Or try using Ubuntu Version 8.04 as it should offer your computer better support, as the that release offers an older driver that supports your graphics card.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Click on the options for 8.04

---

### Post by ikisham on 2009-10-21
In another distro I tried once, it would give that message (because the distro wasn't much good in configuring the video) so to make it boot ok one has to add ```
xres=1024x768
```(or any other resolution that's best for your monitor) to GRUB's boot line.

**If you're running only the demo (live-cd):**

I'll have to see where to put that cheatcode...look at the options you have at the bottom of the screen (F4, F6 etc.). The one that shows 'boot' and where you can type an extra code is where you type xres=1024x768

**If it's installed:**

So when GRUB's menu appears, highlight Ubuntu's entry then press **e** to edit, go to the kernel line and add that xres=... posted above. Then press **b** to boot.

If it works, then you can edit GRUB's menu.lst ```
sudo gedit /boot/grub/menu.lst
```and add the cheatcode to the proper place or even edit xorg.conf file (but that's after you installed, so if you still have trouble, just ask).

---

### Post by Niko Johnson on 2009-10-21
what kind of graphics card are you useing... i had the same error but it ended up being an easy fix

---

### Post by QIII on 2009-10-21
> **LowSky said:**
> the issue is your graphics card. ATI doesn't release drives for card older than their HD2000 Line, but the community should still offer some support.

I know what I'm telling you make little sense but hopefully someone has dealt with this before

Can you please give us a bit more information about your PC.

Or try using Ubuntu Version 8.04 as it should offer your computer better support, as the that release offers an older driver that supports your graphics card.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Click on the options for 8.04

I'm wondering if an open-source alternative is already included and might be working already if he is able to use a live session with the LiveCD.

If he can, I think the solution should be fairly simple...  Maybe using the Alternate install and then using the open-source driver?

That worked for me on an old machine with an unsupported nVidia card.

But yes, I concur.  8.04 LTS may be the way to go for now.

---

### Post by Alan1 on 2009-10-22
Hello everyone and thanks for the replies.  It is 8.04 LTS that I have downloaded and am having the problems with.
 
From the CD I have chosen the 1st option which is the Demo and Full Installation.  Unfortunately, on reboot, the montior goes blank soon after the progress bar has finished and just displays the message 'Out of Range'.
 
To answer a couple of the questions that came with the replies:
 
I am using an ATI Radeon X300 graphics card and the spec for my PC is an IBM ThinkCentre with Pentium Dual Core 3.2GHz CPUs and 512MB of RAM.
 
Please remember that I am a complete beginner when it comes to Ubuntu and Linux.

---

