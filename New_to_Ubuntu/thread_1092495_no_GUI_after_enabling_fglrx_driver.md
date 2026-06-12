---
title: "no GUI after enabling fglrx driver"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Zogh on 2009-03-10
Hello!

I downloaded Ubuntu Intrepid 8.10, 
made a guided dual boot install, 
clicked the update manager, 
let it update everything, 
rebooted.

So far so good.
Now I wanted to install the ATI proprietary drivers (since several posts have suggested that they give better 3-d acceleration etc).

I went System > Administration > Hardware Drivers, 
enabled the driver (fglrx), 
rebooted when it was done.

When linux is finished loading it leaves me at the command prompt (or is it called the bash shell?"  I have no GUI, only the shell.

I have left the computer untouched since i dont want to introduce any unknown variables. It's a clean install + 1 automatic update + 1 click at Hardware Drivers>enable

I only have a few hours experience with linux so take that into consideration when answering. I am not sure what info i need to provide to help you help me so i'll begin with info about my system.

I run a 32 bit version of intrepid. The grub prompt says "ubuntu 8.10, kernel 2.6.27-11-generic after the update manager was done.

MB: MSI K9A2 platinum, RAM: 4GB, CPU:AMD Phenom 9750, Graphic cards:2x ATI HD 3850 (separate cards), Monitors: BenQ 19" and NEC 15". HD0: 300GB containing XP and Ubuntu.

Please help me with restoring my GUI and updating my ati drivers so that they are good enough for some serious gaming as well. 

/Z

---

### Post by Nxion on 2009-03-10
Hi,

So does it even go to the login window at all? What is the last screen you see BEFORE you get just a command prompt?

---

### Post by Zogh on 2009-03-10
No, I never get to see the login window.

First i get the ubuntu startup logo and the load-meter or whatever we want to call it, then i get several rows of boot up text and i get thrown out to the prompt.

---

### Post by Junkieman on 2009-03-10
After logging into the terminal, try resetting your xserver config as [described here]("http://ubuntuforums.org/showthread.php?t=749966").

---

### Post by Zogh on 2009-03-10
What exactly is it that i need to do?

I ran:
sudo dpkg-reconfigure xserver-xorg

The only thing that allowed me to configure was the keyboard.
I rebooted. the problem remained.

then i typed: sudo nano /etc/X11/xorg.conf
and then: sudo dpkg-reconfigure -phigh xserver-xorg
(because it was mentioned in the xorg.conf file)

no change. I still only have a command prompt.

my xorg.conf now contains:

Section "Device"
         Identifier    "configured Video Device"
         Driver        "vesa"
EndSection

Section "Monitor"
        Identifier     "configured Monitor"
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Monitor        "configured Monitor"
        Device         "configured video Device"
EndSection


If I need to edit anything I dont know what I need to change. Please assume that I'm a complete beginner with Linux. 
Pointing me to a thread that says "edit this and this file.." without actually telling me what needs to be edited is yet above my capacity. ;) Or did i just miss something?

---

### Post by Zogh on 2009-03-10
Also,

After updating Ubuntu i got 2 new boot options in grub:
Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)

The 2 on top are new, I only had the two 2.6.27-7-generic options
(omitting memtest and windows choices)
I have tried booting with both ver 2.6.27-11 and 2.6.27-7 to no avail.
I tried the 2.6.27-11-generic (recovery mode) with the xfix option and it didn't work. (still at command prompt)

Do i need to provide more information and in that case, what would that be? I'm not going to try fixing this aimlessly since it will be easier for myself and those helping me if I/they know what's been done with the system.

btw, will those 4 boot options always be there? What's the difference between them? Do i need to delete the old boot options?

---

### Post by Nxion on 2009-03-10
> **Zogh said:**
> What exactly is it that i need to do?

I ran:
sudo dpkg-reconfigure xserver-xorg

The only thing that allowed me to configure was the keyboard.
I rebooted. the problem remained.

then i typed: sudo nano /etc/X11/xorg.conf
and then: sudo dpkg-reconfigure -phigh xserver-xorg
(because it was mentioned in the xorg.conf file)

no change. I still only have a command prompt.

my xorg.conf now contains:

Section "Device"
         Identifier    "configured Video Device"
         Driver        "vesa"
EndSection

Section "Monitor"
        Identifier     "configured Monitor"
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Monitor        "configured Monitor"
        Device         "configured video Device"
EndSection


If I need to edit anything I dont know what I need to change. Please assume that I'm a complete beginner with Linux. 
Pointing me to a thread that says "edit this and this file.." without actually telling me what needs to be edited is yet above my capacity. ;) Or did i just miss something?

Well there it is! The driver you are using is vesa. what it actually should read is fglrx.

So open a terminal and type this:

```
sudo nano /etc/X11/xorg.conf
```

Change "vesa" to "fglrx". Then CTRL + X to exit, hit Y to save it and reboot. Your machine should be back to normal now.

---

### Post by Zogh on 2009-03-10
Thank you for your kind help. I did what you suggested, unfortunately the problem still remain the same. :-k

I managed to find a earlier backup that contains the following:
_____________
Section      "Monitor"
             Identifier        "Configured Monitor"
EndSection


Section      "Screen"
             Identifier        "Default Screen"
             Monitor           "Configured Monitor
             Device            "Configured Video Device"
             DefaultDepth      24
