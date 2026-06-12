---
title: "Cant find .inf file for NDISWrapper"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by neilmorr on 2008-09-17
Hello. Yes, I am new to Linux and the forum. I just installed Ubuntu 8.04 on my new Dell XPS M1330 and the wireless card is not working (Broadcom 1395 WLAN Mini-card).  I am trying to use NDISWrapper to see if it will solve the problem. However, when I downloaded and extracted the driver file on my old XP system, I looked through and couldn't locate the type .inf file that I need. What am I missing? Would it be labeled as anything else? Getting this set up has been a nightmare so far so any help would be appreciated. Thanks guys.

---

### Post by Ayuthia on 2008-09-17
> **neilmorr said:**
> Hello. Yes, I am new to Linux and the forum. I just installed Ubuntu 8.04 on my new Dell XPS M1330 and the wireless card is not working (Broadcom 1395 WLAN Mini-card).  I am trying to use NDISWrapper to see if it will solve the problem. However, when I downloaded and extracted the driver file on my old XP system, I looked through and couldn't locate the type .inf file that I need. What am I missing? Would it be labeled as anything else? Getting this set up has been a nightmare so far so any help would be appreciated. Thanks guys.

The files you are looking for are the bcmwl5.inf file and the bcmwl5.sys (for 32-bit) or bcmwl564.sys (for 64-bit).  If you can't find it, you can figure out your chipset by doing the following in the Terminal:
```
lspci -nnd 14e4:*
```You will need the chipset number (it will look something like 14e4:4312) and the revision number (look for rev--should be right after the chipset).  You can then go to this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
This has some information where you can get the Windows driver that you need.

---

