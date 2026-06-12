---
title: "Partition external HDD"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-03-23
I'm currently dual booting 8.10 and WinXp. I have a 1TB external drive that I used to backup media and system backups on XP, and the drive is NTFS formatted. 

The drive is only 1/4 full, so I would like to create a partition in Ubuntu format (ext2/3/4 (whats the difference??)). Is this possible without erasing existing data and if so how?

Cheers
Kyle

---

### Post by drs305 on 2009-03-23
Certainly. Open gparted via System, Administration, Partition Editor. You will be able to split the partition and format a section to ext3. Defrag the ntfs partition at least once before you do this.

As with any partition operation, make sure you have backups of any critical/non-replaceable data.

Ext3 is ext2 with some improvements, such as journaling (a file writing operation). Ext4 is the next generation but is not widely implemented yet.

Here's a link to help you with gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by mikechant on 2009-03-23
> You will be able to split the partition and format a section to ext3. 

JUst to expand on this a little, you shrink the NTFS partition using the Gparted resize function (moving the end of the partition towards the start; don't move the start of the NTFS partition).  This will leave some unallocated space in which you can create a new ext3 partition

---

### Post by aquascrotum on 2009-03-24
See attached screenshot in gparted of the drive in question - I don't see where I can resize or split the partition?

[IMG]http://i636.photobucket.com/albums/uu89/kylesom/Screenshot--dev-sdb-GParted-1.jpg[/IMG]

---

### Post by aquascrotum on 2009-03-25
Bump...anyone?

---

### Post by odinb on 2009-03-25
> **aquascrotum said:**
> Bump...anyone?

Second option in the menu you have there says "Resize/move". that is the one you use.

Do not know why it is grayed out for you, on mine it is not. do you have a current version of GParted?

---

### Post by aquascrotum on 2009-03-25
Am running GParted 0.3.8. I don't have the resize/move button enabled on any drive, mounted or not.

---

### Post by odinb on 2009-03-25
I am running GParted 0.4.3. What does it tell you when you choose "information" from the bottom of that menu?

---

### Post by aquascrotum on 2009-03-26
> **odinb said:**
> I am running GParted 0.4.3. What does it tell you when you choose "information" from the bottom of that menu?

[IMG]http://i636.photobucket.com/albums/uu89/kylesom/Screenshot.jpg[/IMG]

---

### Post by odinb on 2009-03-26
Your disk is mounted, Try unmounting it before attempting to rezise it. Hopefully that fixes it!

---

### Post by aquascrotum on 2009-03-26
> **odinb said:**
> Your disk is mounted, Try unmounting it before attempting to rezise it. Hopefully that fixes it!

Mounted or unmounted, makes no difference.

Screenshot of info with drive unmounted....

[IMG]http://i636.photobucket.com/albums/uu89/kylesom/Screenshot2.jpg[/IMG]

This is wrecking my head. I really need to move some media around because since I partitioned my main hdd to dual boot, I'm running out of space. But I'm told I can't risk writing valuable data to NTFS using Linux. Creating an Ext3 partition on this drive is urgent. Help!

---

### Post by kansasnoob on 2009-03-26
Install ntfsprogs from synaptic or go to terminal and:

```
sudo apt-get install ntfsprogs
```

**NOTE: Defrag that ntfs partition before you proceed with resizing!**

ntfs-config is an option, I just prefer ntfsprogs.

---

### Post by aquascrotum on 2009-03-26
> **kansasnoob said:**
> Install ntfsprogs from synaptic or go to terminal and:

```
sudo apt-get install ntfsprogs
```

**NOTE: Defrag that ntfs partition before you proceed with resizing!**

ntfs-config is an option, I just prefer ntfsprogs.

Thank you! my resize/move option has come alive :)

---

