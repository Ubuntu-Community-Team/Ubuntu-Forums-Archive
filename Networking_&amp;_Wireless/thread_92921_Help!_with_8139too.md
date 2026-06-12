---
title: "Help! with 8139too"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by rstewartmailacct on 2005-11-20
Hi I have scanned the threads on this without success. The problem is straightforward.  I have onboard lan sis900 disabled in bios and Realtek 8139 lan card added with the need to have parameter of half duplex for cable modem on the Realtek card.

Ubuntu is loading 8139cp.ko and 8139too.ko at boot.  I can run rmmod 8139cp and rmmod 8139too then modprobe 8139too with options of 8139too media=0x01 from file in /etc/modprobe.d named 8139too.modprobe and internet works.  I also have 8139cp entry in /etc/hotplug blacklist file to prevent load of 8139cp but nothing works on boot.  BOTH drivers are still loaded and the internet won't work. 

Any advice would be great!

Thanks!

---

### Post by rstewartmailacct on 2005-11-21
Surely someone has a clue about this??????????????????  Anyone from Ubuntu support????????????

---

### Post by mips on 2005-11-22
Posted some comments here, [http://ubuntuforums.org/showthread.php?p=510858](http://ubuntuforums.org/showthread.php?p=510858)

Seeing you are looking at that thread.

---

