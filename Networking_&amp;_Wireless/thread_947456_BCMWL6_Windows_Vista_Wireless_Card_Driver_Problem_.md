---
title: "BCMWL6 Windows Vista Wireless Card Driver Problem on HP Pavilion DV2902TU Notebook"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by milindkanetkar on 2008-10-14
Hi,

I have been trying to get wireless working on my newly installed Ubuntu Hardy Heron. Have gone thru a lot of forums to understand and get wireless working. But only to get nowhere. Also, also I have been only copy pasting what the forums suggested.

Can I get help in getting my wireless working.

Basic details on the system:

1. HP Pavilion DV2902TU Notebook PC
2. Pre Installed OS: Windows Vista Home Basic
3. Ubuntu Install: Hardy 8.04 using Wubi
4. Wireless Device: BCM4312 802.11b/g (BCM4312 802.11b/g Wireless LAN Controller)

I have tried all the tricks of using ndiswrapper etc etc. Nothing seems to work. I also read that the Vista BCMWL6 driver will not work using it. I do not have any access to the BCMWL6 driver files for Windows XP though my other laptop (Dell Latitude D620) has BCMWL5 and I had installed Ubuntu on that one once before where Wireless worked automatically. 

What should I be doing.

Also, it is quite safe to say I am not very technically good in Linux/Ubuntu.

Thanks,
Milind

---

### Post by milindkanetkar on 2008-10-14
Any ideas, please?

---

### Post by Ayuthia on 2008-10-14
The bcmwl5 driver is what you would need to use for ndiswrapper.  The bcmwl6 driver will not work.

Here is a good guide to use for Broadcom cards and ndiswrapper.  It also has a recommended driver for your card.

---

### Post by milindkanetkar on 2008-10-14
I think the guide document / link got dropped. Can you send it out again.

Thanks,
Milind

---

### Post by Ayuthia on 2008-10-14
Sorry about that.  Here is the link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by milindkanetkar on 2008-10-14
Thanks. Let me try.

---

### Post by milindkanetkar on 2008-10-14
Doesn't work.

---

### Post by milindkanetkar on 2008-10-14
Second boot did it. Thanks a lot!!

---

