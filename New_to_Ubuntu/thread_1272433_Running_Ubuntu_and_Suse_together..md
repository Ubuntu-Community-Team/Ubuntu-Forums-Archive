---
title: "Running Ubuntu and Suse together."
date: 2009-09-22
forum: New to Ubuntu
---

### Post by bvpainter on 2009-09-22
I have recently switched from Windows to Ubuntu which I like very much. I have a cd with Suse on,which I can run from the CD drive  to compare with Ubuntu. 

 Can I then load Suse to dual boot with Ubuntu, so I have a choice.. Can I load Suse from the CD,

I also have Kubuntu CD. If I load this from the CD do I have a choice of dual booting or will it run as a seperate choice of windows manager from my Ubuntu boot screen.
:confused:

---

### Post by louieb on 2009-09-22
> Can I then load Suse to dual boot with Ubuntu

Haven't used Suse but have multi booted up to half a dozen distributions. the only tricky part is getting GRUB let you choose which one to boot. And most of the time that is done automatically.     

> I also have Kubuntu CD. If I load this from the CD do I have a choice of dual booting or will it run as a seperate choice of windows manager from my Ubuntu boot screen

Either way. Use the CD to make Kubuntu a separate install and choose from the GRUB menu. Learn a little about GRUB and tripple boot Ubuntu, Kubuntu and Suse. 

 or in Ubuntu install  kubuntu-desktop and choose from the logon screen.

---

### Post by ajgreeny on 2009-09-22
You can certainly run suse and ubuntu together, or any other distro you want, but whatever you do, make sure you have a separate home for each distro, and don't try to share between both.  You can always have a partition for data which is mounted at boot time using /etc/fstab in both distros, but a shared /home partition will cause all sorts of problems with the configuration folders and files for each distro.  There are a number of ways round this involving tha same /home partition and different usernames etc but come back again if you want to look into that possibility.

For kubuntu, the same situation is possible, ie you can run as separate distros, but you can also in this case, use apt-get or synaptic or Add/Remove to install kubuntu-desktop to your existing ubuntu installation, and then choose kubuntu or ubuntu from the login screen.  In that way you will not need to bother with sharing home, as they will both be on the same OS already.  If your kubuntu CD is an alternate install version you can even add that to your sources.list file and get the desktop files from that, saving download bandwidth.  If it's a live CD, I don't think that is possible, unfortunately.

---

### Post by Zeedok on 2009-09-22
> **bvpainter said:**
> I have recently switched from Windows to Ubuntu which I like very much. I have a cd with Suse on,which I can run from the CD drive  to compare with Ubuntu. 

 Can I then load Suse to dual boot with Ubuntu, so I have a choice.. Can I load Suse from the CD,

I also have Kubuntu CD. If I load this from the CD do I have a choice of dual booting or will it run as a seperate choice of windows manager from my Ubuntu boot screen.
:confused:

You can install Suse (and as many operating systems as you like) to your hard drive as well - just do a manual partition and carve out some space for your new distro.  Bare in mind though, the more distros you have, the less room you will have on your hard drive.

Also, if you what to try Kubuntu (which is basically Ubuntu with the KDE desktop instead of Gnome), you don't need to reinstall the whole OS.  Just install kubuntu-desktop from Synaptic.

---

### Post by farsight on 2009-09-22
Hi,

If you'd like to run all three then maybe you'd like to give virtualbox a blast. It can be downloaded through synaptics package manage and has allowed me to run Windows and Opensuse within Ubuntu. All you have to do to swap back to Ubuntu is hit the hot key.

I found for simple uses, e.g. work processing, Windows ran absolutely fine by me.

Just adding another feather to your bow :)

Farsight

---

### Post by LewRockwell on 2009-09-22
you'd be doing something similar to:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

or

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

we have found one partition per operating system works fine(no separate home or other partitions)

these hard drives have been cloned for back-up protection

all valuable data is securely stored via clone and/or long-term storage media(CD/DVD typically)

.

---

### Post by Darkwing-Duck on 2009-09-23
Another way to compile all of the OS' together and get the MBR to view all of them with a choice.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

