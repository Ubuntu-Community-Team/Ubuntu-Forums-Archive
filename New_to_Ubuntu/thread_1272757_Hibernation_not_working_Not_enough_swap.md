---
title: "Hibernation not working: Not enough swap"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by jumpboy on 2009-09-22
I'm trying to get hibernation to work on my netbook. free -m showed I had 991 MB of mem and only 3xx of swap space. I searched the forum and added a swap file and added it to \etc\fstab. Now I have 1376 MB of swap and its still not working. 

HELP!

---

### Post by Don1500 on 2009-09-22
> **jumpboy said:**
> I'm trying to get hibernation to work on my netbook. free -m showed I had 991 MB of mem and only 3xx of swap space. I searched the forum and added a swap file and added it to \etc\fstab. Now I have 1376 MB of swap and its still not working. 

HELP!
You do have a SWAP Partition right?
How big is yout hard drive? Your swap partition should be at least 2X your memory. Make it a 2 gig and you should be OK, if not try 3 gig.

---

### Post by jumpboy on 2009-09-22
How do I check for the swap partition? I'm not 100% sure but fdisk refers to /dev/sda5 as Linux Swap.

I have a 8GB SSD and 8GB SD card in the extension slot. So I don't want to allocate too much space since I don't have a lot of space.

I don't know if it'll make a difference but I followed this guide to optimize Ubuntu on my machine (except for installing Crunchbang). Would the SSD optimizations of made a difference in my swap space?

---

### Post by jumpboy on 2009-09-25
ok...

so I tried doubling the swap to 2000 with another swap file and nothing. I did some forum searching and see something along the lines of needing to boot from the livecd to change partitions. I installed via WUBI on a flashdrive so would it be the same and if so....steps?

Also, before the not enough swap message, theres a message about a dead queue or something. What does that mean and will it effect my hibernation?

---

