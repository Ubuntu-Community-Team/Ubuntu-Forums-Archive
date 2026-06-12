---
title: "Buying an external USB Hard Drive"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by r3bol on 2009-03-28
I want to buy a USB external hard drive and was wondering if there were any issues with this type of hardware on Ubuntu (things to look out for)? 
A very cheap one at a local store is the Iomega ( [http://www.gigantti.fi/is-bin/INTERSHOP.enfinity/WFS/store-gigantti-Site/fi_FI/-/EUR/El_DisplayProductInformation-Start;pgid=D6ez6oZKCVlSR0EjF5FBwx1q0000Ieq2gFQ0?ProductID=oMbD4QFHVHwAAAEcrLR.6.Z7&CatalogCategoryID=wxbD4QFH4owAAAEOj1g03xil](http://www.gigantti.fi/is-bin/INTERSHOP.enfinity/WFS/store-gigantti-Site/fi_FI/-/EUR/El_DisplayProductInformation-Start;pgid=D6ez6oZKCVlSR0EjF5FBwx1q0000Ieq2gFQ0?ProductID=oMbD4QFHVHwAAAEcrLR.6.Z7&CatalogCategoryID=wxbD4QFH4owAAAEOj1g03xil) )
Does anyone have an Iomega drive running without problems? 

Thanks

---

### Post by Paqman on 2009-03-28
Nope, they work fine. It's just a USB device, after all.

Just remember that since it's USB, your data transfer rate is pretty slow. If you need speed then stick to internal drives, or use eSATA if you have it available.

---

### Post by Delta28 on 2009-03-28
No I don't sorry, but I don't think there is usually problem with that Dr Small would be a good person to ask if you could get a hold of him...

---

### Post by MrWES on 2009-03-28
> **r3bol said:**
> I want to buy a USB external hard drive and was wondering if there were any issues with this type of hardware on Ubuntu (things to look out for)? 
A very cheap one at a local store is the Iomega ( [http://www.gigantti.fi/is-bin/INTERSHOP.enfinity/WFS/store-gigantti-Site/fi_FI/-/EUR/El_DisplayProductInformation-Start;pgid=D6ez6oZKCVlSR0EjF5FBwx1q0000Ieq2gFQ0?ProductID=oMbD4QFHVHwAAAEcrLR.6.Z7&CatalogCategoryID=wxbD4QFH4owAAAEOj1g03xil](http://www.gigantti.fi/is-bin/INTERSHOP.enfinity/WFS/store-gigantti-Site/fi_FI/-/EUR/El_DisplayProductInformation-Start;pgid=D6ez6oZKCVlSR0EjF5FBwx1q0000Ieq2gFQ0?ProductID=oMbD4QFHVHwAAAEcrLR.6.Z7&CatalogCategoryID=wxbD4QFH4owAAAEOj1g03xil) )
Does anyone have an Iomega drive running without problems? 

Thanks

I just put together this 1TB external eSATA drive from new egg: (it has both USB 2.0 and eSATA connections)


Western Digital Caviar Green WD10EADS 1TB SATA 3.0Gb/s Hard Drive - OEM Item #: N82E16822136317

Rosewill RX-358-S SLV (Silver) 3.5" SATA to USB & eSATA Ext. Enclosure w/Int.80mm fan - Retail Item #: N82E16817173043

And I also got this eSATA PCI controller card, and that was automatically detected in 8.04-Server Edition:

Rosewill RC-210 Silicon Image e-SATA PCI Controller Card - Also includes an additional Low Profile Size PCI Bracket - Retail
Item #: N82E16816132007

All together w/ shipping it was ~$150 --I'm very happy.

Bill

---

### Post by ranch hand on 2009-03-28
I slapped a 320G Samsung in a cheap single drive external enclosure from Ebay and it works like gangbusters.

I would not worry about any external with Ubuntu.

---

### Post by r3bol on 2009-04-04
[IMG]http://i157.photobucket.com/albums/t54/r3bol/ntfs.png[/IMG]

EEK! So this is what I was fearing! Error messages that I don't understand. 
I have an old Windows partition that is picked up, so I thought if I unmounted it, it would pick up the Iomega, but that failed.

Next I tried this - blindly obeying the error message...

[COLOR="Green"]leke@leke-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/Iomega HDD -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .[/COLOR]


Please! How do I get it working?

---

### Post by green0eggs on 2009-04-04
What might help: downloading 'Disk Manager' (it's in Add/Remove and under 'System Tools')

Go to 'Advanced Configuration' and select the HD you want, try mounting it from there. The nice reassuring GUI method is the only one I'm qualified to advise.

I've been given this error for my external hd when I've shutdown Windows to hastily, if you are dual booting it might be an idea to go to Windows and Safely Remove, that said I have 'Forced' the mounting from 'Disk Manager' and it never did my hd any harm.

---

### Post by Halcyon31415 on 2009-04-04
I know this is not really useful but I used to have a problem with mounting an 8 gig memory card on my PSP. I upgraded my distribution of Ubuntu and it worked fine from then on? I don't know how you feel about upgrading distributions but it might be worth a shot. I'm sorry I don't understand the error code either :(

Good luck !!!

---

### Post by MrWES on 2009-04-04
> **r3bol said:**
> [IMG]http://i157.photobucket.com/albums/t54/r3bol/ntfs.png[/IMG]
[COLOR="Green"]leke@leke-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/Iomega HDD -o force



The best way to fix this is if you have a windows box, connect the drive and close down windows properly. That should fix the flag that the drive is in use.

I'm assuming you did a 

```
sudo mkdir /media/Iomega\ HDD
```

and changed the ownership and perms to suit your needs with

```
sudo chown user:user /media/Iomega\ HDD
```
user = your actual user name
and
```
sudo chmod 0755 /media/Iomega\ HDD
``` 
or whatever perms you want.

Also you have a space in your mount command, it should read:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/Iomega\ HDD -o force
```

Notice I added the \ after Iomega

Hope that helps.

Bill

---

### Post by ranch hand on 2009-04-04
I think the advice from MrWES is probably the best.

If you need to try something else I would boot to recovery mode and let it run through its routine.

Did the IoMega come with NTFS on it?

---

### Post by r3bol on 2009-04-04
> The best way to fix this is if you have a windows box, connect the drive and close down windows properly. That should fix the flag that the drive is in use.

Thanks MrWES, I decided to try this before any of the other advice and after booting back into Ubuntu it picked up the drive automatically.
> Did the IoMega come with NTFS on it?Yes it did. I thought about reformatting it to ext-2 or ext-3, but then I realised that I might need to take it round to a family member some day who all run Windows.

---

