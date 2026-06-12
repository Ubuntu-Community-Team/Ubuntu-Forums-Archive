---
title: "Installing Ubuntu 9.10 on separate partition on SATA - dual boot with XP"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Nermi on 2010-02-15
I am trying to install Ubuntu 9.10  on SATA HD that is configured as RAID. Basically, I have two SATA drives but the second one is mirroring the first to protect me from single drive failure.  My goal is to install Ubuntu on a separate partition and create dual boot with XP that is already installed.

During installation, the partitioner gives me two options: erase entire disk, or create new partition. Of course I chose to create new partition, which leads me to "manual" setup.  When I click forward, two devices are listed:

/dev/mapper/isw_iijeagcj_Volume0 (Type, Mount Point, Size, Used ...... all blank) and
/dev/mapper/isw_iijeagcj_Volume1 (Type: NTFS, Mount Point: blank, Size: 500GB, Used: unknown)

There are few buttons at the bottom of the page. "New Partition Table" and "Add" are not available.

"Change" is available, if I click that, there is another popup "Use as", "Format Partition" and "Mount Point". I only know that "Use as" should be set to Ext4, and I supposed "Format" should be checked, but what is the "Mount Point"? Here are options:
/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

All I wanted was to resize the XP partition and install Ubuntu on freed space.

Besides, I expected to see something like hd0 and not "dev/mapper" which I don't think is physical drive?

They didn't exactly make it easy for a beginner. I have no idea how to proceed.

Please, help.

Thanks.

---

### Post by Pernig on 2010-02-15
"/" is the root file system. From a Windows user's point of view, you could look at it as Ubuntu's equivalent of "C:\". So you'll be wanting to mount your ext4 partition as / if that's where you want to install Ubuntu.

Using / as the mount point is the bare minimum. The places you listed will be mounted inside the root file system, but they are listed in case you want to make a seperate partition for say your home directory for instance, where your personal settings and the things you download will go.

---

### Post by Pernig on 2010-02-15
Also dev/mapper is what appears if you have a RAID setup; hd0 and hd1 are still there but are reserved for the drives themselves I think. You won't need to use them.

---

### Post by Nermi on 2010-02-15
Ok, I understand that. 
But why is this /dev/mapper... listed there? I think it is not a physical drive? I expected to see something like hd0 .

---

### Post by Nermi on 2010-02-15
Sorry, I guess you typed your reply while I was typing mine LOL... 

ok let me think a little...

---

