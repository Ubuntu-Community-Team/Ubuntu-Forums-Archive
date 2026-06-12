---
title: "Very slow samba and huge memory consumption"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by lil_elvis2000 on 2008-07-08
I'm running 8.04 and 2.6.24-19 on a Celeron 800Mhz 640MB RAM 3COM 3c905C NIC w/ 11Gig IDE and 2X320G SATA, SATA PCI card. RAID 1 on the SATA drives. I'm not sure but in dmesg the SATA drives are configured to UDMA/100 :(


I'm getting pretty poor SAMBA performance. The shares are set to folders on the RAID. a 1.8Gig file copied from one Samba share (or even between folders on the same share) takes over 10minutes. Doing the same thing on FreeBSD (the machine used to run FreeBSD) took 5minutes. Also the memory consumption reported by TOP goes from 140M to 638M with about 320M in swap. This memory does not appear to be returned. Smaller files display the same symptoms except less memory is used.

if I stop SAMBA the memory is not returned. but unmounting the RAID does free the memory!

I'm pretty sure this is the result of taking recommended updates. I'll never do that again!

Anyone have any ideas how I can diagnose and hopefully solve this problem.

---

### Post by bsh on 2008-07-09
well it can be many thing actually... i am not sure about ata100 on a pci sata raid card, probably it's not the worst. but i hope your card is set up correctly and the raid too. (is it a dmraid?)

as the first step, i would copy some big files internally on your computer, but not through samba! copy some big file from the raid to the other ide drive and measure the speed. then copy something from the raid to the raid. then copy something from the ide drive onto the raid. and see if you have good speeds (a 11gb ide drive is probably not the fastest one, lol)
if it shows that you have acceptable speeds, then you are most likely fine with your raid card and raid setup, and the problem might be in your samba config.

---

### Post by lil_elvis2000 on 2008-07-09
I have done a test copy of 1.8Gib file from RAID to IDE. <2min.
Then from IDE back to RAID ~3.5min. Still OK.
from Windows to RAID ~5min..reasonable but slow.

The memory consumption is still there however..maxes out my RAM and start going to swap. I did notice that if I delete the copied file the Cached and RAM figure in TOP drop by over 300M. So something is up. The memory does not drop immediately after the copy is finished. it seems a huge amount of the file is kept in cache (the cached figure in TOP is 600M!)

One thing I noticed if I do a lsmod is: a entry of
3c59x      46376 0
mii         6400 1 3c59x

I have a 3c509c Tornado nic. I suppose the driver is compatible.
 
Two problems I can see:
  1 - extemely high memory consumption used on files (particularily RAID)
  2 - SATA drives using UDMA/100 - effectively choking any performance out

I suppose someone could help explain what I am seeing. Its a lot different than FreeBSD.

---

### Post by lil_elvis2000 on 2008-07-09
Well I've sorted out the cached memory. this is okay as applications will reclaim this if needed.

UDMA/100 - the drives operate at this speed max (even if they are advertised as 1.5Gbps) So this is also okay. 

The rest must be down to processor and mdadm. I am happy with mdadm...with FreeBSD it was much faster, but the mirror also crashed and the PC also crashed nearly everyday. With Ubuntu - it hasn't crashed even once. And I've thrown a lot of big files at it.

Anytips on fine tuning SAMBA and mdadm.

---

