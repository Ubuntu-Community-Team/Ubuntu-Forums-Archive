---
title: "install stalls at partitioning - Xubuntu 8.10"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by simontaylor on 2009-07-12
Having attempted to install Puppy on a Dell Inspiron 3500 (64 Mb Ram ~ 333.9 Mhz ~ i686 CPU) and failed - but having wiped the harddrive and removed all preexisting partitions - and failed (Puppy won't reboot and won't connect to the internet), for my next trick I'm attempting to install Xubuntu 8.10 (alternate CD for 32-bit). Everything looks peachy until the install reaches "Starting up the partitioner." Here it stalls at 50% every time. ctrl+alt+delete forces a reboot and then it stalls at the same place.

What should I do? Apart from run for the hills?

(What I think has happened: Puppy does not set up partitions automatically or by default and thinking to shortcut past the warning signs that were already apparent I took the option to superfloppy the whole of the harddrive which has left it entirely bereft of partitions. Puppy helpfully tells me I ought not do that. It's an option reserved for running the OS off flashdrives and sticks and so on. Not harddrives. I think Xubuntu is striking out into the desert I've made of the harddrive and without signposts or landmarks of any kind is unable to set up its partition.)

Advice please,

Yours,

Simon Taylor

---

### Post by Ji Ruo on 2009-07-12
I think you're running out of memory - even if you get it to install you're going to struggle to do anything using the desktop. You should either put some more in or try an even more minimal distro like DSL or SliTaz.

---

### Post by LewRockwell on 2009-07-12
use puppy live-run gparted to delete all partitions on the hard drive and just create one new ext2 partition out of the whole drive then try installing it again

if you still have problems then I would get a copy of Damn Small Linux and try that

you'll feel better once you've had some success with SOMETHING...and don't fret about all the reformatting, rebooting, mistakes, and failures...it all contributes to our own personal character...

I run a 1996 Gateway 2000 Solo on DSL and it works wonderfully!

System specs: 150MHz processor, 224MB ram, 3GB hard drive, 10/100 PCMCIA ethernet card, cd-rom drive, floppy drive...and, unfortunately, a dead and difficult to replace CMOS battery...lol

Hey, whatever you do, we're pullin' for ya!

.

---

### Post by LewRockwell on 2009-07-12
oh, don't even bother with xubuntu on that machine

.

---

### Post by halitech on 2009-07-12
with only 64 meg of ram, its not going to be the fastest machine around but if you pick and chose wisely, you should be able to get something running.

first off, download a copy of the gparted cd and hope it runs to allow you to reset the drive.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

then look into doing a minimal install with no gui. This should get you a working install with just the command line. Then look into adding the apps you want using the lightest possible apps.

You could also try Debian Lenny with XFCE or LXDE
[http://forums.debian.net/viewtopic.php?f=16&t=26566](http://forums.debian.net/viewtopic.php?f=16&t=26566)

full cd download - 
[http://cdimage.debian.org/debian-cd/5.0.2/i386/iso-cd/debian-502-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.2/i386/iso-cd/debian-502-i386-xfce+lxde-CD-1.iso)

---

### Post by LewRockwell on 2009-07-12
> **halitech said:**
> with only 64 meg of ram, its not going to be the fastest machine around but if you pick and chose wisely, you should be able to get something running.

first off, download a copy of the gparted cd and hope it runs to allow you to reset the drive.

I'd like to point out that the Puppy Linux LiveCD Disk that the OP already has...

Contains gparted...

.

---

### Post by halitech on 2009-07-12
correct, forgot about that as I don't use puppy and haven't looked at it much even with the new release.

---

### Post by LewRockwell on 2009-07-12
> **halitech said:**
> correct, forgot about that as I don't use puppy and haven't looked at it much even with the new release.

I wouldn't be without a copy in my tech kit

.

---

### Post by halitech on 2009-07-12
I have a copy of it, DSL and a few other "low spec" distros, just haven't had much use for them lately.

---

### Post by simontaylor on 2009-07-12
Thank you for your advice. First step gparted on Puppy disc as per & try again with Xubuntu. (Noone's suggesting trying to push through to the other side with Puppy. Why? Ubuntu forum?). Second - - - DSL sounds like it might be a better choice than Debian. I'll go there first.

I need to run the GUI - it's for educational purposes as much as functionality: I don't think my son will be up to commandline ... I know I'm not. 

Thanks again.
Simon

---

