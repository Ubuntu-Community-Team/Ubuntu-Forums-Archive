---
title: "Error after upgrade to 11.04 in Parallels"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by 44tr on 2011-05-14
Hey Guys I have a iMac running Snow Leopard with Parallels Desktop 6 that I installed Ubuntu in (virtual machine).  I just upgraded to 11.04 and now when I try to boot into Ubuntu, I get the error:

"An error occurred while mounting /media/psf

Press S to skip or M for manual recovery"

If I press S, it still doesn't boot into Ubuntu; if I press M, I don't know what to do.

Is this fixable (how please???), or am I hosed and have to reinstall from scratch?

Any help or advice is appreciated.

---

### Post by frankbooth on 2011-05-14
I'm not sure how Parallels Desktop works, but I assume your drive labeled 'psf' contains something related to Parallels Desktop?

It could be a fstab error. If you press 'M' for manual recovery and type:
```

sudo nano /etc/fstab

```

Does it have an entry for 'psf'? What does it say?

---

### Post by 44tr on 2011-05-14
> 
Does it have an entry for 'psf'? What does it say?

It says:
```
#Parallels Shared Folder mount
none    /media/psf   prl_fs   sync,nosuid,nodev,noatime,share   0   0
```

Thanks for looking at.

---

### Post by 44tr on 2011-05-15
Anybody else have some additional advice on how to proceed?

---

### Post by 44tr on 2011-05-15
Anybody?  Please?

---

### Post by wildmanne39 on 2011-05-15
> **44tr said:**
> Anybody?  Please?
Hi, I use virtualbox, so I know there are some requirements that need to be meet before you install ubuntu into a virtual enviroment, like the package that builds the kernel modules so ubuntu can run, did you read up on the program that you are using before you installed ubuntu, if not I recommend doing that now, and see what the requirements are for ubuntu to run. I hope this helps I am sorry that I can not be of more help, also if you want to see the requirements needed you can go to virtualbox.org and it will give an idea of what to look for.:)

---

### Post by 44tr on 2011-05-16
Parallels is setup to run Ubuntu among other things.  I installed Ubuntu with no problems and used it frequently in Parallels.  Parallels provides a tool package that extends functionality for Ubuntu.  No problems were encountered during use and no problems were encountered during the upgrade.  When I rebooted, I got the above error and it has been unusable since.  I can do a clean install again, but I hate to do that unnecessarily, especially if there is an easy fix.  I may need it the next time I upgrade.

Thanks!

---

### Post by 44tr on 2011-05-19
Anybody else have an idea if I can fix this machine to boot.  What would you normally look at with this kind of error?

---

### Post by damonmowr on 2011-05-23
The problem is that Parallels Tools does not currently support Ubuntu 11.04:

[http://forum.parallels.com/showthread.php?t=109817](http://forum.parallels.com/showthread.php?t=109817)

You can either wait for Parallels to release an update and then reinstall Parallels Tools, or try uninstalling the current version of Parallels Tools from the command prompt you get after pressing "M" at the error message.  Hope this helps.

---

### Post by 44tr on 2011-05-28
Mmmm.  I'm afraid it does help. :(

Fortunately there is not data loss, since I store that separately.  Loading and configuring all the non-default software again will be a pain though.

Can anybody give me a clue on how to uninstall the tools from the manual prompt?  It just didn't occur to me that the tools were version specific.  Dumb I know.

Thanks for setting me straight.

---

### Post by damonmowr on 2011-05-29
Boot the VM into manual recovery mode and log in.

From the Parallels menu, select Virtual Machine..Reinstall Parallels Tool.  This will connect the Parallels Tools image to your cdrom device.

Next, in your VM command prompt, type ```
mount -t auto /dev/cdrom /mnt/cdrom
```

If this doesn't work, make sure the /mnt/cdrom directory exists.  If not, type ```
sudo mkdir /mnt/cdrom
``` and then try the above command again.

Change directory to /mnt/cdrom and execute ```
sudo ./install
```

This will start the installer and it should give you the option to uninstall Parallels Tools. DO NOT try to reinstall, as the install will fail.  Once the uninstall completes, your VM should restart and should boot normally ,minus the Parallels integrations (mapped home drive, etc.).  Once Parallels releases an update, you can reinstall the tools and get these features back.

Hope this helps.

---

### Post by BHunsaker on 2011-06-08
Gave that a try, but it failed with something like "can't find /dev/sr1" when mounting /dev/cdrom.

Noticed that I had an .iso mounted as a second CD-ROM, so deleted that virtual device and removed the physical CD from the CD drive.

Rebooted with prl_tools_lin.iso configured as CD/DVD 1 under Virutal Machine -> Configure..  Attempting to mount /dev/cdrom fails with "mount: special device /dev/cdrom does not exist".

Issued the command:

```
mount -t auto /dev/sr0 /mnt/cdrom
```

Uninstalled the tools and rebooted successfully.

---

