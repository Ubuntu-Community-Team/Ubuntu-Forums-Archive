---
title: "Fatal Error during installation of 10.10"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by nerwintheodd on 2010-12-21
Hello, so I've decided to switch from ubuntu after Windows crashed hard on my laptop for the umpteenth time. It had gotten to the point where boot.ini was corrupted beyond recognition, and lacking a Windows restore disk, I figured tonight was as good a time as any to make the switch. 
**TL;DR Laptop crashes, I decide to instead boot/install ubuntu 10.10**
 
So, I'm booting from the 10.10 32 disk I made, and right after it's done wiping the hard drive, it starts installing. During the installation process, it fatals and says it can't write to the boot partition(I sadly futzed with it after I got the message, and I can't remember exactly what the message said.) I tried restarting the computer and start from square one, but now when it attempts to boot, it just crashes as it loads with the message:
 
**(process:318) GLib-WARNING **: getpwuid_r():failed due to unkown user id(0)**
**udevd[72]: worker [83] unexpectedly returned with status 0x0100**
**udevd[72]: worker [83] failed while handling '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda**
 
Basically, what I can in my feeble mind assume happened is that the computer is working under the assumption the ubuntu installed correctly and completely, even though it didnt.
 
I am completely new to this, so if anyone can lend a hand I'd be more than appreciative.

---

### Post by unplugged23 on 2010-12-21
If I understand correctly that your primary problem is not being able to write to the boot partition, you may want to go grab a live distro like g-parted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) wipe all of the drive partitions, then create all of your new partitions from scratch in the ubuntu installation process. Hopefully this is what your looking for, if not let us know!

Best of luck!

---

### Post by nerwintheodd on 2010-12-21
Thanks for the reply!
I take it this piece of software can be put on a disk and will just erase any trace of ubuntu so I can start the installation process fresh?

---

### Post by PhantmKllr on 2010-12-21
> **unplugged23 said:**
> If I understand correctly that your primary problem is not being able to write to the boot partition, you may want to go grab a live distro like g-parted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) wipe all of the drive partitions, then create all of your new partitions from scratch in the ubuntu installation process. Hopefully this is what your looking for, if not let us know!


If I am not mistaken, GParted comes with the Ubuntu live CD.

---

### Post by nerwintheodd on 2010-12-21
Will I be able to boot from the gparted CD?
*EDIT* Answered my own question, nevermind.

---

### Post by PhantmKllr on 2010-12-21
> **PhantmKllr said:**
> If I am not mistaken, GParted comes with the Ubuntu live CD.

When you boot from the Ubuntu CD, click "Try Ubuntu" when the first window comes up. Then Gparted should be under the applications menu..."

---

### Post by nerwintheodd on 2010-12-21
Ok, so what the problem is, is that I can't even get to that screen anymore.
I try to boot, and it just sticks at the "unbuntu . . . ." screen for at least an hour.
The only thing it responds to is the "F8" key, and it gives me that message.

---

### Post by PhantmKllr on 2010-12-21
Oh, OK, I get it now. It sounds like your Ubuntu CD might be bad. Try re-downloading the live cd image and burn it at the **lowest** speed.

---

### Post by nerwintheodd on 2010-12-21
I've done that, the first CD I used looked a little dubious. The second CD still doesn't work.
 
Is there any way I can clear the existing and messed up first attempt to install from my hard drive so I can start from square one, with no OS?
*EDIT TO CLARIFY* because the computer won't let me do anything until I do.

---

### Post by PhantmKllr on 2010-12-21
The fact that you can't boot from the CD, indicates that there's a physical problem with your computer. Most likely your CD/DVD drive.

---

### Post by unplugged23 on 2010-12-21
I would suggest using unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to create a bootable image of the cd on a flashdrive and then try booting from that.

---

### Post by theasprint on 2010-12-21
Hi,

I actually suspect that there's something wrong with your .iso file.

To check your .iso to see if all the things are correct, go and check your MD5 sum.

Here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This would ensure that your .iso file is at its best.

---

### Post by nerwintheodd on 2010-12-21
Alright, so I get that the iso was corrupt on my first attempt to install.
What I NEED to do is remove said corrupted install. Does anyone have any ideas how to do this? I can't access any ubuntu features.
 
Basically, the question I pose to you, is, is there any bootable media you would recommend that would just clear any prior installation of any OS from my hard drive?

---

### Post by theasprint on 2010-12-21
Hi,

Er if you installed a corrupt install, we would like to know how is your install like. (its vague)

Basically its not about clearing the OS anymore, this is because I fear that the uninstallation would also fail badly.

So what I suggest is a reformat of the HDD.
So can I know the structure of your HDD (The different OSes etc)

To give a clear view, can you kindly get a good .iso file and burn it and boot from LiveCD (that means try ubuntu without installation), then go to the boot info script below @ my signature and post the results (results.txt) here.

---

### Post by PhantmKllr on 2010-12-21
> **theasprint said:**
> Basically its not about clearing the OS anymore, this is because I fear that the uninstallation would also fail badly.

Agreed

---

