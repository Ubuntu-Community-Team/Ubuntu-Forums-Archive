---
title: "Local VNC connections unusable when high traffic on Ubuntu 18.04"
date: 2020-08-31
forum: Networking &amp; Wireless
---

### Post by brzi on 2020-08-31
Hi,

I'm running vino and using a Win10 client with TightVNC to connect over wifi on local network with encryption off. 

The VNC connection works just fine, unless there's download traffic on the server. It doesn't even matter what the download rate is, the VNC is just unusable until downloads are complete, which is very annoying.

Any tips on how to allocate/reserve bandwidth for VNC? Or should I try something else instead of vino? (I did try XRDP but that experience was just horrible...).

---

### Post by TheFu on 2020-08-31
Better to slow the download traffic instead. Most download tools have a way to control the bandwidth used. 

For example, rsync has 
```
             --bwlimit=RATE          limit socket I/O bandwidth
```
Consider the disk performance AND the network performance.

The issue is not likely to be with any single program. Rather, look at the total system and how resources are being shared by all the different tasks running.  Especially CPU, RAM, network and disk I/O.  If there is a bunch of data coming down at high rates, being written to a slow HDD and that HDD is shared for the user VNC session, nothing can be done, except to give the disk the time it needs to flush buffers to storage as needed. The easiest way to do that is to limit the bandwidth used.
Or to force the storage used for the download to be different from the storage used for all other parts of the system. Think phyiscal devices, not logical.

---