EndSection


Section      "Module"
             Load             "glx"
EndSection


Section      "Device
             Identifier        "Configured Video Device"
             Driver  "fglrx"
EndSection
_______________

I guess that's how xorg.conf looked like from the start, before i followed the advice the advice mentioned in the thread that was pasted.

Do this tell you anything? 
Is there other log files that might give us a better understanding of why the gui is not loaded?

I really apreciate the help btw.


(edited typo)
/Z

---

### Post by Zogh on 2009-03-10
I tried with replacing my xorg.conf with the backup mentioned in my last post and did a reboot with the new xorg.conf , It was unsuccessful.

I found another post on this forum: [http://ubuntuforums.org/showthread.php?t=1088760]("http://ubuntuforums.org/showthread.php?t=1088760")

after reading throuh it i tried:
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx

It rendered this result:
____________________
Module Loader present
Markers: (--) probed, (**) frp, config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI)not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log
(==) Using config file: "/etc/X11/xorg.config"
(EE) No devices detected.

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno111): unable to connect to X server
xinit: No such process (errno 3): Server error.
_________________


I have no screens?? :D

---

### Post by kansasnoob on 2009-03-10
Distrowatch recently posted this message:

> Since being bought by AMD in 2006, we were promised improved Linux drivers for ATI video cards. Recently AMD released a second batch of information on their hardware to the open source community, which helps to feed into the radeonhd driver, but their closed source proprietary driver still remains, well, closed. The driver has always been second rate, but now it has gotten to the point that Arch Linux developers have decided to dump it all together. Developer Eduardo Romero writes: "The ATI Catalyst drivers are in a pitiful state and AMD is doing close to nothing to improve the situation, they just take Linux as a joke. At least, that is the impression one gets when NVIDIA releases great drivers for Linux." He and Andreas Radke have decided to drop the driver out of the supported package trees and have pushed it back onto the community to maintain. They are instead going to concentrate on the free and open source radeonhd driver: "The radeonhd driver, which is in extra, shows some promise." After many years, the battle for open source graphics drivers is still ongoing.

More here:

[http://www.archlinux.org/pipermail/arch-dev-public/2009-February/010394.html](http://www.archlinux.org/pipermail/arch-dev-public/2009-February/010394.html)

Now, maybe Ubuntu has a better way of working thru this, I don't know, but basically ATI and AMD are on the verge of becoming the equivalent of Lexmark to Linux!

---

### Post by Zogh on 2009-03-10
I read and wept..

then re-read: [http://linuxtipsandtricks.com/ubuntu/ubuntu-ibex-810-with-ati-radeon-hd-2400-xt/]("http://linuxtipsandtricks.com/ubuntu/ubuntu-ibex-810-with-ati-radeon-hd-2400-xt/")
[http://ubuntuforums.org/showthread.php?t=1088760]("http://ubuntuforums.org/showthread.php?t=1088760")
and tried a different combination of commands.

At least I've finally got my GUI back.

sudo apt-get remove xorg-driver-fglrx fglrx-kernel-source

sudo dpkg-reconfigure -phigh xserver-xorg

..then rebooted.

SUCCESS!
I now have a GUI but probably no 3D acceleration at all since it's now set up to use vesa drivers.

Problem 1 in the thread is now solved.

So to my last problem: How DO i update my ati drivers to make them good enough for gaming?

(edited grammatic incompetence)

---

### Post by Nxion on 2009-03-11
I found this, maybe it is what you need:
[URL="http://www.phoronix.com/scan.php?page=article&item=842&num=1"]
http://www.phoronix.com/scan.php?page=article&item=842&num=1[/URL]

(I know it says Hardy but it should work fine)
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#RadeonHD_driver_.28ATI_only.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#RadeonHD_driver_.28ATI_only.29)

---

### Post by JohnFH on 2009-03-11
I might get shot down for saying this, but I'm speaking from experience and also a lot of research.  

I built myself a media centre using MythTV, but stupidly bought a motherboard with integrated ATI graphics to run it.  I struggled for ages to get the graphics to work and for a while it did until I got fed up with the system crashing every time I changed channel!  I tried upgrading to Intrepid and still had the same trouble trying to install the proprietory ATI drivers, so gave up and bought a cheap NVidia card and now the graphics work smoothly with much less configuration and no crashing!  I paid £15 for an NVidia 7300 card on eBay and I should have done that ages ago.  You may need to spend a bit more if you want a decent graphics card for gaming, but if possible, make the switch to NVidia now instead of wasting time with ATI nonsense drivers.  The ATI cards are good but their Linux drivers are buggy and a pain to setup.

---

### Post by Zogh on 2009-03-12
Thank you for the advice, I will check out the HD drivers since my GUI dissapear everytime i install the fglx driver. 

So are the HD drivers found in the link the best alternative to the fglx driver or are there even better alternatives out there?

Dont worry, I wont come and shoot you for suggesting a switch to Nvidia ;) However, bying a different graphics card is not a alternative. I have 2 3850 in a crossfire configuration and I dont feel very inclined to buy a brand new sli configuration just to be able to run ubuntu, especially since there's no guarantee that my gaming will work anyways. I really prefer Ubuntu but if I can't get my graphics to work I will have to switch back to Windows anyway for this simple reason: I've had no problems with it so far.

---

