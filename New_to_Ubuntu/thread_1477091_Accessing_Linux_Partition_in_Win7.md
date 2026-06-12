---
title: "Accessing Linux Partition in Win7"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by stalkier on 2010-05-08
Is there a way to copy files from a EXT3 partition in Windows 7? I have tried several Win apps and they did not work with EXT3 partitions. I have about 100GB of files I need to access. Thanks.

---

### Post by davarino on 2010-05-08
I'm sure there's a more elegant way to do this, but you can set up a new vfat partition somewhere.

Using Linux, copy the files you want to be available to Win (and Linux?) to this partition and you'll be set.

Of course, this assumes you have room for this partition (a flashdrive is the easiest way, at least for up to 4 Gigs) and it will take some time. The upside is that it is nearly foolproof to do.

Next time you upgrade your Linux, seriously consider a vfat partition if you're running a double-boot system or if you're on a network that needs to access your data with Windows.

---

### Post by stalkier on 2010-05-08
> **davarino said:**
> I'm sure there's a more elegant way to do this, but you can set up a new vfat partition somewhere.

Using Linux, copy the files you want to be available to Win (and Linux?) to this partition and you'll be set.

Of course, this assumes you have room for this partition (a flashdrive is the easiest way, at least for up to 4 Gigs) and it will take some time. The upside is that it is nearly foolproof to do.

Next time you upgrade your Linux, seriously consider a vfat partition if you're running a double-boot system or if you're on a network that needs to access your data with Windows.

Thanks for the help but I was looking for a fast way. I have two large partitions on the same drive. One is the EXT3 and the other is a NTFS. It is taking forever to copy th files frm one partition to the other. Thought there might be a faster way of doing it.

---

### Post by Ducatiboy Stu on 2010-05-09
install "ext2ifs" in win7 . This will allow you to view ext2/3 partitions. 

NOTE, it wont work for ext4

---

### Post by Zintha on 2010-05-09
> **Ducatiboy Stu said:**
> install "ext2ifs" in win7 . This will allow you to view ext2/3 partitions. 

NOTE, it wont work for ext4
IF this doesn't work.
Could you just boot Linux and copy across to Windows from there?

I duel boot and quite often grab stuff from the other side or send it over.

---

### Post by Rushyang on 2010-05-09
I used Explore2fs some months before to seek into Linux Ext3 partition through Win XP. Not sure whether any version is out there compatible to win7 or not.

---

### Post by lavinog on 2010-05-09
ext2ifs works in vista...I would think it would work in 7 also.
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

It won't work with ext4 partitions though.

---

