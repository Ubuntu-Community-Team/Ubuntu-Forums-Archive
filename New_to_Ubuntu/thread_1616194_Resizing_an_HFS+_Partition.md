---
title: "Resizing an HFS+ Partition"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by nosh276 on 2010-11-07
I've been looking for days and trying various things. I've tried claiming ownership--which doesn't work, of course. I've tried disabling journaling, but I can't get the diskutil command to work at all.

Using the gui DiskUtility and GParted, even though I've installed (through synaptic) the HFS support packages, I can't get it to work.

I don't want to resize the partition. I want to be able to write to my mac formatted external from my Ubuntu laptop. However, I figured if I could resize the partition and create a new, linux compatible, partition, I could just copy the files over and then, eventually, just get rid of the HFS+ partition.

I can't seem to find anything that solves the problem though. I can't seem to resize, or gain write abilities on the drive.

Thanks

---

### Post by bioterror on 2010-11-07
Hmmm... [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu")

Gives this kind of option in OS X:
> 
At this point, we are really just allocating the space you want for Ubuntu. The actual Linux partitions will be created later during the installation.

For pre-Leopard OS X, there are no such tools. BootCamp does not run, and DiskUtility will only allow you to create more partitions if you wipe out all the current partitions. However, the underlying commandline utility still exists.

Here's a usage example. Let’s say you want to resize your OS X partition to 200GB and leave the rest of the disk free (for Ubuntu of course). You would open a terminal and type the following, followed by the "Return" key.

```
sudo diskutil resizeVolume disk0s2 200G

```

You can read more on diskutil by typing 'diskutil help' in your OS X terminal.


---

