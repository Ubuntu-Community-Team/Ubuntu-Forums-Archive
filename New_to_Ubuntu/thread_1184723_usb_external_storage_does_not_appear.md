---
title: "usb external storage does not appear"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-06-11
*edit:  I had to use html br tags to separate paragraphs, a format that is requested in the forum guidelines.* 

When I plug in a usb device (e.g. mp3 player, external hard drive), it is hit or miss.  Sometimes, I get a dialog box that pops up, and a new icon in the right menu (the menu that shows some common folders like Home and Desktop) showing the usb-connected storage.  Sometimes, I get nothing.  In the cases when I get nothing, is there something that I can do to go from nothing to something (e.g. a command that I can issue)? 

I'm not afraid of the command line, but I do like to understand the commands that I issue, especially when I issue them with sudo.



Machine: 
EeePC 900 (the one that comes with 16 GB solid state drive and Windows XP)

OS: 
Easy Peasy 1.1 (allegedly Ubuntu Hardy Heron 8.04.1, i.e. with Netbook Remix GUI)  I suppose I should note that Synaptic indicates version 1.0 of easypeasy rather than 1.1.  Also, I don't remember where (i.e. in which menu) I saw this, but I got a strong impression that the version of Ubuntu is actually 8.10 (Intrepid Ibix), but I don't know if any of that stuff matters.

Background story: 
I am *quite* accustomed to Microsoft Windows (98, and then XP, but *never* Vista).  However, I am forced to use Linux for work (well, for school/research).  I recently got an Eee PC and decided to do a clean install of Easy Peasy (I think that's the terminology:  I installed Easy Peasy with the intention of totally wiping out whatever 1's and 0's happened to be on the ssd by repartitioning/reformatting, thus starting from scratch).  I am actually running my fourth installation of Easy Peasy; apparently I have a knack for breaking it to the point that I figure it is just easier to reistall.  I hope that is not too bad for my hardware.  Anyway, I think that I now have Easy Peasy running OK (notwithstanding my newly developed apprehension for unwittingly issuing a key sequence that works for Windows but apparently wreaks havoc on Easy Peasy).  I installed (four times now) from a flash drive.  I created my Easy Peasy installation flash drive in Windows XP by formatting a 1 GB Verbatim flash drive as FAT, downloading the .iso image from the Easy Peasy website (well, sourceforge actually), and using the unetbootin utility (that I got - somewhere) to make the flash drive bootable and simulateously transfer the .iso image file to it.  If I have opened my mouth and removed all doubt in your mind (that I have no clue what I'm doing to my poor computer), then your assessment is correct.

---

### Post by blueridgedog on 2009-06-12
When you plug in a USB drive and nothing happens, you can look at (and post) the recent (at the end) entries in 

```
dmesg
```

You can also look at (and post) the output of

```
sudo fdisk -l
```

From there you can see the /dev/XXX id assigned to the drive/device and mount it by hand.

To mount it by hand you would

```
mount /dev/XXX1 /path/to/mount/point
```

An example that I use would be:

```
sudo mount /dev/sdc1 /mnt/Backups
```

The key is in using the first commands to identify what id (sdc) for example has been assigned to the media, so you can mount the first partition (sdc1) of the media where you want.  Other partitions can be mounted by referencing them as sdc2...etc.

---

### Post by MichaelBurns on 2009-06-13
Thanks for the suggestion.  Unfortunately, I do not see a corresponding /dev/sd# from the output of "fdisk -l".
```

Disk /dev/sda: 16.1 GB, 16139681792 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x589bb5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         996     8000338+  83  Linux
/dev/sda2             997        1962     7759395    5  Extended
/dev/sda5             997        1962     7759363+  83  Linux

Disk /dev/sdb: 8065 MB, 8065646080 bytes
8 heads, 32 sectors/track, 61535 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       61536     7876591+   b  W95 FAT32

Disk /dev/sdc: 4098 MB, 4098883584 bytes
127 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       98824      243796   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(98823, 58, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(243795, 59, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       21424      267300   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21423, 77, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(267299, 87, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      237476      483352   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(237475, 53, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(483351, 62, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      366483      366490       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(366482, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(366489, 36, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```
I connected three usb devices, one to each of the three usb ports.  One of them is an 8 GB flash drive, and it is sdb.  The other two are 4 GB mp3 players.  According to the file browser, the one that is mounted is the Sansa Clip.  However, the partition editor gives me a warning that whatever sdc is, it cannot be mounted (but it knows that the file system is fat32).  That's strange, because I can use the file manager to navigate it.  The Samsung YP-Z5 (a crappy mp3 player to begin with) is simply invisible so far.

