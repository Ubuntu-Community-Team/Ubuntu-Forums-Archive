---
title: "Why is internet download faster than nfs?"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by Gotou on 2006-09-02
Hi!  Why can I download an 800meg file from the internet faster than I can copy the same file from one Ubuntu computer to another using NFS?

What config files do I need to tweak or is NFS just not up to the task?

Thanks!

---

### Post by SkyNet2029 on 2006-09-02
NFS should be (most definetly is, actually) up to the task of a simple transfer of only 800 Megs.
Here are some of the actual factor(s) that can affect NFS, either to the positive or the negative:
 
> appropriate network capacity, faster NICs, full duplex settings in order to reduce collisions, agreement in network speed among the switches and hubs, etc
as well as the actual kernel version/compiled capacity as related to the maximum block transfer size, cpu type, wether or not the actual hardware being used is up to the task-Cpu type/Memory available/number of NFS daemons running at any given time, the type of file-system being used on the server could be a bottleneck in the transfer rates due to overhead, and the list just goes on and on. 
But, yes, in the end the NFS is definitely up to the task of an 800 meg transfer.
Here's a link that should prove more useful to you than my ranting as to the many different issues one can blame instead of the actual NFS service.  ;) 

[http://nfs.sourceforge.net/nfs-howto/ar01s05.html]("http://nfs.sourceforge.net/nfs-howto/ar01s05.html")

---

### Post by cylon359 on 2006-09-03
How did you set it up?  You want to use the kernel server, as it's faster, supports locking, and more.

But usually if performance sucks, then you have a duplex mismatch or something like that.

---

### Post by Gotou on 2006-09-03
What's a duplex mismatch?

I'm using the kernel server.

I'm fighting another Linux battle at the moment so I haven't been able to study the link provided earlier.

Thanks!

---

### Post by NetworkGuy on 2006-09-03
A duplex mismatch is when you have an ethernet card at either half or full duplex and your ethernet switch is set to the opposite setting.  This causes the device set to full duplex to transmit more frequently than the device set to half duplex can handle, thus making the full duplex device re-transmit the same information over again.  This will slow down a transfer to a crawl.  The faster the cards are communicating at, the more noticeable the duplex mismatch is.

Think of duplex as either a two or one way road.  Half duplex allows traffic to flow both ways at the same time.  Full duplex only allows traffic to flow in one direction at a time, but technically at double the speed.

Hope this helps.

---

