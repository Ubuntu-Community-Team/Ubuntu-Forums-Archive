---
title: "slow file transfers"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by raghav_p on 2005-11-25
Hi

I was attempting to transfer a few files (300 MB) from my wirelessly connected Ubuntu to another Ubuntu connected to a router. I am running 802.11g and the transfer speed from my computer was at max 95kb/s and that seems immensely slow. What could be causing this?

---

### Post by darknuala on 2005-11-25
You probably need to check the dma settings on your drives.  DMA needs to be turned on, and is set to off by default.  

[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

---

### Post by raghav_p on 2005-11-25
Would DMA affect hard drives? Also, could it be that since my hard-drive is SATA, I'm having driver issues?

---

### Post by darknuala on 2005-11-25
Yes the DMA setting enabled on the hard drives makes a tremendous difference

---

