---
title: "broken video drivers"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by jcats on 2009-11-01
This morning I  updated 8.10 to 9.04 through the update manager. The update went fine except that the best video resolution I could get was 1280X1024. I have a Dell E228wfpc (native resolution is 1680X1050).
So, like every other upgrade I have done, I fired up Envy, let it pick the ATI driver and install it. After it rebboted, I lost my desktop. 
The screen is divided in half, horizontally. The bottom half is all snow. The top half is black with 2 small Ubuntu's. (like the one that shows up on boot up). And I have no keyboard or mouse.
The system is dual boot, and the Windows side works fine.
So, I'm assuming that the video drivers are not compatible. But I have no idea on how to get the driver out. 
I have tried booting into the other versions, but it is always the same.
I could really use some help here. Anything would be appreciated.

jcats

---

### Post by Turtle.net on 2009-11-01
I don't know Envy, and I don't want to use something that install "stuff" that I don't understand.
So you just killed your video driver, no big deal.
Since you justinstalled you can reinstall to wipe out this faulty config or you can try to launch a recovery mode to access your system via command line.
then you can edit your xorg.conf to change manually the driver from the ATI one to the default one. Hopefully the xorg.conf was backed up and you still have the old version.
Anyway, go to the recovery mode, then log in (no graphics, no problem) and go to 
```
cd /etc/X11/
ls -l xorg.conf*
```
Let say you see a xorg.conf.backup or something similar with the same creation time as your xorg.conf (it should be the one before you change the driver.
You can check by looking into it
```
nano -w xorg.conf.backup
```
the driver should be different than the one in ```
nano -w xorg.conf
```
Since you want to use the later one you can do a ```
sudo cp xorg.conf.backup xorg.conf
```
and reboot.

Alternative : ```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
That should (no garanty) regenerate your xorg.conf with the default parameters.

After that use "Hardware Drivers" to install the suggested driver.

---

### Post by Mark Phelps on 2009-11-01
You told us only what Dell monitor you have.  

We need to know what video card/chip you're using -- because if it IS ATI, and it's not one of the newer HD 3x/4x/5x series, there are NO ATI video drivers that will work for your card and running Envy is only going to corrupt your display, forcing you to boot into a console to remove the ATI drivers and replace them with open source drivers.

---

### Post by jcats on 2009-11-01
Well, you are right. I'm using a Radeon 9800 Pro. So, how do I get into a console and remove the drivers? I can only get into the recovery mode. So, I'll need to remove it from there.
Thanks

---

### Post by Turtle.net on 2009-11-01
Have you tried the process I suggested ?
Can you post the result of```
cd /etc/X11/
ls -l xorg.conf* 
```

---

### Post by jcats on 2009-11-01
Yes, Mr. Turtle, I did try, but either I messed up or it didn't work.
On the other hand, I spent the last 4 hours digging around the web and trying things. I got it to work!

I found the solution at:
[www.logicalinsanity.net/?p=196](www.logicalinsanity.net/?p=196)

Thank you everyone for your time

---

