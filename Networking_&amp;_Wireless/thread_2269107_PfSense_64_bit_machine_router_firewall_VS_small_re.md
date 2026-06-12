---
title: "PfSense 64 bit machine router/ firewall VS small retail wireless routers"
date: 2015-03-13
forum: Networking &amp; Wireless
---

### Post by queennikki1972 on 2015-03-13
[B]I have been weighing out the pros and cons of a Linux based router like PfSense SSD or SATA hard drive installed vs. a stand alone small scale retail router. Currently we only server 2 outbound web machines and 4 personal machines. We also have several wireless access devices that use WAP. I read on a different website that not only do the bare metal routers run a lot more options to tweak, but actually improve gaming as well for those hard core gamers. That would be my roommate. Also I watch a video about using larger hard drives for the sole purpose of swap and local caching of data for faster browsing. PfSense has many built in extras like blocking non U.S. ip's, spoofing and spam, all built into the router. 

Now that I've about sold myself on the idea, by typing all of this, here is the actual question.


The current hardware I have available is a Intel Dual Core 3.2ghz Socket 995 with 4GB memory max. Its an ASUS P5LD2 board. [http://www.fracassi.net/iw2ntf/manuali/asus_p5ld2.pdf](http://www.fracassi.net/iw2ntf/manuali/asus_p5ld2.pdf)

It has 
x1 PCI-E 16 Reserved for video since there is no on board video 
x2 PCI not used
x3 PCI-E x8  for

x2 1000MB Ethernet Cards
x1 Wireless N dual channel

I also have a 24 port Gigabyte Unmanaged Switch

The websites themselves seem VERY fast and the current main website has built in protection, but is limited as it is based on SMF forum. This is an average small load server with plenty of resources to grow. 

The reason for this post is I have a 42U rack and going to deploy a custom OpenStack with seperate machines for database, apache, ftp, etc. The expected load will be 100 people day at first and eventually 100 people round the clock. 

Is this the way to go in terms of preparing for UNEXPECTED GROWTH in terms of the router for a National Site with multiple databases and heavy php scripting and will it increase my roommates gaming experience?

[/B]

---

