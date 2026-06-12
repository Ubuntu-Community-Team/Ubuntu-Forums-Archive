---
title: "Partitioning NTFS"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-06-17
I have a 250GbHD, and partitioned it to 170Gb (Windows Vista) and 80Gb for Ubuntu using the partitioner in Vista. During the installation of Ubuntu, I selected "Use Largest Continuous Free Space" as my partitioning option.

Is it still possible to repartition the Vista partition of 170Gb to something smaller like 150Gb for another OS? GParted won't allow me to partition NTFS. Not even in Windows. I tried disk check (chkdsk /f) and Defragmenting the HD but to no avail. Am I missing something? If my case is still unclear to you, please do ask me!

Thanks for advising. :)

---

### Post by wpshooter on 2009-06-17
When you say Gparted won't allow me to partition NTFS do you mean that it will not allow you to resize the 170gb partition to a lesser size ?

---

### Post by elysianfields44 on 2009-06-17
As far as I remember GParted can resize NTFS partitions without a problem. Resizing doesn't work only when you already have 4 partitions on a single HD. My guess is that when you used the default partitioning during the Ubuntu installation, it probably created 3 partitions: root, home and swap, which together with your Vista partition makes 4, and thus the problem you are having. You could get rid of the swap partition and use a swap file instead, here's how: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?) Make the size of the swap file the same as the size of your current swap partition, and that should work. Hope that helps.

---

### Post by LesterPalooza on 2009-06-17
> **wpshooter said:**
> When you say Gparted won't allow me to partition NTFS do you mean that it will not allow you to resize the 170gb partition to a lesser size ?

Yes, Gparted won't allow me to resize the 170Gb to a smaller size.

---

### Post by LesterPalooza on 2009-06-17
> **elysianfields44 said:**
> As far as I remember GParted can resize NTFS partitions without a problem. Resizing doesn't work only when you already have 4 partitions on a single HD. My guess is that when you used the default partitioning during the Ubuntu installation, it probably created 3 partitions: root, home and swap, which together with your Vista partition makes 4, and thus the problem you are having. You could get rid of the swap partition and use a swap file instead, here's how: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?) Make the size of the swap file the same as the size of your current swap partition, and that should work. Hope that helps.

Does the picture attached to this reply show that I have four partitions?

---

### Post by Miljet on 2009-06-17
You can't resize partitions that are mounted. You need to boot from a live CD and change the partitions from there. Or make a bootable gparted CD and use that.

---

### Post by elysianfields44 on 2009-06-17
> **LesterPalooza said:**
> Does the picture attached to this reply show that I have four partitions?

Nope. The screenshot shows you have one primary partition (NTFS) for Vista, and one extended partition for Ubuntu, where it placed the ext3 file system and the swap space. What I was referring to in my previous post was that you can have up to 4 primary partitions, but anyway this is not your case, so in theory it should allow you to resize them. I noticed there's a warning icon beside your NTFS Vista partition and it doesn't show the used/unused space, so that's most likely why you can't resize it either. (I am guessing you probably *can* resize the Ubuntu partitions?) It also appears that when you use GParted to mess around with a Vista partition, you then need to boot from the Vista installation CD and run "repair your computer" from there, see this: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/). Have you tried rebooting and loading Vista? Does that work or does it give you a "windows failed to load" message?

(By the way I've resized my XP partitions many times and this never happened, so it's all due to the "improvements" that come with Vista :-P)

---

### Post by swerdna on 2009-06-18
Don't resize a vista NTFS partition with GParted until you read this caution on repairing vista's record of the partition table afterwards:
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by elysianfields44 on 2009-06-18
> **Miljet said:**
> You can't resize partitions that are mounted. You need to boot from a live CD and change the partitions from there. Or make a bootable gparted CD and use that.

Ah yes, that's an excellent point. I almost forgot about that. Though you could probably just unmount them from Nautilus.

---

### Post by LesterPalooza on 2009-06-18
Amazing replies. I will try them all today! :) For now, I'm going to Calculus class!

---

