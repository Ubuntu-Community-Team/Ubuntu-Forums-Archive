---
title: "Ubuntu 10.04 will not boot"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by jafurcha on 2010-05-09
I just upgraded from Ubuntu 9.10 to 10.04 and immediately had some problems with booting after a restart.

Here is a video but I will explain it anyway:
[http://www.youtube.com/watch?v=aEr7glFLf48](http://www.youtube.com/watch?v=aEr7glFLf48)

The font changed suddenly during startup, and then the screen flashed, and the logo appeared but then became what I would call pixelated. Then all I got was a black screen and it just hung there.

Did a hard restart and entered the GRUB loader and chose Ubuntu 10.04 kernel 2.6.31-21 instead of Ubuntu 10.04 kernel 2.6.32-22 and it came up with this message which hung there long enough for me to snap a photo:

mount: mounting none on /dev failed: No such device092b3250a
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory.

Then, just as I thought it would hang there forever, it started to fill the screen with commands (yay, it's doing something!!), which I couldn't copy down, and eventually started up and is working fine. However: If I start it up normally it will never never boot. I always have to enter GRUB and choose the other option.

And who knows when this tactic will stop working? Please help!

---

### Post by Diabolis on 2010-05-09
Your second kernel works and it will work always, so don't worry. Probably Grub is the one that can't find the partition from which it can boot, it doesn't find the new kernel. Can happen if you modified your partition table after the system was installed.

---

### Post by jafurcha on 2010-05-10
Hey thanks Diabolis!

Edit my partition table? I don't even know what that is...

But is there any way I can fix the problem with Grub? 

Thank you for your time.

Sincerely,
Jacob Furchak

---

### Post by lamb.chris on 2010-05-10
I had this same problem and fixed it with this:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by jafurcha on 2010-05-10
That did not work.


jacob@jacob-laptop:~$ echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
[sudo] password for jacob: 
options i915 modeset=1
jacob@jacob-laptop:~$ sudo update-initramfs-u
sudo: update-initramfs-u: command not found
jacob@jacob-laptop:~$

---

### Post by jafurcha on 2010-05-10
Okay I was a bit hasty in saying it did not work. I tried most of the things in the article (and also I did not put in a space in the statement "sudo update-initramfs -u" and that's why the statement did not work), not doing the things that said "this will disable your 3d acceleration" or the things that said "this may cause problems for your system".

But I did use this statement correctly <echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf> I believe.

Also I added <http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu> to my software sources

---

### Post by jafurcha on 2010-05-11
Ok now it works.

But now it crashes in the middle of a Youtube video, or while I am switching windows when using ZNES Emulator, or while I am trying to view something on [www.newgrounds.com/audio](www.newgrounds.com/audio) which are all graphical applications (newgrounds has a visual which runs while playing audio and it crashed when the visual started).

I googled it and thought it might be a GEM Leak so I went here:
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

jacob@jacob-laptop:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
61542400 object bytes
jacob@jacob-laptop:~$ 

and followed the instructions but it didn't seem to update anything (it said there were 0 updates and 0 things installed successfully)

I did this and rebooted:
echo options i915 modeset=0 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

but it gave me a graphics warning and let me revert to old settings.
so I went into terminal and typed this
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

jacob@jacob-laptop:~$ grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
61542400 object bytes
jacob@jacob-laptop:~$ 

Thanks

---

