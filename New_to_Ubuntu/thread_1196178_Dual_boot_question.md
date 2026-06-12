---
title: "Dual boot question?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Paul T. on 2009-06-24
I have Win XP & Ubuntu on my desktop pc, but am having problems with Windows and think I will have to re-install it, if so will I still get the dual boot screen at start up, or will I have to re-install Ubuntu as well?

---

### Post by skyjacker on 2009-06-24
> **Paul T. said:**
> I have Win XP & Ubuntu on my desktop pc, but am having problems with Windows and think I will have to re-install it, if so will I still get the dual boot screen at start up, or will I have to re-install Ubuntu as well?
You will have to install windows first, and then ubuntu, while installing ubuntu, it will create a new bootloader for you. Good luck!

---

### Post by Zzl1xndd on 2009-06-24
It is possible to reinstall Windows and not reinstall Ubuntu.

However Windows is going to right over the Boot loader, and you will need to reinstall grub by hand.

---

### Post by Octagonal on 2009-06-24
Whenever I do this, I just open up the case and unplug the ubuntu hard drive and set the windows hard drive to be the primary one in the BIOS settings.
Reinstall Windows and plug the ubuntu drive back in and everything works like normal.
No need to fiddle with Grub

---

### Post by jimv on 2009-06-24
Assuming you have both operating systems installed on the same harddrive:


Reinstall Windows.  Be sure not to delete the Ubuntu partition during this process.  Once you are done, you'll need to run this command from a terminal on the Live CD to re-setup Grub:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Then you should be able to boot both OS's again.

---

### Post by WRDN on 2009-06-24
> **jimv said:**
> Assuming you have both operating systems installed on the same harddrive:


Reinstall Windows.  Be sure not to delete the Ubuntu partition during this process.  Once you are done, you'll need to run this command from a terminal on the Live CD to re-setup Grub:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Then you should be able to boot both OS's again.

That assumes that Ubuntu is installed on the first partition of the first drive, which may not be true.

You can find the guide for reinstalling GRUB (from Ubuntu LiveCD) [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

You could also reinstall GRUB using the [Super Grub Disk]("http://www.supergrubdisk.org/") (or other tools/ LiveCD's).

Note that, to reinstall GRUB you need to use a LiveCD for Ubuntu 8.04 or above. When I tried reinstalling from the 7.10 LiveCD, the stage1 file could not be found.

---

### Post by -kg- on 2009-06-24
> **Octagonal said:**
> Whenever I do this, I just open up the case and unplug the ubuntu hard drive and set the windows hard drive to be the primary one in the BIOS settings.
Reinstall Windows and plug the ubuntu drive back in and everything works like normal.
No need to fiddle with Grub

Well, that'll work as long as Ubuntu is installed on the master hard drive and Windows on the slave, but if Ubuntu's on the slave drive, or if both OSes are installed on the same drive, you will have to re-install GRUB once you've installed Windows.

Re-installing GRUB is really pretty easy. Some directions are posted in the following post:

[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

There are two methods of doing it posted in the above thread...use whatever method you feel comfortable with.  I personally would go with the Live CD terminal method (Post #2) rather than using the installer, but that's me.  If you use the terminal method, though, be aware that the first couple of posts dealing with this tells you to become a superuser.  The only thing you really need to do is launch the terminal and type (or copy and paste):

```
sudo grub
```

which will launch the GRUB installer with root access.  From there you will be able to run all the commands without the "sudo" in front of them.  You might want to read into the thread if you have more problems, or post back here and someone will walk you through.

<edit> I see I was late again! :P  Much better link, too!

---

### Post by presence1960 on 2009-06-24
> **skyjacker said:**
> You will have to install windows first, and then ubuntu, while installing ubuntu, it will create a new bootloader for you. Good luck!

No!! NO!! NO!! Do not reinstall Ubuntu. Reinstall Windows to it's own partition and if necessary restore GRUB by doing this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

P.S. sorry -kg- didn't see your reply until after I posted mine. I just didn't want this person to lose their Ubuntu install for nothing.

---

### Post by Zzl1xndd on 2009-06-24
Octagonal's method is problably the best to use if Ubuntu is your master drive or you are using Sata.

---

### Post by egalvan on 2009-06-24
> **Octagonal said:**
> open up the case ..unplug the ubuntu hard drive
set the windows hard drive to be the primary one in the BIOS settings.
Reinstall Windows and plug the ubuntu drive back in and everything works like normal.
No need to fiddle with Grub

+1

This is an excellent method; ingenious, very simple, rather fool-proof;
definitely Microsoft-proof. :)
I like it.
Also, modern BIOS's allow changing boot order of separate drives,
accomplishing the same thing as physically disconnecting the drive.
(Just not as fool-proof)


Sadly it only works if you have two physical drives,
with Linux on the first drive,
and Windows on the second.

That setup is not very common to a newer Linux user,
who has probably set up dual-booting on a working Windows machine,
which only has one drive.

---

### Post by Paul T. on 2009-06-25
Thanks all for the advice, should have mentioned that I have both Windows & Ubuntu on same drive but in seperate partitions.

---

### Post by philcamlin on 2009-06-25
yup you just have to reinstall grub :popcorn:

---

### Post by Paul T. on 2009-06-25
> **philcamlin said:**
> yup you just have to reinstall grub :popcorn:

That's good to hear, got Ubuntu configured nicely now and don't want to have to re-install 2 operating systems. :D

---

