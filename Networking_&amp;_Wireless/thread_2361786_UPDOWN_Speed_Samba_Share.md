---
title: "UP/DOWN Speed Samba Share"
date: 2017-05-20
forum: Networking &amp; Wireless
---

### Post by jay116 on 2017-05-20
I wanted to bounce this off someone. I have a samba share on a Ubuntu server, with gigabit nics on both ends sending and receiving, and a gigabit switch in between. All drives are non-raid platter on the server, and when I transfer a file from windows explorer from the server to my ssd on my windows box I get 113MB/s, which seems reasonable to me. When I transfer a file to the samba share from windows explorer I only get 80-95MB/s. Is this a read/write issue with the server hard drive maxing out its writing performance? If so the only option I can see is a Raid 0 setup on the server to give me a write performance between greater than 100MB/s to over come the single drive write speed. Any thoughts?

Thank you.

---

### Post by TheFu on 2017-05-20
Spinning disks are slower than SSDs.

I normally see 65-80 MB/s with Samba to "blue" WD disks on a GigE network using Intel NICs. These are 500MB-10GB files, not lots of tiny files. If you are using non-Intel NICs, there are some performance issues which can impact throughput. Realtek is famous for this issue.

If you want faster performance, put 4 SSDs into a RAID0 config.  Using a high performance file system that understands using SSDs for caching would help too. ZFS can do this, but ZFS isn't best used on less than 6 disk setups.

---

### Post by jay116 on 2017-05-21
Thanks for the input. I think I'll live with that performance until I'm ready to invest more money.

---

### Post by TheFu on 2017-05-21
BTW, 120MB/s for SSDs is pretty low.  My cheap SSD gets 180MB/s. I don't use samba on that machine.  NFS is faster and provides native file permissions. Not really an option under Windows - well - it is an option, but I haven't found any of the free NFS-client software to work.  The paid NFS-client software is a hassle and runs $150+ the last time I looked at it.  In theory, Windows Enterprise and above includes an NFS-client, but I've never gotten it working after spending about 6 hrs in the attempt.

If you have realtek NICs, getting intel NICs that support offloading will help by reducing the amount of CPU necessary for network stuff. If the system is low powered, it will make a difference. If it is high powered, perhaps not. Hard to say.

You can help others here by marking this thread as "**solved**" - that will prevent people trying to help from looking and help people looking for help to gain a little understanding.  Most people don't see the sort of performance you are seeing.

---

### Post by jay116 on 2017-05-21
"BTW, 120MB/s for SSDs is pretty low" ---- So you get 180MB/s off of Gigbit ethernet? I'm confused. Maybe reread my original post. I believe Gigabit has a maximum of 123MB/s.

---

### Post by TheFu on 2017-05-21
> **jay116 said:**
> "BTW, 120MB/s for SSDs is pretty low" ---- So you get 180MB/s off of Gigbit ethernet? I'm confused. Maybe reread my original post. I believe Gigabit has a maximum of 123MB/s.

Drive throughput isn't limited to network throughput, plus some people could have ludicris speed networking at home - either using multiple bonded GigE connections or 10Gbps stuff.  Never know around here.

Also, 125MB/s is the theoretical max for a GigE connection.  115MB/s (920Mbps) is the most I've ever seen with pure network, no disk, no encrypt, no protocol overhead, testing. Basically, ideal conditions.  That isn't realistic for CIFS, even with highly aggressive tuning.

NFS is faster than CIFS in real-world use, if you care to get all the network disk performance you can. Alas, Windows is a 2nd-class NFS client.

---

### Post by jay116 on 2017-05-21
is there a way to add an SSD as a write cache so that i can write to the SSD over the network and it pushes the data back to the platter drives internally within the server?

---

