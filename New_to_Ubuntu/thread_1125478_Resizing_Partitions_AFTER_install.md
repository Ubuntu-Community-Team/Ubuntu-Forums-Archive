---
title: "Resizing Partitions AFTER install?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-14
I installed Ubuntu last night, and I love it. I let 150GB for Windows, and only about 90GB for Ubuntu. I'm now kicking myself for that, as I don't see myself using Windows very much anymore.

Is there any way to resize the partitions so that Ubuntu would have a much larger partition, and my Vista drive would shrink down to around 50GB?

---

### Post by Jakey_TheSnake on 2009-04-14
Yessir :) Boot from your LiveCD/LiveUSB again, press "Try Ubuntu" and then go to System > Administration > Partition Editor. 

Hope this helps,

Jake

---

### Post by Noise... on 2009-04-14
> **Jakey_TheSnake said:**
> Yessir :) Boot from your LiveCD/LiveUSB again, press "Try Ubuntu" and then go to System > Administration > Partition Editor. 

Hope this helps,

Jake

I used the Ubuntu Studio disk - which lacks the LiveCD feature. Is there another way? 

Could I use Vista's own Partitioner against it? :p

---

### Post by aleks.rudzitis on 2009-04-14
> **Noise... said:**
> 

Could I use Vista's own Partitioner against it? :p

No...i don't think that would work :p At least it wouldn't in XP. Or rather, if you had an empty partition you could, but Vista doesn't understand the filesystems of linux, so it couldn't move around existing data.

---

### Post by Noise... on 2009-04-14
> **aleks.rudzitis said:**
> No...i don't think that would work :p At least it wouldn't in XP. Or rather, if you had an empty partition you could, but Vista doesn't understand the filesystems of linux, so it couldn't move around existing data.

Shame...It would have been very satisfying to use a Vista against itself. :lolflag:

---

### Post by Yvan300 on 2009-04-14
Yeah the live cd would have been the easiest option, if gnome partition editor had the ability to resize partitions before they are mounted (like what partition magic does) then all you would have to do is install gnome partition editor, configure the partition sizes and restart. But maybe it has that feature, you never know. Search google for more help :)

---

### Post by Jakey_TheSnake on 2009-04-14
> **Noise... said:**
> Shame...It would have been very satisfying to use a Vista against itself. :lolflag:

Welcome to the Ubuntu mentality :D 

Can you not create a LiveUSB? Download an .iso of Ubuntu from the website, then System > Administration > USB Startup Disc Creator. USB drive must be 1GB or more.

---

### Post by cariboo on 2009-04-14
You can and should use Vista's disk management tools to resize your Vista partition. Then you can use the [Gparted]("http://gparted.sourceforge.net/download.php") LiveCD to resize you ext3 partitions.

Jim

---

### Post by ddarsow on 2009-04-14
> **cariboo907 said:**
> You can and should use Vista's disk management tools to resize your Vista partition. Then you can use the [Gparted]("http://gparted.sourceforge.net/download.php") LiveCD to resize you ext3 partitions.

Jim

what he said.
+1 for sure.

---

### Post by loomsen on 2009-04-14
> **Noise... said:**
> I installed Ubuntu last night, and I love it. I let 150GB for Windows, and only about 90GB for Ubuntu. I'm now kicking myself for that, as I don't see myself using Windows very much anymore.

Is there any way to resize the partitions so that Ubuntu would have a much larger partition, and my Vista drive would shrink down to around 50GB?

LOL 90 GB, you could install 90 full featured OSs into that ^^

I suggest, honestly, to read through the wiki and gather information about the filesystems differences.

Right after that, preferrably with the wiki still open (your terminal web browser is launched by typing w3b btw...), consider to rather create a useful set of partitions than just allocating WAY 2 MUCH diskspace.

Most likely you'd want to create a /boot partition to install your MBR to, 1GiG sized is way more than you'll ever need.
Create another partition for your root /. 20GiG if you plan ro grab everything in that apt offers ^^

Create a swap partition, max twice the size of your RAM, tho 1GiG should rarely be exceeded...

