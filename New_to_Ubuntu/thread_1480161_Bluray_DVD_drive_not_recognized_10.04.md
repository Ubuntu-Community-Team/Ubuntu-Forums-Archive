---
title: "Bluray DVD drive not recognized 10.04"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by taprimo on 2010-05-11
I just built my system.  My bios recognizes the Pioneer BDR-205 drive.  However, I show my hard drive, a floppy drive, and my current thumb drive in the computer window.  There is no floppy drive installed and the optical drive is connected by SATA.  I am not versed in command line.

Trevor

---

### Post by mbzn on 2010-05-11
Hi, and welcome

I don't know about 10.04 but my sony drive works fine(then again i have never had a bd-rom in the drive) in 9.10. It does work fine with dvd and cd. 

What is the response when you put a cd or dvd in the drive?

---

### Post by Objekt on 2010-05-11
How did you install Ubuntu 10.04?  USB stick?  I'm wondering whether the Blu-ray drive was recognized when you were running the live 10.04 session, before installing it, which I would guess you did at some point.

---

### Post by taprimo on 2010-05-11
Mbzn,

I installed it on USB.  I do not recall it recall it ever recognizing the drive.

---

### Post by taprimo on 2010-05-11
There is no response from the software when I insert an audio or data disk.  The drive does spin up though.

---

### Post by mbzn on 2010-05-11
Go to the file manager(places/computer), then go to 'file system'(on the left hand side) then /media (on the right hand side) look for cdrom0...

Also browse to /dev and look for 'scd0'

---

### Post by Objekt on 2010-05-11
OP, are you planning to watch Blu-ray movies once you do get the drive recognized?  I'm not sure how one would go about watching Blu-ray discs in Ubuntu.  As far as I know, Blu-ray player software is all Windows-only.

---

### Post by taprimo on 2010-05-11
Mbzn,

There is not a folder cdrom0.  I have Floppy and Floppy0.

There is no folder /dev and look for 'scd0'

Thanks,

Trevor

---

### Post by taprimo on 2010-05-11
[Objekt]("http://ubuntuforums.org/member.php?u=407368"),

The drive was actually given to me.  I do intend to be running multiple OSs eventually on the system.

Trevor

---

### Post by Objekt on 2010-05-13
> **taprimo said:**
> [Objekt]("http://ubuntuforums.org/member.php?u=407368"),

The drive was actually given to me.  I do intend to be running multiple OSs eventually on the system.

Trevor

Nice windfall!  Your Pioneer BDR-205 is a $185+ item.  Any luck yet getting it to work?

I hate to say it, but you may be dealing with defective hardware.  It's pretty unusual for Vista or Ubuntu to flat-out not detect a drive which shows up in BIOS.  I once had the symptoms you describe (drive spins, but OS doesn't detect it) with the CD/DVD-ROM drive on a Compaq notebook.  I ended up having to replace the drive.

If the drive is still under warranty, you should probably investigate doing an RMA with Pioneer.

---

### Post by taprimo on 2010-05-13
The drive is not working in Ubuntu.  However it did load it onto an XP machine and with the driver updates it was immediately operational and works flawlessly.  I have ordered a LG cheapy just to see if that changes things.  Could it be the SATA port I have it in?  I have six ports that are 3.0 and two that are 6.0.

The Bios Does recognize it.  I went into the bios and disabled the floppy.

Hmmm.

---

### Post by Objekt on 2010-05-13
Very odd.  Sure, try a different SATA port.  I don't have any other ideas at this point.

---

### Post by barreyi on 2010-06-06
I have the exact same problem with the exact same drive.  I was wondering if there was any change once you plugged the drive into a different sata port.  I was wondering if there is no support in ubuntu for that drive.  Thanks.

---

### Post by taprimo on 2010-06-06
I went into my bios and disabled the floppy controller and it worked perfectly when I booted.

---

### Post by jjloupe on 2010-06-09
Many are having the optical drive problems after the upgrade to 10.04, but there is no response from support.,

---

### Post by k3lt01 on 2010-07-01
You will probably need to [edit your fstab file]("http://ubuntuforums.org/showthread.php?t=283131") and create a cdrom0 folder in /media. Reboot and you should at least be able to read a CD/DVD, I can't promise if it will read a Blu-Ray though.

---

### Post by arapaho on 2010-07-01
> **jjloupe said:**
> Many are having the optical drive problems after the upgrade to 10.04, but there is no response from support.,

