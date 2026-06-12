---
title: "Server cluster for storage"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by spewperb on 2007-08-01
Hi, I am trying to find out the best way of building a server cluster for storage. Basicly we are trying to build a system for storing large amounts of video data. We currently have about 20TB of data floating around on portable hardrive which is really not ideal on a number of levels! The idea is to create a series of cheap RAID 6 nodes each containing about 8 500GB SATA drives. What I want to know is there a way linking these servers together so they appear as one storage area. The important thing is that we can add another server to the cluser when we need more space without having to rebuild files systems etc. Is the possible? I was planning to use ubuntu as I have has some experience of using it and its compatible with the RAID hardware I'm using.

---

### Post by kidders on 2007-08-02
Hi there,

I'm no clustering expert by any stretch of the imagination, but what you described sounds very like ATA over Ethernet. It's an ultra-low-overhead means of exposing block devices (ie "blades") on a SAN.

Configuring a software implementation of AoE is trivial on Ubuntu (or almost any other Linux distro, for that matter). You could use it to...[LIST]
[*]Set up a series of block devices, and expose them over a network. These could be raw hard drives, RAID arrays, or even plain files.
[*]Compose a gigantic RAID array out of them on a single machine. How many layers of RAID to use would depend on how you wanted to handle your redundancy (ie how reliable individual blades would be).
[*]Expose that array to your LAN over NFS/AFP/Samba/etc.[/LIST]If AoE is something you don't already know about, and you're interested in looking into it, take a peek at software packages called "vblade" and "aoetools".

---

