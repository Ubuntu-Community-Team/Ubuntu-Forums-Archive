---
title: "external hard disk drive not detected"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by rahul1975 on 2011-05-08
I have an Western Digital external hard disk , but its not getting detected in ubuntu aswell as in windows xp. The drive itself is not detected. Can anyone pls help me out.

---

### Post by powerpleb on 2011-05-08
> **rahul1975 said:**
> I have an Western Digital external hard disk , but its not getting detected in ubuntu aswell as in windows xp. The drive itself is not detected. Can anyone pls help me out.

USB right?

If so, first plug it in and open a terminal and type "lsusb". Let us know what is says.

---

### Post by rahul1975 on 2011-05-08
rahul@rahul-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 043: ID 13fd:160e Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by powerpleb on 2011-05-08
OK, looks like it is seeing it. 

First try moving it around to different USB ports on your PC. Sometimes particular ports don't provide enough power for USB powered hard drives.

If this doesn't work run "sudo fdisk -l" and see if you can see it. If you can see it, try mounting it manually by first creating the directory with "sudo mkdir /mnt/usb" then running "sudo mount /dev/sd?? /mnt/usb/".

---

### Post by Lateralis on 2011-05-08
Er, I'm not sure it is being detected...  

You said that the hard drive is not detected in Windows XP running on the same machine?  If not, try it on a second computer.  If it is detected on that computer, there then the hard drive works and the USB ports on your computer don't.  If the hard drive isn't detected on another computer then it is probably dead.

---

### Post by rahul1975 on 2011-05-08
Thank u for your answer powerpleb, but i tried sudo fdisk -l but it still not detected and i tried to mount in different usb port but still its not detected. But the light on hard disk is flickering that means its not dead as Lateralis says. Any chance of virus?.


rahul@rahul-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032062

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29165   234259456   83  Linux
/dev/sda2           29165       30402     9936897    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris
rahul@rahul-desktop:~$

---

### Post by Lateralis on 2011-05-08
I doubt its a virus, and I wouldn't be too mislead by the light on the drive.  The LED only means the drive has power but there's more to the hard drive than that.  This is one case where the phrase "the light's on but there's no one home" can be applied with some legitimacy.  

As I said, I think the best thing to do is attach the drive to a different computer.  If it isn't seen there then you are out of luck.  

If you don't have access to another computer then you could try entering the BIOS with the drive attached and seeing if the drive is listed in there.  If it is, then that is more promising.  If it isn't, then you really need to try hooking it up to a different PC.

---

### Post by powerpleb on 2011-05-08
The reason I thought it was detected is because of this:* 13fd:160e Initio Corporation *
I'm pretty sure it is a USB sata controller.

But anyway... A virus is doubtful, I don't think that would stop you from mounting it. And fdisk would most likely detect at least the drive, which it isn't.

Have you had it working before? On this machine? Have you tried other machines?

I ask this because if it isn't a problem with inadequate power, it sounds to me like the drive is dead. If it isn't showing up in fdisk than I don't know how you would be able to mount it.

---

### Post by Lateralis on 2011-05-08
Yeah, I saw that too, but a WD hard drive normally has something like this:

```

Bus 002 Device 006: ID 1058:0704 Western Digital Technologies, Inc.

```

This is from my WD passport HD, but other WD drives I've had give identical outputs.  

So yeah, my conclusion is the drive is dead as well, but to confirm that the OP needs to use a second machine as a sanity check.

---

### Post by rahul1975 on 2011-05-08
This time i started the machine  it showed me the 120 gb drive it was mounted on the desktop. I had inserted the usb in different port.But later on when i tried to open the folder inside the external drive the OS got hang so I restarted the machine to format the drive, but this time again it was not detected. I tried it on my friends pc there also it was not detected.

---

### Post by aviralvatsa on 2011-05-09
Hi I have been struggling with mounting an external drive. It had been working okay on Ubuntu for past one year and suddenly I can not see it anymore. Although I have upgraded to 11.04 but this problem I had from the earlier version. I have tried using other computers, windows xp, but no success. Changed the USB ports. THe drive runs when connected to the computer. I can hear the disk run but I cannot see it. Also tried looking through

here is what I see (The NTFS partitions are on this dual boot computer and are not really the external drive I am looking for. That drive is 500 gb. Also there is additional linux partition in addition to the one I am using).


sudo fdisk -lu
[sudo] password for**:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bbea9fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    61431807    30714880    7  HPFS/NTFS
/dev/sda2        61432621   625141759   281854569+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   130929749    34748563+   7  HPFS/NTFS
/dev/sda6       130929813   211495724    40282956   83  Linux
/dev/sda7       211495788   215030024     1767118+  82  Linux swap / Solaris
/dev/sda8       215031808   314595327    49781760   83  Linux
/dev/sda9       314597376   318500863     1951744   82  Linux swap / Solaris
/dev/sda10      318502912   625141759   153319424   83  Linux

---