[i]update:
I guess this is a bug?  When I connect only the Samsung mp3 player, it is mounted.  This works on each of the three usb ports.  Perhaps Easy Peasy (Ubuntu 8.40.1) cannot handle three usb devices simultaneously.  That could be a problem...[/i]

---

### Post by blueridgedog on 2009-06-13
Another reason for the issue is that your USB system may not have sufficient voltage to run that many devices that need power.  The two MP3 players start to charge when plugged in?  I suspect they have power needs that exceed the USB bus.  Try moving one of the players to the back.

---

### Post by MichaelBurns on 2009-06-13
> **blueridgedog said:**
> ... your USB system may not have sufficient voltage to run that many devices that need power.Why should the voltage depend on the number of usb devices?  If the voltage can go out of spec if I connect to all three usb ports, then the Eee PC is very poorly designed (and I will considering demanding a refund).  Do you mean that the power supply may not be able to supply enough current for all three usb devices?  How can I find out what is the current and voltage at each of the usb ports?

> **blueridgedog said:**
> Try moving one of the players to the back.What is "the back"?  The only connection I have on the back is the power jack.  There is one usb port on the left, and two on the right.  Is this some operating system terminology?

---

### Post by blueridgedog on 2009-06-13
Sorry...I didn't catch the make of the PC.  There are no back ports on your eee PC (I have one too).

I am not an electronics person, but imagine the power required to connect 100 mp3 players to charge off of your eee pc.  The pc would need a great deal of amperage to supply that demand.  Just because it has a certain number of USB ports doesn't mean that it can charge MP3 plays or other high amperage devices in all of them simultaneously.  I wouldn't consider it a defect.  The hallmark of the eee pc is its size and battery life, not the robustness of its power supply.

---

### Post by MichaelBurns on 2009-06-14
Well, I managed to get Ubuntu to show me all three of the usb devices.  I don't think that this was an issue of current draw, since I hadn't charged them up any more.  I just played with various combinations of the order in which I connected the devices, and which device was connected to which port.  Another reason that I don't think that the current draw is the issue trying to connect an older harddrive with a usb-to-ide adapter that is externally powered.

> **blueridgedog said:**
> The hallmark of the eee pc is its size and battery life, ...I don't think that (avg) 2 1/2 hours of battery life is very remarkable.  But that's not an Ubuntu issue; I'm pretty sure that's a hardware issue.  In fact, from what I can determine, Ubuntu gives me an extra 30 minutes or so of battery life compared to when I was running Windows XP on it for the first few battery cycles.  But perhaps that is just due to battery excercise.

---

### Post by blueridgedog on 2009-06-14
I have the eee pc 1000 and get about six hours.

---

### Post by MichaelBurns on 2009-06-15
> **blueridgedog said:**
> I have the eee pc 1000 and get about six hours.Yes, I've heard that.  People should be made aware of this difference.  Why ASUS ever even thought about making a model with only just over 2 hours of battery charge is a mystery to me.  But as a PSA, I take every reasonable opportunity to warn people:  It is up to you to make sure that the model that you buy has the battery charge that you expect.  I am not the only one who has this problem.  In fact, Wikipedia even has a section on the "battery controversy" (I didn't write it, BTW; unfortunately I found this wikipedia article after I made my purchase).

Caveat Emptor:  The Eee PC 900 gets a little over 2 hours of battery power.  And if you made the mistake of purchasing it at Best Buy, don't expect them to let you return it during the 14 day return period.  They will find an excuse.

I appologize if I have broken the forum policy in this post.  It is getting a bit off-topic, but I will post it anyway because I don't want others to make the same mistake that I made.

---

### Post by blueridgedog on 2009-06-15
I am sorry you have had a bad purchasing experience.  I generally have received great service from NewEgg and recommend them based the same.

---

