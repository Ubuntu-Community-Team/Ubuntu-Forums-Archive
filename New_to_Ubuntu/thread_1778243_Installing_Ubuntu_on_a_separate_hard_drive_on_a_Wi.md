---
title: "Installing Ubuntu on a separate hard drive on a WinXP PC"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by L Campbell on 2011-06-08
I would like to install a separate hard drive with Ubuntu 10.04.2 on my WinXP PC, as opposed to having both systems on a partitioned hard drive.

My searches have not come up with a guide for doing this and my concern is whether the PC would recognize the hard drive with Ubuntu on it.

I would appreciate any suggestions.

TIA.

---

### Post by wildmanne39 on 2011-06-08
> **L Campbell said:**
> I would like to install a separate hard drive with Ubuntu 10.04.2 on my WinXP PC, as opposed to having both systems on a partitioned hard drive.

My searches have not come up with a guide for doing this and my concern is whether the PC would recognize the hard drive with Ubuntu on it.

I would appreciate any suggestions.

TIA.
Hi, yes it would see the drive and use it. Here is a guide.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Jerry N on 2011-06-08
> **L Campbell said:**
> I would like to install a separate hard drive with Ubuntu 10.04.2 on my WinXP PC, as opposed to having both systems on a partitioned hard drive.

My searches have not come up with a guide for doing this and my concern is whether the PC would recognize the hard drive with Ubuntu on it.

I would appreciate any suggestions.

TIA.

Disconnect your Win XP hard drive.  Install Ubuntu 10.04.2 on its hard drive and check it out to make sure it is working.  Reconnect the XP hard drive (with the computer turned off, of course).  On restart, the Ubuntu drive will be the first drive on the boot list and Ubuntu will boot up.  It will also find the XP installation and the next time you boot up you will be given the choice of Ubuntu or Windows.  Simple as that!  My secondary computer is set up that way right now - Mint 11, Mint 10, and Ubuntu 11.04 on one (removeable) drive and Win 7 and Win XP on the other (removeable) drive.  

Jerry

---

### Post by wolfen69 on 2011-06-09
> **Jerry N said:**
> Disconnect your Win XP hard drive.  Install Ubuntu 10.04.2 on its hard drive and check it out to make sure it is working.  Reconnect the XP hard drive (with the computer turned off, of course).  On restart, the Ubuntu drive will be the first drive on the boot list and Ubuntu will boot up.  It will also find the XP installation and the next time you boot up you will be given the choice of Ubuntu or Windows.  Simple as that!  My secondary computer is set up that way right now - Mint 11, Mint 10, and Ubuntu 11.04 on one (removeable) drive and Win 7 and Win XP on the other (removeable) drive.  

Jerry

That's a great way to do it, but sometimes ubuntu will not see windows right away.
```
sudo update-grub
```
will fix that.

---

### Post by Mark Phelps on 2011-06-09
When you install Ubuntu to its own separate physical drive, even when you later reconnect another drive with MS Windows, it will not know about Windows in term of boot options.

You will need to boot into Ubuntu, open a terminal, enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for Windows XP.

When you reboot, you should get a GRUB menu.

---

### Post by Jerry N on 2011-06-09
> **Mark Phelps said:**
> When you install Ubuntu to its own separate physical drive, even when you later reconnect another drive with MS Windows, it will not know about Windows in term of boot options.

You will need to boot into Ubuntu, open a terminal, enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for Windows XP.

When you reboot, you should get a GRUB menu.

I've never found that to be necessary, I just let it boot a couple of times.  Of course "sudo update-grub" is a pretty trivial task and can't hurt!

Jerry

---

### Post by verymadpip on 2011-06-09
When I did this I had to go into my BIOS & set the drive with Ubuntu on it as the first boot HDD.  I run W7 but I imagine the process is the same.

GRUB saw windows no problem & the whole thing ticks over beautifully.

here's the thread:

[http://ubuntuforums.org/showthread.php?t=1706223](http://ubuntuforums.org/showthread.php?t=1706223)

(I didn't have two entries in the GRUB menu for W7 by the way).

---

