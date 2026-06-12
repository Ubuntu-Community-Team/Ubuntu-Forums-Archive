---
title: "Would you recommend installing via Wubi?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Julita on 2009-12-12
I need dual-boot w/ Win, and if install via USB won't work, I have to opt for Wubi. I have read many reports about failed install/no access to Win partition though. So... The question is whether it's worth to try it! Any help would be greatly appreciated!

---

### Post by NoaHall on 2009-12-12
No, and here are my reasons -

If your Windows disk is fragmented, then Ubuntu suffers - but more - as it uses the same drive.
It relies on Windows. If something goes wrong with windows, then you can't get into Wubi.

---

### Post by Julita on 2009-12-12
> **NoaHall said:**
> No, and here are my reasons -

If your Windows disk is fragmented, then Ubuntu suffers - but more - as it uses the same drive.
It relies on Windows. If something goes wrong with windows, then you can't get into Wubi.
I see. Thank you. I have defragmented the disk (both partitions), though, but I guess that doesn't count in this case. I have one partition with Win, the other - just formatted in NTFS. If I install Wubi on this empty partition, will it help?

---

### Post by wilee-nilee on 2009-12-12
> **Julita said:**
> I need dual-boot w/ Win, and if install via USB won't work, I have to opt for Wubi. I have read many reports about failed install/no access to Win partition though. So... The question is whether it's worth to try it! Any help would be greatly appreciated!

So with your net book is the windows system in one partition or several? And If I remember is it XP installed?

---

### Post by Julita on 2009-12-12
My netbook has Win XP Home installed in one partition (72GB). There are no visible files on the other (also 72GB.)

---

### Post by NoaHall on 2009-12-12
> **Julita said:**
> My netbook has Win XP Home installed in one partition (72GB). There are no visible files on the other (also 72GB.)

Wubi doesn't let you install to another partition.

---

### Post by Julita on 2009-12-12
> **NoaHall said:**
> Wubi doesn't let you install to another partition.
I see... Thank you... I'll have to figure out how to boot from my USB flash...

---

### Post by NoaHall on 2009-12-12
Unetbootin :)

---

### Post by Julita on 2009-12-12
Doesn't work. USB creator as well. [http://ubuntuforums.org/showthread.php?t=1353245](http://ubuntuforums.org/showthread.php?t=1353245)

---

### Post by NoaHall on 2009-12-12
Hm. In that case, it might be worth considering buying a external USB cd-drive.

---

### Post by Julita on 2009-12-12
> **NoaHall said:**
> Hm. In that case, it might be worth considering buying a external USB cd-drive.
That's I guess the only way...

---

### Post by wilee-nilee on 2009-12-12
> **Julita said:**
> My netbook has Win XP Home installed in one partition (72GB). There are no visible files on the other (also 72GB.)

Do you also have a recovery partition on the HD, I forget how to bring up the partition manager on XP.

If the 2nd partition is empty and the last one then if it is made unallocated the USB should read it as empty space theoretically. 

You should also make sure that if you are going to want to keep XP that you have a way to reinstall it in case you run into any problems in the future. The manufacturer will probably provide you with a down load of the XP or you can buy a disc from MS. If you have to go this far though you might consider buying the upgrade to W7 it is a much better and faster running OS.

If you buy the upgrade you can do a custom install leaving the partition space open for the Linux install. This is what I did my netbook came with XP and it ran really slow but it was acer's version with extra programs running then a normal XP setup.

Ther is also a gprted in system-administration gparted in the Linux OS see what it shows when opened.

Since you seem to be having several problems I suspect you netbook is not so Linux friendly so would you tell us what it is so we can look on the web and forums for compatibility.

Here is a compatibility wiki.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One%20150](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One%20150)

---

### Post by Julita on 2009-12-13
Thank you for your advice, but I experimented today a bit, and I was successful to boot into Kubuntu 9.10, but I didn't like it; nevertheless, it showed that my flash worked fine, and I thought about trying 9.04 .img file, and it worked! I deleted empty NTFS partition and installed on it UNR 9.04. Wired network didn't work, but I compiled necessary driver, and everything went smoothly! Hooray.

---

