---
title: "Grub Error 18 on Dell XPS M170 Laptop"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by kkritsilas on 2009-03-31
Hi,

I am attempting to set up a dual boot system. The hardware is a Dell XPS M170, 2.0GHZ P4M, 2GB RAM, nVidia 6800 Ultra w/256MB frame buffer, and the hard drive has been upgraded to a 250GB WD Caviar Blue, Dell Bios version A05. I partitioned the hard drive with 60GB for Ubuntu at the end, and the remaineder is Vista Home Premium, which is running just fine, and has for a while.

The machine does run the live CD, version 8.04 without any problems (video looks fine, wireless is fine, no issues with the touch pad or DVD). I tried to do the install from the little install icon that appears on the Live CD desktop. Install went well, but now the computer won't boot. I'm getting a Grub Error 18. Doing some research, the problem appears to be related to the lack of BIOS support for drives of over 137GB (that what the BIOS sees when I look at the entry for the hard drive). 

1. Is there any way around this? I have tried the GAG bootloader, and it doesn't seem to help. Is there any other boot loader that will get issue resolved for me, whether freeware or commercial? I would like to keep the Vista Home Premium on the machine as a dual boot (i.e. I won't turn the entire machine over to Ubuntu, at least not yet).

2. If I can eventually get the machine to dual boot, is it worth staying with 8.04, or should I go to 8.10 or even 9.04?

My backgroudn is with Windows and Mac, and a very small amount with Solaris.

Kostas

---

### Post by cariboo on 2009-04-01
Follow this [thread=224351] howto[/thread] to fix grub.

Jim

---

### Post by kkritsilas on 2009-04-01
> **cariboo907 said:**
> Follow this [thread=224351] howto[/thread] to fix grub.

Jim

Jim,

Thanks for taking the time to forward this, and I'm sure that somewhere along the line, I will need it. The problem I am having is not with Grub installing; it installs and runs, but at step 1.5, it stops with an error 18. From what I have been able to find, error 18 is caused by the drive not being completely supported by the BIOS, which in this case is correct. When I enter the BIOS, it reads the drive as a 137GB drive, when it is actually a 232GB (sold as a 250GB) hard drive. As Grub relies on the BIOS to determine the drive size, and the drive size in the BIOS is not correct, the Error 18 results. Windows (XP and onwards, I don't know about NT and 2000) do NOT rely on BIOS support for the hard drive, so Vista has no issue seeing the full 232GB (around 170GB with 60GB Ubuntu partition I created). I am using the lastest Dell BIOS for the system (release A05). 

Kostas

---

### Post by mikechant on 2009-04-02
One thing that's worth checking is the BIOS setting for the hard drive mode. If it's not set to LBA, try changing it to LBA.

If you can't get change your BIOS settings so the area > 137Gb is visible then you probably need to have your Linux partitions within this area. You could give your windows setup a C: drive at the beginning of the disk with <20Gb, then have your Linux partitions next, then another windows partition for your D: drive.

or:
You could avoid the grub problem by booting Linux from the Vista boot loader, using something like EasyBCD to configure a Linux boot option in Vista. You'd have to restore the Vista mbr - not my specialist subject but this looks helpful:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

This would probably allow you to start the boot process sucessfully but I imagine it would just fail at a later stage because the Linux partitions are still > 137Gb

---

### Post by kkritsilas on 2009-04-02
Mikechant:

Thanks for explaining that. I do have a point that I would like to have clarified, which is:

Do I need to have the ENTIRE ubuntu partition within the first 137GB, or would I just need to have the ubuntu partition starte somewhere below the 137GB limit? 

In the first case, I would need to shrink the Windows Vista partition down to (ball park figure) 77GB, then the Ubuntu partition of 60GB, and the remaining disk space also Windows Vista. In the second case, I would split the drive evenly, with the first 116GB or so of Vista, and the remaining 116 GB for Ubuntu. I can live with 116GB for Vista; the machine is used for experimenting on, and loaning out,  not much user data on it at all. The second case appears cleaner to me, but if it doesn't work, no use trying it.

