---
title: "Is there HDD Health check application for ubuntu"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by nakama85 on 2009-11-08
I would like to test the health of my HDDs. Is there an application that someone recommends?

---

### Post by Tyke91 on 2009-11-08
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

note: it's run every 30-something mounts on ubuntu anyway. so you shouldn't really need to worry about it. 

NEVER RUN FSCK ON A MOUNTED HARD DRIVE. EVER. if you really want to use fsck to check your hard drive, boot into a live cd or into the read only recovery shell (via grub) and run it from there.

---

### Post by braete on 2009-11-08
maybe this is what u are looking for: in system/administration try disk utility, click on ur hdd and then click more information and do a test (i only did the short one do see what it does :lolflag:) ...

---

### Post by Paqman on 2009-11-08
> **nakama85 said:**
> I would like to test the health of my HDDs. Is there an application that someone recommends?

If you're running Karmic, there's now a hard disk utility in the default install that, among other things, can give you a full run down of the SMART health status of your disks. It monitors them continuously, and will spit out warnings if they're starting to fail.

---

### Post by phillw on 2009-11-08
> **Tyke91 said:**
> [http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

note: it's run every 30-something mounts on ubuntu anyway. so you shouldn't really need to worry about it. 

NEVER RUN FSCK ON A MOUNTED HARD DRIVE. EVER. if you really want to use fsck to check your hard drive, boot into a live cd or into the read only recovery shell (via grub) and run it from there.


+1 on the mounted issue, I forced an fsck on mine -- took it 4 goes to recover what I messed up by the disk being mounted.

Phill.

---

### Post by gdonwallace on 2009-11-08
Tyke91 is correct, although nothing happened this time, I speak from experience when I say don't run FSCK on a mounted hard drive.  I had to completely wipe my hard drive and re-install Ubuntu.  It totally hosed my Master Boot Record so that Ubuntu would not boot up properly.

---

### Post by Paqman on 2009-11-08
Runnning fsck won't actually tell you the health of your drives though. It just deals with the filesystem, which isn't quite the same thing (although a failing drive will most likely mess with the filesystem)

What you want is the [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") data.

---

### Post by Tyke91 on 2009-11-08
> **Paqman said:**
> Runnning fsck won't actually tell you the health of your drives though. It just deals with the filesystem, which isn't quite the same thing (although a failing drive will most likely mess with the filesystem)

What you want is the [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") data.

ah. you are right...

I just assume the hard drive is allright until fsck starts being unable to fix things ^_^ I keep backups of all of my important stuff, so getting another hard drive is not really an issue, though I've only had to replace a hard drive once (was the first time I messed around with a source based distro... apparently hard drives don't like being formatted and then used to compile an OS 7 times in a day without proper cooling :p. Oh well... I learned the hard way)

---

### Post by nakama85 on 2009-11-08
Thanks for the reply everyone. 

I ran the check as recommended via the Disk Utility. Everything seems to be ok.
However I am a little concerned. The disk I am having problems with is an ext4 storage only drive (no OS) But on occasion my computer will freeze..I will reboot... then that disk will fail to mount. But then if i shut down and wait a while and boot up again it will be fine.

any ideas?

---

### Post by kio_http on 2009-11-08
In terminal sudo apt-get install hddtemp

then 
sudo hddtemp /dev/sda 

for 1st disk

for 2nd sdb and so on

---

### Post by nakama85 on 2009-11-08
> **kio_http said:**
> In terminal sudo apt-get install hddtemp

then 
sudo hddtemp /dev/sda 

for 1st disk

for 2nd sdb and so on

Sorry for asking this but I never install and run anything without knowing what it is. What is "hddtemp"?

---

### Post by Arthur_D on 2009-11-08
hddtemp is a small utility for checking your hard drive temperature.

---

### Post by tommynz1975 on 2009-11-08
can I please jump in here and ask
what range should your HDD temp fall in to be ok?

much thanks :popcorn:

---

### Post by kio_http on 2009-11-08
> **tommynz1975 said:**
> can I please jump in here and ask
what range should your HDD temp fall in to be ok?

much thanks :popcorn:

Mine goes to about 37 C used to reach 50 C but now I've installed a cooler fan on it.

---

