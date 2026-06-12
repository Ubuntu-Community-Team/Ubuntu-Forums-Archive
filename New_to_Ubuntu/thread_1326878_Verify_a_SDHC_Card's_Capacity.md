---
title: "Verify a SDHC Card's Capacity"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by hanzj on 2009-11-14
Hello,
Have just bought a no-name/generic SDHC memory card. It says 32 GB on the label, but when I plug it into my computer, the properyt dialog says "34 GB". Is there a way  I could verify the capacity of the card? I've heard that some cards may appear to have a big volume, but in reality, don't have as much.

I'm currently copying gigabytes of files onto the SDHC card, but it's quite slow. So if you know of a faster way, please let me know.

---

### Post by Jon Monreal on 2009-11-14
You could try "df -H" at the terminal. It lists the sizes of mounted partitions.

---

### Post by sandyd on 2009-11-14
> **hanzj said:**
> Hello,
Have just bought a no-name/generic SDHC memory card. It says 32 GB on the label, but when I plug it into my computer, the properyt dialog says "34 GB". Is there a way  I could verify the capacity of the card? I've heard that some cards may appear to have a big volume, but in reality, don't have as much.

I'm currently copying gigabytes of files onto the SDHC card, but it's quite slow. So if you know of a faster way, please let me know.
the speed problem - thats normal for those cards, you dont get really good speeds with them.

disk space - the only way is to copy til you run out. i had a card once that showed 20 GB in gparted, 25 GB in fdisk and the dialog said 18 GB. turned out to only have 15GB

---

### Post by hanzj on 2009-11-14
Jon,
```
df -H
``` works..
It shows
> Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdc1               34G    14G    21G  41% /media/7443-1B51

Wow. I guess I got more capacity (34GB) than I paid for (32G).

---

### Post by hanzj on 2009-11-14
> **carlee said:**
> the speed problem - thats normal for those cards, you dont get really good speeds with them.
You mean as compared with regular SD cards?


> **carlee said:**
> 
 i had a card once that showed 20 GB in gparted, 25 GB in fdisk and the dialog said 18 GB. turned out to only have 15GB

Disk Usage Analyzer shows 109.9 GB Size. Wow! That's way off!
what's the fdisk command to show size?

---

### Post by Jon Monreal on 2009-11-15
> **hanzj said:**
> You mean as compared with regular SD cards?




Disk Usage Analyzer shows 109.9 GB Size. Wow! That's way off!
what's the fdisk command to show size?

It's true: while you may have gotten a decent amount of storage space, you probably sacrificed speed.

Also, I wouldn't count on it for extreme reliability either. I wouldn't store anything on it that I didn't have a copy of elsewhere.

As far as your second request, you could try "[FONT=monospace]s[/FONT]udo sfdisk -l -uM". I don't believe you can get anything but blocks with fdisk ("sudo fdisk -l"). There's always "sudo parted -l" as well.

---

