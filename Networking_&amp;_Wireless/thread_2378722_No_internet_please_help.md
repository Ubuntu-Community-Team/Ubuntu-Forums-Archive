---
title: "No internet please help"
date: 2017-11-26
forum: Networking &amp; Wireless
---

### Post by johnstefnds on 2017-11-26
So I did a huge mistake I installed the packages mentioned in the answer to the topic here [https://askubuntu.com/questions/660603/steam-download-speed-drops-off-a-cliff-and-then-stops#708227](https://askubuntu.com/questions/660603/steam-download-speed-drops-off-a-cliff-and-then-stops#708227) for a totally different reason (I had the same error popping in the console when trying to start a steam game but I had NOT any prior connection issues what so ever until then... ) 

Now after restarting my computer I can no longer connect to the internet :( 

How can I revert the above steps (well I guess I could just delete the packages I installed but I dont wont to mess things further and hope someone tell me what to do step by step :P )

I use ubuntu 17.10 my kernel version is 4.13.0-18 my motherboard is an Asrock 970 pro 3 with - Northbridge: AMD 970 - Southbridge: AMD SB950 and has an Realtek RTL8111E and supports gigabit lan.

---

### Post by howefield on 2017-11-26
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by johnstefnds on 2017-12-02
Thank you for your responses. The issue was dnsmasq which apparently is an obsolete service and which I needed to purge after doing so everything works fine.

---

