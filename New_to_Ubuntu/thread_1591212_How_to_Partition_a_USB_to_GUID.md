---
title: "How to Partition a USB to GUID?"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by HellaSpencer on 2010-10-08
So I'm trying to partition my USB drive to GUID so I can attempt to run OS X. I've been looking around in Disk Utility and GParted and can't seem to get it to work. So now do to me not knowing what I'm doing it says (in GParted) that my Partition is /dev/sdb1 with a caution sign and a key. And below that is something with everything saying unallocated or it's blank. Can someone help me? I can try as best I can to provide more information but I'm a noob with Ubuntu especially and computers somewhat. I just found out what partition is (kinda) today.

---

### Post by MisterGaribaldi on 2010-10-08
In Mac OS X:

Disk Utility:

Click on the device itself (not any of the partitions) in the list on the left side of the window.

Then, click on the Partition Tab on the top of the section to the right.

Then, click on the Options button which is below the display of the partition list.

Then, click on the GUID Partition Table button and click OK.

Now, whatever you set up for your partition table, the table itself will be GUID.

---

### Post by mordoc on 2010-10-09
While the link discusses creating large partitions, this should also work for other drives that need gpt type partitions:

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

### Post by srs5694 on 2010-10-09
Another online reference is [this article](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) that I wrote for IBM developerWorks a while ago.

I'm uncertain about precisely what's happening with your specific situation, but it sounds like GParted doesn't want to adjust your existing partition for some reason (that's what the key symbol means). This often happens if the partition is mounted. My suspicion is that your GNOME desktop has auto-mounted whatever partition is on the disk now, thus interfering with changes to the disk. You should be able to right-click the partition and select an option to unmount it. At that point, you should be able to click Device -> Set Disklabel to create a new disklabel. Click the "Advanced" item to reveal the partition type selector, pick "gpt," and click "Create." The disk will now be GPT.

---

