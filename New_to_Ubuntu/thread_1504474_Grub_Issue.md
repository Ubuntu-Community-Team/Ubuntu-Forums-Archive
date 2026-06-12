---
title: "Grub Issue"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Failboat88 on 2010-06-08
My pc goes to the grub screen, which didn't use to happen, and my key board and mouse do not work. I can't select a version to boot into. I have seen my pc shut off while streaming video. Right after it did that tonight the problem started. The pc is my htpc and I don't update it. It's running 9.1 with a gnome desktop. Anyone have any ideas?

---

### Post by Failboat88 on 2010-06-08
I tried to reinstall grub with this.

Command line
Boot your computer up with Ubuntu CD
Open a terminal window or switch to a tty.
Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
Type "grub"
Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
Quit grub by typing "quit".
Reboot and remove the bootable CD.

When I got to "grub" it said grub not installed. So I did apt-get install grub. I don't think I installed it onto my hard drive because when I rebooted nothing changed.

---

### Post by Buuntu on 2010-06-08
After you run 'sudo apt-get install grub' you have to run 'sudo grub-install /dev/sda' where /dev/sda is the location of your hard drive that you want grub on.  If you only have one HDD it will most likely be /dev/sda but if not you will have to find out.  You can run 'sudo fdisk' or other commands to figure this out if you're not sure.

---

### Post by Failboat88 on 2010-06-08
Can high cpu temps cause some of these problems? I went into my bios and my keyboard was working. I glanced at my cpu temp and it was at 88C. My house is hot right now I have no ac on because I am poor.  

I'll try what you said after work buuntu. Do you know why it told me I didn't have grub installed when I can see the screen after I boot into my hdd?

In the past it never went to the grub screen so I would have not known if my keyboard ever worked there. Is there a way to config my grub from the live cd to skip the screen?

---

### Post by kansasnoob on 2010-06-08
You probably have grub 2 and you're trying to use legacy grub commands to reinstall grub.

That will NOT work!

Please save us all time and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2010-06-09
> **Failboat88 said:**
> Can high cpu temps cause some of these problems? I went into my bios and my keyboard was working. I glanced at my cpu temp and it was at 88C. My house is hot right now I have no ac on because I am poor.

Can't give you a specific answer because the operational temperature range is CPU-specific, but in my experience, most CPUs tend to run around 40C when idle and get up into the 50's or 60's at most when under load.  It's not uncommon for shutoff thresholds to be set at 70C.  So, a temp in the upper 80's is really HOT.

And, yes, when the CPU gets too hot, it generally either throttles back to a slower speed (to cool down), or it shuts down.

---

