---
title: "Partition with failed install"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by HardDiskDriver1 on 2011-04-05
Hi all,
I've only ever used Ubuntu on an occasional basis installed inside Windows 7, so I decided to start booting from a partition. Everything seemed to be running smoothly and I allocated a partition (somewhere between 10 and 15 GB). I got right through to the stage of installation where it asks for keyboard type and username, and the files had copied. The installation hung there for 15 or 20 minutes (with the message "Ready when you are" above the progress bar, yet no Forward button) and I had to go, so I used the "Suspend" button.
I can't find any way of booting into this partition now, and I don't want it to simply be sat there occupying space. I'm not sure which partition it was, either, since I have two at 15 and 11 GB. 
If anyone can give me some idea of which partitions are which (my laptop has a recovery partition too) or how to remove/reinstall in it, I'd be greatful for your assistance :)

---

### Post by oldfred on 2011-04-05
Welcome to the Forums.

Your userid cannot have capitals or special characters. For some reason it does not tell you that.

If you have created partitions, then use manual install to reuse partitions or you will end up with duplicates.

From liveCD this will show partitions.
sudo fdisk -lu
This shows UUIDs and labels if assigned I like to label partitions to know more what they are:
sudo blkid

---

### Post by nickleboyblue on 2011-04-05
There's a chance that, if you attempt installing it again, that it will auto-detect the location of the attempted install and ask if you want to install it there.  The installer will detect all of the partitions, so even if the partition didn't get installed completely, you should be able to still install ubuntu on it without any real problems.

The only issue is that, for dual booting with windows, it's difficult to keep the windows install intact.  I haven't ever worked with a dual boot, as Ubuntu has always had everything I could want and so much more, but I am aware that lately, the dual-boot setup hasn't been working completely with Ubuntu.  You might try searching the forums to see if there is anything special you need to do to get a dual boot working without killing windows.

---

### Post by HardDiskDriver1 on 2011-04-05
Thank you for the prompt reply. Would it be better to install within windows then? Or perhaps treat myself to an external drive for my Ubuntu installation?
oldfred - Will using those commands give me a clear indication of which partition contains the failed install? Also, will I need to create a different account to sort out the capitals problem?
Thank you very much :)

---

### Post by Daniel0108 on 2011-04-05
> **HardDiskDriver1 said:**
> Thank you for the prompt reply. Would it be better to install within windows then? Or perhaps treat myself to an external drive for my Ubuntu installation?
oldfred - Will using those commands give me a clear indication of which partition contains the failed install? Also, will I need to create a different account to sort out the capitals problem?
Thank you very much :)

By installing within windows, do you mean WUBI? Because WUBI isn't very good, it's just like a trial (or test) version of ubuntu.
If you really want to use Ubuntu, install Ubuntu only and create a Virtual Machine for windows (you need a good computer for Virtual Machines ;)).
If you don't have a good computer, use wine.

I hope this helped you,
Daniel

---

### Post by oldfred on 2011-04-05
The fdisk command just shows all partitions. NTFS are windows and ext3 or ext4 are Linux, swap is swap. If only one ext4 partition that has to be your install. If not sure post what the command gives.

---

