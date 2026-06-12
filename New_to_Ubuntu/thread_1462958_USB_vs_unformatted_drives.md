---
title: "USB vs unformatted drives"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by KirbySmith on 2010-04-26
I loaded two new unformatted SATA drives into a new StarTech.com JBOD four drive housing and used its USB 2 interface to connect to my computer running 9.10.  The drives aren't seen by gparted, or palimpsest or the directory viewer.  All of these work with partitions so maybe this should have been predictable.  Still, I know that the live CD can find an unformatted drive on IDE0.  Maybe where unformatted drives can be detected is a BIOS issue.  Anyway, assuming that this is not a Startech.com hardware issue, my questions are:

Is there ubuntu distribution software or some other software that is normally successful detecting and formating drives attached via USB?
If not, would the expected behavior of ubuntu distribution software or some other software allow formatting be performed via eSATA if I were to install a PCIe to eSATA card?

My goal is to not have to open my computer's case and hook up a new drive to a spare SATA port whenever I need to format a new drive for use in the JBOD housing.

Thanks

kirby

---

### Post by Kakers on 2010-04-26
You say you can't see them? It might just be they are not mounting because they are not formatted.

Do they show up when you type:
```
sudo fdisk -l
```

Personally I find I always get better support running the gparted live cd rather then the gparted program when booted into Ubuntu. Although the eSATA vs. USB shouldn't make too much difference the way of connectivity I would recommend it purely for the speed increase.

---

### Post by Penguin Guy on 2010-04-26
Since you're using hardware rather than software to control JBOD, your computer can't access the JBODed drives independently. You'll have to take them out of the JBOD controller and hook them up to a SATA port to format them. In my opinion, hardware controllers are generally for more industrial computers, whereas software controllers usually suffice (and are easier) for desktop PCs.

I'm no expert, sorry if I'm wrong about any of that.

---

### Post by KirbySmith on 2010-04-26
Kakers: 
[INDENT] Thanks for your quick response.

sudo fdisk -l shows only the drives that I otherwise see in the programs I listed.

I'll have to look into generating a gparted live cd.  I'll have to plead ignorance about it at this point.
[/INDENT]Penguin guy:  
[INDENT] Thank you also.  I will have to do as you suggest just to confirm (or not) that lack of formatting is the interface problem, if not the ultimate solution.
[/INDENT]------

I'll get back to this after an employment interlude.

kirby

---

### Post by KirbySmith on 2010-04-27
The following seems to be true.

GParted live cd won't work without (at a minimum) hacking its video settings because my nVidia card doesn't work with default settings with live cds.  Video hacking would have taken too long for today.

I used the GParted GUI available from System > Administration > GParted  to partition and format one of the drives from the housing when plugged into a spare internal SATA slot.  The drive became visible when remounted in the StarTech.com housing.  This is consistent with expected behavior reported by StarTech service after I inquired.

A second drive from that housing connected to the same SATA port would not partition, or be recognized.  Diving into the BIOS I could see that it recognized the drive model, but the auto detection function wasn't detecting any values.  Forcing it led to a hung, but recoverable with minimal work, BIOS.

Thus, I cannot confirm at this point that multiple drives in the StarTech housing will be visible once partitioned and formatted.

I have to get WD to repair/replace the drive, and buy some more to fully populate the housing.  Then I can test it fully.

I'll update this thread when I have more results.

kirby

---

### Post by KirbySmith on 2010-04-28
It seems that the USB drive is owned by root and I cannot paste any files into it.  While I'm sure that I could log into root and do it the hard way, I really need to change the permissions, something I haven't yet researched.

Suggestions/methods will be appreciated.

kirby

---

### Post by Penguin Guy on 2010-06-20
To get your USB owned by you:
[LIST=1]
[*]Find your USBs UUID and filesystem type:
[LIST=1]
[*]Run [FONT="Courier New"]sudo blkid[/FONT]:
```
# blkid
/dev/sda1: LABEL="Windows" UUID="5C1886B518868E28" TYPE="ntfs" 
/dev/sda2: LABEL="Ubuntu 10.04" UUID="4684ee8a-4467-4c7a-927c-45cbe51705d5" TYPE="ext4" 

```
[*]Plug in USB.
[*]Run sudo blkid again and find the UUID and TYPE of the new entry:
```
# blkid
/dev/sda1: LABEL="Windows" UUID="5C1886B518868E28" TYPE="ntfs" 
/dev/sda2: LABEL="Ubuntu 10.04" UUID="4684ee8a-4467-4c7a-927c-45cbe51705d5" TYPE="ext4" 
**/dev/sdb1: LABEL="PG-USB" UUID="_8b0dfb4d-c356-4c06-87f2-e869aa5afd92_" TYPE="_fat32_"**

```
[/LIST]
[*]Add an appropriate FSTab entry ([FONT="Courier New"]gksu gedit /etc/fstab[/FONT]) with the [FONT="Courier New"]umask=000[/FONT] option:
```

# <file system>   <mount point>   <type>   <options>   <dump>   <pass>
proc   /proc   proc   nodev,noexec,nosuid   0   0
UUID=4684ee8a-4467-4c7a-927c-45cbe51705d5   /   ext4 noatime,errors=remount-ro   0   1
**UUID=_8b0dfb4d-c356-4c06-87f2-e869aa5afd92_   /media/PG-USB   _fat32_   umask=000   0   0**

```
[/LIST]

---

### Post by KirbySmith on 2010-09-18
Belated thanks and apologies to Penguin Guy; I seem to have lost track of this thread.  I will mark the thread solved, but will have to defer testing his ownership solution for a while until I finish some PC building and disk cloning activities.

kirby

---

