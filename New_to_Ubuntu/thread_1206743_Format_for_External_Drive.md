---
title: "Format for External Drive?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by tomreid on 2009-07-07
Hi

I have a LACIE USB external drive that I previously used with various Macs. I don't need the data on it, so I can re-format it. 

At the moment Ubuntu will read from it, but not write to it. 

I think this may be a format issue. 

How do I reformat it, so I can use it freely to read and write with on my Ubuntu machines and maybe the Macs too?

cheers

---

### Post by LowSky on 2009-07-07
in the repos is a program called gparted


sudo apt-get install gparted


it will install and be named _partition editor_ under System > admin  for GOD knows why?

---

### Post by laidback on 2009-07-07
It'll ask you for your password when you run it. I'd use ext3 format.

---

### Post by green0eggs on 2009-07-07
> **tomreid said:**
> 
At the moment Ubuntu will read from it, but not write to it. 


It's not necessarily a format issue. I am not sure what file system Mac uses but if it's NTFS (like Windows) it may just be a case of downloading a package that enables support.

For NTFS the package you want is ntfsprogs which you will find in the package manager...
[INDENT]Administration > Synaptic Package Manager[/INDENT]

gparted is a useful tool to have anyway, especially if you are not sure what file system your external hd is formatted to, you will be able to find out: 

[INDENT]Select the hard disk from the drop down menu in the top right hand side of gparted's GUI... you should see the external drive with partitions (if any) surrounded by a coloured border corresponding to a file format.
[/INDENT]

If I were you I'd try searching for a package to enable support for your file system before reformatting the hd unless you really don't care and are unlikely to want to use your external with a Mac ever.

Hope this helped.

---

### Post by LewRockwell on 2009-07-07
It's probably formatted HFS+ and so I'd just scrub it and reformat it

You might want to use this opportunity to try out a neat utilities disk called Parted Magic([http://www.partedmagic.com/](http://www.partedmagic.com/))

It is a LiveCD that has Firefox and internet/network capabilities

It also has Gparted for partitioning, clonezilla for cloning, and an erase disk function that can deploy several ways, including with the hard drive's control-board level secure erase function that has been a drive spec since approximately 2001

For more information on secure erasing hard drives:

[http://ubuntuforums.org/showthread.php?t=1204949](http://ubuntuforums.org/showthread.php?t=1204949)

.

---

### Post by tomreid on 2009-07-07
Interesting. 

I agree with trying to fix the permissions on the disk before going as far as re-formatting it, but when I run GP Parted, it shows up like a blank disk, see attached screenshot. But when I look at the disks contents in Nautilus I can see it is mostly full and I can read all the files.

cheers

---

### Post by Volt9000 on 2009-07-07
Wow, weird... Nautilus can read it but gparted can't.

Post the output of

```

sudo fdisk -l

```

Those last two characters are a hyphen and a lowercase letter "L".

This will show us what partitions reside on this drive.

[edit]
Just a thought-- are you sure you have the right drive selected? ;)
In the top-right corner of gparted you can choose your device. Are you sure that /dev/sdd is the drive in question?

---

### Post by louieb on 2009-07-07
Apple uses its own partition table type [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 

Don't know if Gparted can deal with it. Might want to look at changing it to an msdos partition table. In Gparted under Device>Set disk - you can write a new partition table. - Warning doing that will delete all the partitions currently on the drive. Make sure you want too and that the right drive is changed.

---

### Post by tomreid on 2009-07-07
Hi all - thanks for all your help.

After some considerable experimentation, I have successfully re-formatted the drive to ext3.

I think I have a simple permissions problem now though. 

The drive is owned by "root" and not me, so I can' write to it. How do I configure it so I own it? The "permissions" options are grayed out in Nautilus.

cheers

---

### Post by Volt9000 on 2009-07-07
Run Nautilus with root permissions with

```

gksu nautilus

```

You will be asked for your account password. When you enter it, Nautilus will appear to run as normal but now you can change ownership and permissions.

---

### Post by tomreid on 2009-07-08
Many thanks, that worked fine.

cheers

---

