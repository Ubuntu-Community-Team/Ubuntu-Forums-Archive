---
title: "Help! slow network"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by soongwoo on 2006-10-23
I installed Ubuntu 6.06 AMD64 Server on two Intel machines.
Those two have are same hardware specification, except CPU:
 - two CPUs, 4G RAM, SCSI HDDs
 - use Intel on-boatd NICs

Surprisingly, network speed is very different!
Slower CPU machine is much faster in network.

I think the installation of Ubuntu on them is in same manner:
 - differ only in hostname, I think.

How could I identify the cause and fix this problem?

Thanks
soongwoo

---

### Post by DaveBorealis on 2006-10-23
> **soongwoo said:**
> 
Surprisingly, network speed is very different!
Slower CPU machine is much faster in network.

I think the installation of Ubuntu on them is in same manner:
 - differ only in hostname, I think.


Hello Soongwoo,

What exactly is the slower machine doing that makes it seem slow.  For instance, does it take a long time to make the connection, but then exchanges data at a normal speed, or does all transference of files happen slowler?

Also, what are the printouts for each machine when you open a terminal and type:
/sbin/ifconfig
cat /etc/hosts
cat /etc/resolv.conf

Best regards,
Dave

---