Exactly. I reported it as a bug after I had problems with DVD on Linux Mint. Maybe it would be a good idea if you reported it as a bug too on Ubuntu launchpad.
[https://bugs.launchpad.net/linuxmint/+bug/600213](https://bugs.launchpad.net/linuxmint/+bug/600213)
It seems, it is the only way to get developers attention to the problem.

---

### Post by philinux on 2010-07-01
> **taprimo said:**
> I went into my bios and disabled the floppy controller and it worked perfectly when I booted.

This ^. Looks like solved it.

---

### Post by philinux on 2010-07-01
> **taprimo said:**
> I went into my bios and disabled the floppy controller and it worked perfectly when I booted.

This ^. Looks like solved it.

---

### Post by arapaho on 2010-07-01
Could you give me a more detailed tip how can I do it? I have no idea about bios. I don't want to mess up anything.

---

### Post by k3lt01 on 2010-07-01
If you mean with the issue Lucid is having recognising cd/dvd/blu-ray drives then take a look at the link in my previous post that will help you. If, on the other hand, you mean in setting up your BIOS we will need to know what your BIOS is and you could probably Google that information and get it straight from the manufacturer

---

### Post by arapaho on 2010-07-02
My fstab for DVD device looks like this:
```
/dev/sr0	/media/dvdcd	udf,iso9660	group,users	0	0
```

Attached Thumbnails shows my MountManager (from Mint) settings.

When I press mount nothing happens. The options are:
atime,suid,mand,group,users,auto,rw,dev,exec,async

What can I do? I discovered that I when I click apply (even when I don't change any settings) options under 'Actions' change from 'Mount' to "Mount all resources" and when I click on this option DVD finally becomes visible in Nautilus. But I don't want to do it every time I put in DVD. 
This configuration should work all the time but it doesn't. When I remove my DVD and put it in again the situation repeats itself. Help, please.

---

### Post by k3lt01 on 2010-07-02
This is my fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5fc62749-ff32-4369-94bd-d50cf6ac2e03 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=eb7d46af-6ef9-4004-aef2-eb9f9fe2f7e6 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=b929474e-fb26-4f86-a701-d25c16231025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Have you got a folder in /media for your DVD drive? if you haven't you will have difficulty mounting it.

---

### Post by arapaho on 2010-07-02
I do created dvdcd folder in /media. It is set as a mount point as you can see in in Mountmanager attached thumbnail.
I noticed that previously I forgot to save the configuration. But I'm note sure where to do it. In fstab file or in any newly created file?
Maybe it is the issue of who have permission to mount DVD? When I close Mountmanager without saving changes and reopen it I see that 'Who can mount the partition' is set to 'Only administrator'. I don't understand it. I'm the administrator. Why linux is so complicated...

---

### Post by k3lt01 on 2010-07-02
Save the configuration in /etc/fstab

---

### Post by arapaho on 2010-07-02
I saved the configuration, but when I opened the fstab file it appeared that content didn't changed at all. Maybe this Mountmanager doesn't work properly. I have to do it directly in fstab. Can someone help me to write correct settings and permissions?
I read this topic about iso9660:
[http://ubuntuforums.org/showthread.php?t=283131&page=3](http://ubuntuforums.org/showthread.php?t=283131&page=3)
Interesting that this DVD that I have problem with was burned from ISO image.

---

### Post by k3lt01 on 2010-07-02
```
gksudo gedit /etc/fstab
``` that will give you administrator rights to change your fstab.

I'd remove "mount manager" before you did that though as it seems, from what you are saying, that it isn't letting you save your fstab file properly.

---

### Post by arapaho on 2010-07-02
Ok, but I don't know what to write in fstab, so that it will automount DVD everytime for every user.

---

### Post by k3lt01 on 2010-07-02
> **arapaho said:**
> Ok, but I don't know what to write in fstab, so that it will automount DVD everytime for every user.take a look at the last line in my fstab and you will see what it is supposed to look like. just change it in yours to suit the folder you created in /media

---

### Post by arapaho on 2010-07-02
```
/dev/sr0 /media/dvdcd udf,iso9660 user,noauto,exec,utf8 0 0
```
I changed it to match your configuration but still it doesn't work. But I I wrote earlier some DVD are read without problem. I suspect that has something to do with iso problem, because DVD that fails to be read was burned from ISO. And I'm sure it was burned correctly because I checked md5 and compared data burned DVD with data with k3b option.

---

### Post by k3lt01 on 2010-07-02
what is sr0? mine says scd0

It may be an issue, as you say, with iso, I don't know. I am at the limit of my knowledge now with this. What I described to you has worked for me without a problem so I don't know why it hasn't worked for you.

I hope someone else comes along that can offer assistance.

Maybe if you start a new thread describing everything you have done but put it in the hardware section of the forum you may get more help.

---

### Post by arapaho on 2010-07-03
Can you paste your permissions to folder /media/cdrom0?
On a media folder do right mouse button - open in Terminal and write:
```
ls -l
```
I have:
```
dr-xr-xr-x 7 root   root    2048 2008-10-27 12:03 cdrom0
```
When I open /media/cdrom0 (I renamed it) as a root it finally shows me its contents.
I discovered that
```
pmount /dev/scd0
```
also do this without any special root permissions. 'pmount' is a program and must be installed first. Anyway, I want to configure it so that it will work without any special permissions or commands.

---

### Post by k3lt01 on 2010-07-03
> **arapaho said:**
> Can you paste your permissions to folder /media/cdrom0?
On a media folder do right mouse button - open in Terminal and write:
```
ls -l
```
That's the long way to do it, just type
```
ls -l /media
``` and with this I got
```
lrwxrwxrwx 1 root root    6 2010-05-07 15:49 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-05-07 15:49 cdrom0
```

> **arapaho said:**
> I discovered that
```
pmount /dev/scd0
```
also do this without any special root permissions. 'pmount' is a program and must be installed first. Anyway, I want to configure it so that it will work without any special permissions or commands.What I posted above didn't need any special permissions nor did I need to install anything to do it.

Google Linux commands or Ubuntu commands and find them so you can learn them. Doing this will help you so you can avoid installing things you don't need.

---

