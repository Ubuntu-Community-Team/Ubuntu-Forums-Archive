---
title: "How to remove ubuntu"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by odear on 2009-06-22
I used the wubi installer to install ubuntu from windows.
I used ubuntu for several days  but decided to remove it again.
So I went in XP mode and uninstalled wubi with the windows uninstallers menu
Back I days this worked for me(also when removing ubuntu) after I did that I deleted the linux files from my hd
but now when i try to boot my system it first brings me in a dual boot menu (XP and Ubuntu)
When I try to start ubuntu my system just reboots
how can I delete ubuntu from the dual boot system menu without using the XP installation cd ?

---

### Post by zeroseven0183 on 2009-06-22
Hi!

After you installed Ubuntu inside Windows, it creates another entry in the boot.ini file. The original boot.ini file should contain only this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Just edit the boot.ini (using Notepad) in C:\ when you go to Windows.

---

### Post by caravel on 2009-06-22
I'm not familiar with Wubu but I don't think it installs grub.  Post up the contents of your boot.ini file as it's likely that the boot entries are there.

---

### Post by 3rdalbum on 2009-06-22
> **caravel said:**
> I'm not familiar with Wubu but I don't think it installs grub.

It does, but it uses the Microsoft bootloader to call GRUB and GRUB will boot Ubuntu.

The first two posters have given you the correct answer.

---

### Post by presence1960 on 2009-06-22
in XP go Control Panel > System, click on Advanced tab and go to Startup & Recovery options. Click the edit button and it will bring up in notepad your boot .ini file. Remove the reference to ubuntu and you'll be good to go.

---

### Post by caravel on 2009-06-22
> **3rdalbum said:**
> It does, but it uses the Microsoft bootloader to call GRUB and GRUB will boot Ubuntu.
I see, so grub is installed but not in the mbr.  That clarifies it.

So why doesn't the uninstall restore the boot.ini back to it's default configuration?

---

### Post by Mark Phelps on 2009-06-23
> **caravel said:**
> So why doesn't the uninstall restore the boot.ini back to it's default configuration?

Good question.  You'd think that when it installed itself, it would have made a copy of the boot.ini file and restored that when it uninstalled, but apparently it does not.

However, the Wubi guide link below clearly shows that you're supposed to do the edit manually:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?")

---

### Post by ajkenney on 2009-06-28
I'm in a similar situation, I'm selling my netbook to get a better one but my friend who's buying it wants me to remove Ubuntu first.  It's a dual boot with Ubuntu on a second partition.  Here are my questions:

1.  Can I still remove it the same as above?  

2.  After removed, will I be able to increase the Windows partition size to fill the void left by the removal of Ubuntu?

Thanks! I appreciate all the help I can get!

And don't worry, the first thing I'm doing with my new netbook is, you guessed it, installing Ubuntu. :D

Cheers,

Andy

---

### Post by 3rdalbum on 2009-06-28
> **ajkenney said:**
> I'm in a similar situation, I'm selling my netbook to get a better one but my friend who's buying it wants me to remove Ubuntu first.  It's a dual boot with Ubuntu on a second partition.  Here are my questions:

1.  Can I still remove it the same as above?  

No - Wubi installs Ubuntu into a file, and registers it with Windows' package manager so Windows can remove it.

There are quite a few HOWTOs around about how to remove Ubuntu from a dual-boot situation. I haven't done this before so I can't really advise. They should also go through resizing the Ubuntu partition to nothing.[/QUOTE]

---

