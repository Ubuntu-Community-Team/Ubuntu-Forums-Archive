---
title: "Can I access Ubuntu files from Vista?"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by ArnoldGove on 2009-06-08
I installed Ubuntu 9 through Wubi.

Is there a way I can access Ubuntu files when in Vista, and vice versa?

---

### Post by MDNZ on 2009-06-08
Not sure if you can access the files from within Vista. However, you can access your Vista files from within Ubuntu by going to the /host directory.

---

### Post by whistlerspa on 2009-06-08
> **ArnoldGove said:**
> I installed Ubuntu 9 through Wubi.

Is there a way I can access Ubuntu files when in Vista, and vice versa?

No and Yes - says it all really doesn't it

---

### Post by alphacrucis2 on 2009-06-08
> **ArnoldGove said:**
> I installed Ubuntu 9 through Wubi.

Is there a way I can access Ubuntu files when in Vista, and vice versa?

There is software available for Windows that can access ext3 partitions.  Probably ext4 wont be possible yet.

---

### Post by tiyowan on 2009-06-08
You should be able to access your Windows partition and the files in it using Ubuntu. As far as accessing the files that are stored on your Ubuntu partition, there are ways to do this, but I strongly discourage you from trying to do so until you become more knowledgeable about the risks involved.

---

### Post by The Cog on 2009-06-08
> **alphacrucis2 said:**
> There is software available for Windows that can access ext3 partitions.  Probably ext4 wont be possible yet.

But he installed with WUBI, which means there isn't an Ubuntu partiton for the Windows ext3 drivers to see. Wubi uses a large file to simulate an Ubuntu partition. So no, I don't think he can access the Ubuntu files from Vista.

---

### Post by lukjad on 2009-06-08
> **ArnoldGove said:**
> I installed Ubuntu 9 through Wubi.

Is there a way I can access Ubuntu files when in Vista, and vice versa?
Yes, and here is how. 

First, you can make a partition that is called Data. Then format it to either FAT32 or NTFS. Then you can add files to it from both Ubuntu and Vista.

The second way is to follow this guide:
[http://www.go2linux.org/accessing-linux-drive-ext-with-vista](http://www.go2linux.org/accessing-linux-drive-ext-with-vista)

It basically allows you to access ext2 and ext3 drives. There may be a possibility for data corruption this way, so be careful what you edit. I don't know if malware running in Vista could damage the files in Ubuntu, thereby damaging Ubuntu, but I would be wary of that. I suggest the Data partition myself.

---

### Post by trulan on 2009-06-08
I tried installing the ext2efs drivers as mentioned many places.  They don't work, because Jaunty uses a 256 bit inode and the fs-driver requires 128.  But I like the data partition idea.  Thanks.

---

### Post by dileepm on 2009-06-08
Try Partition Magic [http://www.softpedia.com/get/System/Hard-Disk-Utils/Partition-Magic.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Partition-Magic.shtml)

---

### Post by abhiroopb on 2009-06-08
There are a number of different softwares that allows access to ubuntu partitions from windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://ext2fsd.sourceforge.net/projects/projects.htm](http://ext2fsd.sourceforge.net/projects/projects.htm)

---

### Post by 3rdalbum on 2009-06-08
NOTE: The original poster installed Ubuntu through Wubi. So, he doesn't have an Ubuntu partition, he has an ext3 filesystem inside a file on his NTFS Windows partition. Any howtos posted MUST address this otherwise they are useless to the OP.

ArnoldGove: It's very easy to access files from Windows in Ubuntu when you have used the Wubi method of installing. Wubi automatically sets up a folder called "/host" which is where your Windows partition is mounted. /host is at the top level of the filesystem (in other words, in the file manager click the "Filesystem" in the left pane, and then double-click "host").

---