Create another one for your /home. This is where the magic happens and should happen. You shouldnt mess around anywhere else unless you know what you're doing.

This is the basic desirable setup. Assign as much Mem to your home partition as you'd like, files should go there.

For instance, I made a directory /home/MyMedia and added a system user (a user which doesn't actually exist, but is used for assigning properties) So I created that user, changed the ownership of the directory to root:media and added myself (and the other users on my system who should gain rights to access files located there) to the group media. Then, to preserve properties for newly created files somewhere in that directory tree, I set the GUID.

That way, if let's say someone on my network places a Video in /home/MyMedia/Video the file won't belong to <user>:<group user>, which would be default, but to root:media providing access to all the users in the group.


Just as an example.

I, for instance, created another partition and mounted it to /opt.

This is the default location for misc other apps/addons which don't go anywhere else. I use it across different distributions, it contains Java64, Flash64 and some custom scripts, pkges and stuff like that. 

This should be it for now, oh, and btw, resizing will work of any livecd, liveusb, whatever (tho USB is much faster)

But look at the partitions, it could take a loooooong time. I did it once, took me 8 hrs approximately, because smart me resized that part of my home (the largest partition) containing the data, which isn't much of an issue if you cut sth off at the end of it. But I cut it off at the beginning... 
&#8594;.&#8592;

However, enjoy.


(Btw, you could use the liveusb for a lot of other magic too... like stripping your windows, and converting the image to make it usable with some virtualization solution or so. I found the latest VBox release is just BAM!)

---

### Post by Noise... on 2009-04-14
^I just did the guided install on the free space of ~90GB. Basically, I just want the largest space possible for Ubuntu. The guided partitioning made the / partition, as well as a swap partition of 3.8GB. Both are Logical partitions.

I have a lot of music, as well as videos. Plus I'll be using the various programs that got installed with Ubuntu Studio to do audio recording, and maybe some video editing - both of which will end up with projects that have large sizes.

I'm not looking for anything fancy. Just a larger partition for Ubuntu.

---

### Post by sschnee on 2009-04-14
> **Noise... said:**
> ^I just did the guided install on the free space of ~90GB. Basically, I just want the largest space possible for Ubuntu. The guided partitioning made the / partition, as well as a swap partition of 3.8GB. Both are Logical partitions.

I have a lot of music, as well as videos. Plus I'll be using the various programs that got installed with Ubuntu Studio to do audio recording, and maybe some video editing - both of which will end up with projects that have large sizes.

I'm not looking for anything fancy. Just a larger partition for Ubuntu.

If you are worried about having space for your music and videos (I assume they are already on your Windows partition), why not just keep those files there?  Ubuntu can read and write to NTFS partitions just fine.  It would save you the effort of resizing partitions.

I believe ntfs-config does the trick for you.  Installed through synaptic.

---

### Post by Yvan300 on 2009-04-14
Hold on, the driver for ntfs read/write capability is still very experimental, it's good for reading from ntfs, but i highly recommend that you do not write to ntfs. There is a high risk of data corruption. A more better resoultion would be to create a partition in fat32, because windows and linux can read and write to it efficently.

---

### Post by sschnee on 2009-04-14
> **Yvan300 said:**
> Hold on, the driver for ntfs read/write capability is still very experimental, it's good for reading from ntfs, but i highly recommend that you do not write to ntfs. There is a high risk of data corruption. A more better resoultion would be to create a partition in fat32, because windows and linux can read and write to it efficently.


I did not know that.  I've been using it successfully on my dual boot system.  I guess not everyone has had my luck?

---

### Post by louieb on 2009-04-14
Fat32 would be my 2nd choice. For two reasons. 1). It has a 4GB or so file size limit. 2). It fragments much worse that NTFS or ext3. 

Reading and writing to an ext3 file system from windows with [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")  has a problem.  Newer versions of ext3 use an inode size greater that 128 bytes. And this sofware has not been updated to work with that.  

Writing to an NTFS file system from Linux has been around for years and its constantly getting better. Until you go completely windows free, that would be my choice for sharing data on a dual boot PC.  

Just my two cents worth.

---

