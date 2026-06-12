---
title: "Disappearing DVD Drive"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by kwacka on 2010-05-02
Problem was present in 9.10 & remains in new (not update) install of 10.04.

Boot computer, DVD drive identified, can read data & audio disks, can also write to media using brasero & K3b.

Some hours later DVD drive disappears - no apparent reason, the only way (so far) I've found to get it back (for a while) is to reboot. K3b/brasero report no optical drive, cannot mount with mount from command line (dev/sr0 /media/cdrom0 -t etc)

Replaced DVD drive (& cables) & problem persists. Added ```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto     0       0
``` to fstab in an attempt to resolve, but no change

Here are the results of lshw -C disk for the two states:

_Drive not recognised_

```
*-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       **bus info: scsi@1:0.0.0**
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       [B]capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open[/B]
```

_Drive recognised_

```
*-cdrom
       description: DVD-RAM writer
       [B]product: CD/DVDW SH-S182D
       vendor: TSSTcorp[/B]
       physical id: 0.0.0
       **bus info: scsi@3:0.0.0**
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       **version: SB06**
       [B]capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```[/B]

Any ideas what's happening here?

---

### Post by Hippman on 2010-05-03
Same problem here.
DVD-Drive disappears after some hours with Ubuntu 10.04LTS.
With WindowsXP no problem.:confused:

Attached my DMesg output.

Can anyone solve the problem ?

---

### Post by meho_r on 2010-05-03
I noticed this too. Didn't happen on Karmic.

---

### Post by Hippman on 2010-05-03
@kwacka
I noticed that you have a TSSTcorp-Device too. I've got a SH-S202N.
What kind of Mainboard do you have ?
I've got a ASROCK 4CoreDual-VSTA with VIA PT-880 Chipset.
Maybe there is a problem with the IDE-Controller driver.

@meho_r 
What kind of Hardware do you have ?

Any ideas for the problem welcome.:D

---

### Post by meho_r on 2010-05-04
Hl-dt-st dvdram gsa-4167b

No idea why. And, it doesn't happen regularly on my machine. I noticed this morning that DVD was just unmounted, not gone :?

---

### Post by kwacka on 2010-05-04
> **Hippman said:**
> @kwacka
I noticed that you have a TSSTcorp-Device too. I've got a SH-S202N.
What kind of Mainboard do you have ?
I've got a ASROCK 4CoreDual-VSTA with VIA PT-880 Chipset.
Maybe there is a problem with the IDE-Controller driver.

@meho_r 
What kind of Hardware do you have ?

Any ideas for the problem welcome.:D

MSI motherboard with VIA VT82C586 controllers.

My dmesg regarding this is identical to yours, but the entry immediately before it is regarding insertion of a memory stick - is it possible that this 'bumped' the entry for /dev/sr0? I don't see how (or why) but I'll be checking it out over the next day or so.

---

### Post by kwacka on 2010-05-04
Also showing up in dmesg is:

VFS: busy inodes on changed media or resized disk sr0

Searching I found that there have been entries in launchpad about this (looked before but didn't find it) with suggestions

1. comment out the Cd line in /etc/fstab (I only made an entry there because this was happening without a CD entry in fstab,

2. a. sudo eject, (no entries in dmesg, tray did not open)
   b. use button to return tray, 
   c. followed by cd eject -t (which gave the error: eject: CD-ROM tray close command failed: Input/output error)

Unfortunately not convenient to reboot computer, I'll try again tomorrow.

---

### Post by cuberts on 2010-05-04
> **meho_r said:**
> I noticed this too. Didn't happen on Karmic.
I couldnt actually see that problem. If so many people see this problem then it might be a problem with Lucid Lynx, but if it is not then it is just probably that your DVD reader is not running very well.

---

### Post by kwacka on 2010-05-05
Appears to be this bug - (not a previous one I found in Launchpad):

[ LIBATA with PATA_VIA causes ATAPI PATA devices to hang with HPET enabled](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282536)



Seems to be a problem with VIA boards.

---

### Post by kwacka on 2010-05-07
One of the respondents to the lauchpad bug mentioned in my last post suggested that using (test) kernel 2.6.31 resolved the problem.

Today update manager upgraded to kernel 2.6.32, and my drive hasn't disappeared since the upgrade.

If its still there in 24 hours I'll mark this 'solved'.

---

### Post by Hippman on 2010-05-08
I tested the 2.6.34-rc6 Kernel and my drives still disappear. Also with the daily-build.:mad:

---

### Post by kwacka on 2010-05-10
Sadly, still drives are disappearing.

---

### Post by Hippman on 2010-06-13
The workaround is 'noapic' parameter to kernel cmdline.
That worked for me. I've found that in launchpad 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544548](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544548)

So I've edited grub:
```
sudo gedit /etc/default/grub
```with noapic:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```finally:
```
sudo update-grub
```

---

