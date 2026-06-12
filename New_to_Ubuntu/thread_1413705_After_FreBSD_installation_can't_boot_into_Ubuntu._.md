---
title: "After FreBSD installation can't boot into Ubuntu. I don't think I lost it..."
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Ubunser on 2010-02-22
Hi! I had Windows XP and Ubuntu installed when I decided to add FreeBSD. I hoped 3 systems would fit in as I had one extended partition. I am not very skilled in partitioning yet, so it was much an experiment. Now FreeBSD installation completed. It substituted grub loader with its own loader. What's ridiculous is FreeBSD doesn't boot either. The only thing left working is Windows, which I used to have a look at my partitions. So they are all there, nothing's gone. I mean only FreeBSD's partition emerged as new. But Ubuntu's are still there. I used only unused disk space for FreeBSD. So, it's fair that I counted on it's secure living further on. The thing I agreed to substitute grub loader with a BSD's one is also not a mistake I think. So what did I do wrong? Is there a way to bring my Ubuntu to life?
Of three systems supposed to be now only Windows is bootable - the one I need least - and it's in the beginning of the disk. I know there might be ways to correct this setback, aren't there? 
I view this as a chance to find out more. So please If you know what's going on spend a minute to post here. Thanks.

---

### Post by byStanderone on 2010-02-22
...try to reinstall grub from your ubuntu live cd into the ubuntu partition.

---

### Post by Ubunser on 2010-02-23
> **byStanderone said:**
> ...try to reinstall grub from your ubuntu live cd into the ubuntu partition.

I just did that, but unfortunately this didn't work. When I installed FreeBSD I remember it said that FreeBSD loader (similar to grub) must be installed in the first boot sector(you got me). So there is another loader from BSD that beats grub(. I even deleted the partition with BSD, but that's not the issue, this is all due to BSD loader programm, once I remove it - the grub will be accessed. 
Help, please.

---

### Post by oldfred on 2010-02-23
You should be just able to restore grub. Just be sure to restore the correct version of grub as now there is grub legacy and grub2 with new installs of Karmic.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want some help reviewing what is where run this script, but I do not know if it includes FreeBSD in all of its searches. My understanding of FreeDSB is that it uses both the MBR and PBR (it calls it boot slice) like windows does. 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Ubunser on 2010-02-27
Hi! I did it, it was easy. Though I'm not sure all that I did was necessary, but I was so eager to access my Ubuntu that I deleted everything except it. Then reinstalled Grub Legacy following simple instructions from this manual  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I am more happy that I encountered this and solved it, rather than I would be if I didn't:p
Thanks. Finding what you need hugely depends on key words, so thanks to byStanderone because he said "reinstall grub" and thats what I googled for. THanks to all.

---

### Post by Ubunser on 2010-02-28
I again installed FreeBSD but this time without installing BSD loader into Master Boot Record. But I cannot boot to FreeBSD as it is not listed in Grub. What am I supposed to do?

---

