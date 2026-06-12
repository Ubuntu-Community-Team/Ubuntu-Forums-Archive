---
title: "How to avoid entering a password for HD access"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by ianp5a on 2010-01-17
In 9.10 in the File Manager, if I click on any Hard Disk other than the one where Ubuntu is installed I'm asked for my Password the first time after logging in.
The Pop up says "Authentification is required to mount a device."

How can I avoid having to do this. As it is unnecessary.

Thanks

---

### Post by Morbius1 on 2010-01-17
Have it automount at boot. It would require you to edit /etc/fstab.

Post the output of the following commands and tell us which partition(s) you want to mount :

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

---

### Post by anantshri on 2010-01-17
if its ntfs or fat32 file format all i needed to do was to install ntfs mount tools and it did all my config work hence removing the need of having a separate editing of files.

will post the link from where i got that tool as soon as i get some time to check

---

### Post by Gone fishing on 2010-01-17
Add the drive to fstab

sudo gedit /etc/fstab

my added bit looks like:

```
# Added by John /dev/sda8: UUID="2E72A2E172A2ACD1" LABEL="Storage" TYPE="ntfs"
UUID=2E72A2E172A2ACD1 /media/storage      ntfs    defaults,nls=utf8 0       0
# Added by John /dev/sdb1: UUID="78ECEFF7ECEFAE16" LABEL="Personal" TYPE="ntfs"
UUID=78ECEFF7ECEFAE16 /media/personal      ntfs    defaults,nls=utf8 0       0 
```

to find the UUID use this command

```
sudo blkid -c /dev/null
```

Sorry you also need to add the mount points in my case

sudo mkdir /media/storage and sudo mkdir /media/personal

---

### Post by ianp5a on 2010-01-17
> **anantshri said:**
> if its ntfs or fat32 file format all i needed to do was to install ntfs mount tools and it did all my config work hence removing the need of having a separate editing of files.

Thanks. With your tip I found NTFS Tools and Mount Manager in the Software Centre.
And you are right, it does save the need to mess around in text files and folders. And a lot safer too.

I used **Mount Manager** which did it all for me and showed me a whole load of other options too that I would not have discovered with a text file.

Thanks to all the others who suggested typing things in a Terminal or text files. Now if anybody else in the Beginners area asks about this, be sure to tell them the easy way.

---

### Post by alpha-buntu on 2010-01-17
there is also the "storage device manager", which I found easier to understand and use for newbies.

---

### Post by ianp5a on 2010-01-17
Thanks. Very Useful. I think it's "Assistant" is the way to set the settings. However I think that the Mount Manager gives a better overview of the drives and their settings. But it's nice to know that there are several tools to help us.
Personally, though, I would have preferred these settings right in the File Manager (Nautilus). As I would expect to right click a disk, choose properties, and make *all* my settings there. But maybe it is possible to customise that?

---

### Post by Methuselah on 2010-01-17
NTFS is not a native linux partition that is why everything is not there out of the box.
You would have to install additional tools in windows to read the linux partitions from windows.

---

### Post by ianp5a on 2010-01-18
But it *does* work out of the box. The Ubuntu installer probably detected NTFS disks at install time.

They just were not set to **mount** automatically at boot time. And that was just a switch.

---

### Post by anantshri on 2010-01-18
> **ianp5a said:**
> Thanks. With your tip I found NTFS Tools and Mount Manager in the Software Centre.
And you are right, it does save the need to mess around in text files and folders. And a lot safer too.

I used **Mount Manager** which did it all for me and showed me a whole load of other options too that I would not have discovered with a text file.

Thanks to all the others who suggested typing things in a Terminal or text files. Now if anybody else in the Beginners area asks about this, be sure to tell them the easy way.

Thanks

---