Kostas

---

### Post by meierfra. on 2009-04-02
If you don't want to put the whole Ubuntu partition inside the 137GB limits, you need to create  a separate boot partition. The boot partition should be a primary ext3 partition of size  about 200MB and mount point /boot, and needs to be completely inside the 137GB.  The main Ubuntu partition then can be anywhere you want to.

---

### Post by kkritsilas on 2009-04-03
Maybe there is something I don't understand, or perhaps just displaying my newness/ignorance, but If I need a 200MB boot partition within the 137GB limit, wouldn't splitting the drive into 2 116GB (116 GB for Vista, and 116GB for Ubuntu) partitions accomplish the same thing? If the required 200MB boot partition is in the first 200MB of the 116GB Ubuntu partition, would this work? If so, isn't that the way Ubuntu normally sets itself up?

I'm beginning to think that I screwed up the initial install attempt by placing the Ubuntu partition entirely after the 127GB limit, but as I am still really new at this, there are probably more things going on than I understand.

Kostas

---

### Post by meierfra. on 2009-04-03
> if the required 200MB boot partition is in the first 200MB of the 116GB Ubuntu partition, would this work? 

No.  If you don't have a separate boot partition, the boot files might end up anywhere  on the Ubuntu partition.  (I even have seen cases  where original everything worked out ok, but after a kernel update the new kernel was outside the 137 GB limit)

So instead of splitting  the drive 116 GB/116 GB just split it 116 GB/200MB/116 GB.

---

### Post by kkritsilas on 2009-04-04
> **meierfra. said:**
> No.  If you don't have a separate boot partition, the boot files might end up anywhere  on the Ubuntu partition.  (I even have seen cases  where original everything worked out ok, but after a kernel update the new kernel was outside the 137 GB limit)

So instead of splitting  the drive 116 GB/116 GB just split it 116 GB/200MB/116 GB.

Meierfra:

Thanks, that does explain things a little better. 

To do this partitioning, do I use the partition editor that comes with the Ubuntu CD (in manual mode, I guess), or do I need to create the partitions using the admin tools in Vista?

Is there an idiot's guide to using the Ubuntu partitioning tool? I have looked at it a few times, and I don't find it very intuitive (probably due to my Windows/Mac background). I know that I can use guided mode to create a 116GB Ubuntu partition, and that works no problem, but I can't seem to use the guided mode to create two partitions (Vista of lets say 60GB, a 60GB Ubuntu partition to stay below the 137GB limit, and the remainder (112GB) as another Windows Vista Partition). I'm not stuck to the actual sizes, they were just examples.

Is 60GB enough space for Ubuntu for lets say the next year or so? I don't have a feel for how big a complete Ubuntu install is, and how many/how ofter/how big the updates and patches are (this is all new to me).

Kostas

---

### Post by meierfra. on 2009-04-04
> but I can't seem to use the guided mode to create two partitions (Vista of lets say 60GB, a 60GB Ubuntu partition to stay below the 137GB limit
I recommend to create all the partitions before hand and then use "manual" during the install.


I would shrink the vista  partition with the Vista Disk management:

