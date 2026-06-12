---
title: "Samba starts fast and then slows down significantly"
date: 2015-12-03
forum: Networking &amp; Wireless
---

### Post by Spency on 2015-12-03
I'm trying to optimize my samba server. I'm experimenting with a tar.gz file that's 30GB. I have found loads of information on Samba optimization, but there's something I can't quite understand.
When I begin the transfer in nautilus, the transfer dialog initially shows a transfer rate of 130MB/s and within a few minutes transfers over 3Gb of the file onto the share, and in this time the transfer rate slows down to about 5MB/s, which is usually when I cancel the transfer. I've let it go on for longer and it has gotten as low as 1.5MB/s. 

After killing the transfer, the file size of the file on the share is right around 3-4GB. So am I right to think that there was a true burst of speed and that amount of data made it over? What's more puzzling is, while monitoring the traffic on the server using iftop, it does not appear that amount of data was in fact transferred, nor does it seem like that initial speed was achieved. 

Is this common for Samba users over a wireless network? Moreover, what could this indicate about the potential of my samba server transfer rate?

---

### Post by TheFu on 2015-12-04
This likely isn't samba, it is Linux doing disk buffering in RAM.  **free -m** will show the buffers being used.  Once the buffers are full, then the data must be stored to disk, which is much slower than any GigE network.  USB2 disks will be VERY slow.  So, what you need to do is look at all the components being exercised in the file transfers.
* Source disk READs
* Source NIC 
* Networking (all GigE or is there some 10/100 left)?
* Target NIC
* RAM avail for buffers
* Target disk WRITES

iperf is good to validate networking between A and B.

Reading is 20-30% usually faster than writing on spinning disks. The connection bus matters, USB2, USB3, Firewire, SATA, eSATA, Infiniband ... SATA, eSATA and Infiniband are the fastest - by far.  "Green" drives are slower than "Blue" which are slower than "Black" ... every disk has design specs which explain.  You can also tune the disks using **hdparm**.  There are a few tuning guides out there.   Mine: [http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results)

And don't forget that networks are always bits-per-second while disks are usually Bytes-per-second, so convert everything to one or the other for your calculations. Be extremely careful with Mbps vs MBps.

---

