---
title: "No internet connection with wireless"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by focus310 on 2008-08-11
Hi,

I'm having trouble connecting to the internet via wireless.

I typed sudo modprobe iw13945 and received the following message:
FATAL: Module iw13945 not found.

My wireless card is Intel Corporation PRO/Wireless 3945ABG Network Connection.

Can someone help me out?

Thanks.

---

### Post by carmarthen lad on 2008-08-11
Join the club. There are loads of threads regarding this problem. I have been following these for weeks and still no luck.This seems to be a major problem. Any NEW ideas anyone?

---

### Post by jgaudario on 2008-11-14
> **focus310 said:**
> Hi,

I'm having trouble connecting to the internet via wireless.

I typed sudo modprobe iw13945 and received the following message:
FATAL: Module iw13945 not found.

My wireless card is Intel Corporation PRO/Wireless 3945ABG Network Connection.

Can someone help me out?

Thanks.

I was getting the same message.
so i typed dmesg \ iwl:
the message says: iw13945 radio frequency kill switch is on.
kill switch must be turn off for wireless  networking to work.

any idea? i checked my intel wireless, there seems to be no kill switch, all i could think of is turn it off but that wouldn't work will it?
i have a neo laptop, with prointel wireless 802.11. wireless works with windows xp but not with Hardy. any ideas?

---

