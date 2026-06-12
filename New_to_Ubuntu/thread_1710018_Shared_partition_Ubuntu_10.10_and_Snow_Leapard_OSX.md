---
title: "Shared partition Ubuntu 10.10 and Snow Leapard OSX MBP 6,2"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by gizmonizmo on 2011-03-19
I'm using a MacBook Pro 6,2 currently running ubuntu 10.10 in VMware Fusion and am planning to do a dual boot with ubuntu and Snow Leapard 10.6.6. I also want to make a separate partition to be shared between OSX and Ubuntu.

I have two questions:
1 - How would I go about installing ubuntu by making a new partition for on my hard drive. 
2 - What would be the best format for the shared partition ( I may need to access it for windows, but I don't know how I would be able to do that because I don't want to do a tri-boot)
3 - I need guidance on how to set up the partitions for linux (ie. sda, ext3/4, swap; plus what to choose for "/", "/home", etc..)
4 - How would I know what hardware is compatible with my MacBook Pro using the liveCD?

Any help is appreciated. :)

-gizmo

---

### Post by iMarck90 on 2011-03-19
You can use the guide here **[Click]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")**
Is like working everything with some command **[https://help.ubuntu.com/community/MacBookPro6-2/Maverick]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick")**
You can use the first guide to partition your hardrive or just use the Bootcamp or DiskUtility.
It like also Ubuntu 10.4 LTS working with your hardware but need some step **[https://help.ubuntu.com/community/MacBookPro6-2/Lucid]("https://help.ubuntu.com/community/MacBookPro6-2/Lucid")**
Remember to install REFIT and boot from it to install Ubuntu.

Sorry for bad english.

---

### Post by stmiller on 2011-03-19
Format the partition HFS (non-journaled) in OS X with disk utility. (Make sure you choose non journaled!)

Linux and OS X can read / write to this without issue.

In Ubuntu, you may have to install:

```

sudo apt-get install hfsplus hfsutils

```

There are some third party apps for Windows to read hfs (hfs explorer?).

---

