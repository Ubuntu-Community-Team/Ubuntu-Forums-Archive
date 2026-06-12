---
title: "Frustrated with install"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Ash Velveteen on 2009-02-13
Hi, I am trying to install ubuntu 8.10 and I've hit a bit of a snag. I just cannot figure out the partitioning. I don't want to use the auto partition option, it wants to squeeze my windows partition instead of going into the unallocated partition I want it to go in. I've got a screenshot below.

[IMG]http://sites.google.com/site/adfskjl/Home/Untitled.gif[/IMG]

I've been trying for sometime to find something current that tells me how to manually put Ubuntu in where I want it, and I'm getting really frustrated. If someone could give me a 'for dummies' explanation of how to do this I'd be grateful. Please assume I don't know anything about linux.

---

### Post by N4zgu1 on 2009-02-13
you have to make two new partitons at least:

Swap: Put the double space than your ram size (the swap its kind of a second ram)

/: root, it where ubuntu is installed


(I also suggest to make a different /home partition, so that you dont lose information if something goes wrong)

You can get more info from this tutorial

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Ash Velveteen on 2009-02-14
Sorry, I tried reading the manual but it still doesn't make sense.

- Should I do the swap or the main partition first?

- For both partitions should I select Primary or Logical?

- For the main partiton, what should I put in the "Use As" field - Ext3 journaling file system, Ext2 file system , ReiserFS journaling file system, JFS journaling file system, XFS journaling file system, FAT16 file system, or FAT32 file system? The manual says that if you are only installing ubuntu to use ext3, which I assume is the same as Ext3 but I don't actually know. But I'm not sure if "installing ubuntu only" means installing it as the sole OS on the system - I don't want it as the sole OS, I want a dual boot. This may be a stupid question, but I'm really puzzled.

- For the "Mount Point" field for the main partition, what should I select - /, /boot, /home, /tmp, /usr, /var, /srv, /opt, or /usr/local? You said earlier to select root, but that doesn't seem to be an option. If I had to guess I would think it's either /boot (closest spelling to what you said), or the / option. As far as I can tell the manual doesn't say.

- For the swap space, can I assume that I should select 'swap area' in the use as field? That would be my guess, but I just can't find anything that confirms it.

- Assuming I continue to be this dense, what other problems do you think I might run in to? Any advise on how to solve them?

---

### Post by overlord.gaurav on 2009-02-14
Skipping the above manual, I'll tell you what you should do to get your ubuntu installed.

Select the free space, and click on 'New Partition'.
I cannot recall the exact layout of this prompt, but I can tell you what has to be done.
Enter the "Size" of your partition. This size should leave some space [around 1 gb] for swap area. Select the mount point as "\" [This is what is meant by mount point as "\root"]. 
The Primary/Logical option will already be selected, you need not worry.
The "Use As" field, select "Ext3 Journaling file system" [Off topic: Ubuntu 9.04 will have Ext4]
Now, make another partition, and as you mentioned, the 'use as' field should be 'Swap Area'.

---

### Post by 4Orbs on 2009-02-14
Hello, Ash Velveteen:
1. Click on the line that says "free space" to highlight it, then click on the "new partition" button.

2. Set the partition parameters as "logical", mount point "/", type "ext3", and size as "10000" MB or if you are going to be ripping and editing video "20000" MB. location "beginning". Click "apply".

3. After the tool re-scans the partitions, click the line "free space" to highlight it, then click the "new partition" button.

4. Set the partition parameters as "logical", mount point "/home", type "ext3", and size "all remaining except 2000 MB", location "beginning". Click "apply".

5. After the tool re-scans the partitions, click the line "free space" to highlight it, then click the "new partition" button.

6. Set the partition parameters as "logical", mount point "swap area", size "2000" MB (or whatever remains), location "end". Click "apply".

7. Move on to the next installation step.

---

### Post by Ash Velveteen on 2009-02-14
Okay, I got it working. Thank you for the help :)

---