[http://www.bleepingcomputer.com/tutorials/tutorial133.html](http://www.bleepingcomputer.com/tutorials/tutorial133.html)


Sometimes the Vista Disk Management won't let you shrink the partition by very much and you will have to use gparted. But using gparted can lead to booting problems:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

If you use the gparted to shrink vista make sure to uncheck the "round to cylinder"  box.
 

To create boot partition and the Ubuntu "/" partition I would use gparted: 

[http://www.bleepingcomputer.com/tutorials/index.php?act=print&tut=152&client=printer](http://www.bleepingcomputer.com/tutorials/index.php?act=print&tut=152&client=printer)

(If you don't like the tutorials I linked, just google and you'll find others)

Actually instead of creating a separate boot partition, you could create a separate Home partition:

```

Vista    Ubuntu "/"   Home   Share   Swap
116GB       20 GB     40     54       2GB
```


Ubuntu "/"  should be a primary partition of type ext3.
Home should be logical partition of type ext3
Share should be logical partition of type ntfs
Swap  a logical partition of type Swap

Before you can create  the logical partition, you will have to create a extended partition  of size 40+54+2=96
The logical partition are then created inside the extendend partition

You can adjust the numbers to your liking, just make sure that Ubuntu stays inside the 137 GB limits



> Is 60GB enough space for Ubuntu for lets say the next year or so?
Yes 60GB should be plenty. If you have a separate Home partition, 20GB is plenty of big for the Ubuntu "/" partition.  (People usually recommend somewhere between 5-20)
The only things which really use up space is music, videos and games.  And you can always keep was on an shared ntfs partition if you prefer.

> Vista of lets say 60GB
Trying to shrink Vista to 60GB with the Vista disk management probably won't work.

---

### Post by kkritsilas on 2009-04-06
Hi,

I just wanted to update my progress so far.

I have managed to shrink the Vista Partition down to 76GB (Vista drive C: ). I have also been able to create an additional 2 partitions, a 58GB partition that I intend to put Ubuntu into, and a second 95 GB Vista partition (Drive D: to the Vista system).

I used the home version of EASEUS Partition Master 3.5, which is free, and works well for this purpose. I used it from within Vista. After the partition was shrunk down to 76GB, I rebooted the system multiple times to verify that all was well, and Vista booted up fine every time. My system is running Vista 32 Bit (I don't think my processor can run the 64 Bit version of Vista, and seeing as it only maxes out at 2GB of RAM, that is probably for the best). Next step is for me to create the "/", "Home", and "Swap" partitions using gparted. I intend to allocate them out of the 58GB Ubuntu partition that I have already allocated. 

Does this sound reasonable?

Kostas

---

### Post by meierfra. on 2009-04-07
> Does this sound reasonable?

It does.

---

### Post by meierfra. on 2009-04-07
Just as a reminder. The Ubuntu "/" partition should be primary (in some rare case "Grub error 18" can be caused  by logical "/"-partition).  Since you can have only 4 primary partitions, you will have to create an extended partition and  then create logical partitions for "home" and "swap" inside the extended partitions.

---

### Post by kkritsilas on 2009-04-13
Last Update:

I have installed Ubuntu 8.04 in a dual boot confirguration, and can dual boot into both Vista and Ubuntu.

I ended up needing to download and burn a copy of the gparted live CD, which allowed me to make the Ubuntu partition a primary, and I then used the partitioning program in the Ubunutu installer in manual mode to create the logical partitions inside the primary partition.

Thanks go to meierfra for all the help with the partitioning information.

I have a number of issues that I will need to address, from wireless networking stopping after I did the updates (all 361 of them) to trying to get Grub to default to Vista (and it needs a cleaning out of some entries), but a lot of them I can work out on my own, I hope.

Kostas

P.S. Initial impression is that Ubuntu is pretty snappy, right around Windows XP Pro speed, meaning noticeably faster than Vista Home Premium.

---

### Post by kkritsilas on 2009-04-16
Postmortem:

I figured out, just by poking around, that the network issue was created by turning off the roaming on the Network application. As soon as that was turned on, and the system rebooted, I was able to see the local networks, and connect. I have Internet access and I am able to print on my laser printer using the wireless interface. I'm pretty sure that I screwed that up, but it may have been related to the upgrades as well. 

After that started working, I was able to download the nVidia driver for my 6800 Ultra chip, and enable the Extra setting on the Appearance Preferences. Rebooted again, and a nice increase in both video speed, as well as very impressive eye-candy.

Thanks again to all for the help.

Kostas

---

