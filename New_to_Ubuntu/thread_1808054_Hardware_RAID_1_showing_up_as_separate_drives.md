---
title: "Hardware RAID 1 showing up as separate drives"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by imhotep531 on 2011-07-19
I've just installed this SATA RAID controller card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815124027](http://www.newegg.com/Product/Product.aspx?Item=N82E16815124027)

I booted the BIOS for the card successfully and created a RAID 1 using two 500GB SATA II drives.  When I boot a live CD of Ubuntu 10.04.2 LTS and open GParted both drives are visible separately instead of as a single volume.

I bought this card because some of the reviews said it 'just worked' with Ubuntu.  Right now I want to get hardware RAID up and running and I'll only look at mdadm as a last resort.  Nothing against it, but I want hardware RAID and this should be working.

Idaes?

---

### Post by imhotep531 on 2011-07-19
Well, now that I read more carefully, I realize the reviews on Newegg don't specifically mention RAID being recognized in Ubuntu.  Rather the reviewers are saying individual drives appeared with no troubles.  That part is true for me, I just plugged in the card and both drives were there.

I guess I jumped the gun.  If there's not a way for Ubuntu to recognize the RAID 1 volume off this card then I'll resign myself to mdadm.

---

### Post by imhotep531 on 2011-07-19
...ok maybe not!  I found another thread which led me to check the Disk Utility.  Under Peripheral Devices it only lists two drives:

80GB WD
500GB Maxtor

Above that it still shows three drives (1x80GB and 2x500GB) on the SATA and PATA host adapters.

So...does this mean Ubuntu recognizes the RAID 1 ???

---

### Post by Roasted on 2011-07-20
What's your device ID? I've noticed hardware RAID tends to name drives weird, as opposed to /dev/sda, etc.

For example, at work my one server named my drive /dev/cpspsp01110 or something like that.

In terminal, run:

```
sudo fdisk -l
```

Then post back here.

Note - that's an -L "ell"

---

### Post by imhotep531 on 2011-07-20
I apologize in advance for this whopper of a post...

Hopefully this is just as good.  The results of running 'sudo dmraid -r'

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: sil, "sil_bhahdcaifbbj", mirror, ok, 976771120 sectors, data@ 0
/dev/sdb: sil, "sil_bhahdcaifbbj", mirror, ok, 976771120 sectors, data@ 0
/dev/sda: nvidia, "nvidia_afgceafe", mirror, ok, 156301486 sectors, data@ 0

FYI, in GParted it shows my 80GB HD as /dev/sda, and each 500GB HD as /sdb and /sdc respectively.  So I interpret the output of 'dmraid -r' to say the following things:

1. Two different chipsets are detected for /dev/sda and Ubuntu is deferring to the nVidia chipset.  I don't understand this because this drive is NOT plugged into the RAID controller card.  It is plugged directly into the mobo which is where the nViidia chipset resides.  I don't understand why the sil chipset would be discovered on this drive too.  Am I misunderstanding?

2. Both /sdc and /sdb are given the same name of "sil_bhahdcaifbbi", so Ubuntu considers this a single logical volume.  Correct?

Right now I'm fairly baffled by the Disk Utility in Ubuntu.  It lists each HD separately under SATA and PATA, but then below that under 'Peripheral Devices' it shows only two drives, the 80GB and a single 500GB which I took to be a good sign that my RAID 1 array is recognized.  BUT when I try to partition or format either volume under 'Peripheral Devices' I get an error about the device being in use.  So I tried partitioning the 80GB drive in GParted and it worked.  I was able to split it into two unformatted partitions.  Now when I go back into Disk Utility it has added each partition under 'Peripheral Devices' AND it still shows the 80GB drive!?  That's really weird to me because the 80GB was split into two....

Sorry for the bombshell of questions.  Once I wrap my brain around how these utilities work I'll be all set.  Thanks again for your help.

---

### Post by Roasted on 2011-07-20
Well, at home in GParted it shows my system as having individual drives as well as RAID drives. However, that's via mdadm's software raid, so it may be different from what you are doing.

But for me, I have 3 drives. a 250gb drive for Windows 7 and Ubuntu's root, then a pair of terabyte drives in RAID1 via mdadm. I see:

/dev/sda
/dev/sdb
/dev/sdc
/dev/md0

sda = W7/Ubuntu
sdb = RAID 1 Drive A
sdc = RAID 1 Drive B
md0 = My actual array.

I have md0 mount my home directory, so when I write data, it goes to md0, which respectively gets tossed to sdb and sdc as they are members of the RAID family.

HOWEVER - that's software RAID. I'm not entirely sure I know what you are seeing, and on top of that I won't be able to get to the other building today where my server is to check, which is the only system with Ubuntu I have access to with hardware RAID. I'm just trying to let you know that even in software RAID, I see the individual drives. The key is to work with /dev/md0, which is the RAID device for me, and leave sdb and sdc alone.

But again, that's software RAID. Things may be very different between our setups.

I wonder.... I wonder if "cat /proc/mdstat" works for hardware RAID or if that's just for software RAID? That command gives me an output to see who's a member of the array and what drives are active... Just a thought, but I'm not sure it pertains to hardware...

---

### Post by imhotep531 on 2011-07-20
I'd like to do a test by placing a very large file on the RAID volume, then checking in GParted to see if both individual drives show the same amount of used space afterward.

You mentioned mounting drives to home and such.  I'm fairly ignorant so is there anything special I need to know in order to do the test, or is it as simple as copying say 1GB worth of data from a flash drive onto the RAID volume using the Ubuntu equivalent of Windows Explorer?

---

### Post by imhotep531 on 2011-07-20
Nevermind, apparently I don't even have true hardware RAID.  I didn't realize there's very little difference between what my controller card is actually providing (fakeRAID) and the software RAID built into Ubuntu.  Both require the CPU to do all the work.  Meh.

So I'm abandoning any further obsessing over whether Ubuntu sees the fakeRAIDed volume on my controller card.  I'm going to use mdadm and get on with the bigger project.

---

