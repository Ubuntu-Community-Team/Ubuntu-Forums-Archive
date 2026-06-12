---
title: "accessing root"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by daddy97032 on 2010-09-10
I can't get into root -it tells me that I'm not the owner so I don't have permission. How do I change this ? I'm trying to update the bios on a hopelessly outdated machine and I need to get the floppy to work so that I can flash the bios so I can upgrade.
any help is appreciated.
Thanks in advance

---

### Post by Calash on 2010-09-10
I am not sure I understand what your problem is.  Nothing in the operating system will effect your ability to access the BIOS.

Unless your having issues with writing the bios to the floppy drive, but that should not require root unless you need to add yourself to the floppy group.

You should be able to do that from under the System->Administration->Users and Groups menu.

---

### Post by iMisspell on 2010-09-10
In the terminal, *gksudo nautilus* will bring up a password check and then the root file browser.

Or if you are working completely from the commanline, *sudo WHAT-EVER*  will let you execute root commands. You have to use *sudo* before each command.

---

### Post by bodhi.zazen on 2010-09-10
See : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I also advise you learn Linux Permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by coffeecat on 2010-09-10
> **daddy97032 said:**
> I'm trying to update the bios on a hopelessly outdated machine and I need to get the floppy to work so that I can flash the bios so I can upgrade.

Are you sure you need to update the BIOS? Do you think you need to update the BIOS to get the machine to run Linux? Does it run any form of Linux now?

A cautionary tale:

I had a machine that ran Windows XP, Windows 7 RC (before Windows 7 was released) and every version of Linux that I threw at it - including Ubuntu. There was a minor issue that I hoped would be fixed by a BIOS update, so I downloaded the newer BIOS code plus a Windows GUI utility for flashing the BIOS which included a facility for saving the old BIOS. Fortunately I had the presence of mind to use this and to backup the old BIOS version. I then successfully updated the BIOS only to find that the machine would now only boot into Windows. Not a single Linux distro would boot up. BIOS bugs which interfere with Linux are not unknown - I had been bitten by one.

But with Windows I was able to reflash the older version back to the BIOS and I was into Linux again. The machine is still running Ubuntu - I've now given it to a relative - and it and Ubuntu are doing sterling work.

---

