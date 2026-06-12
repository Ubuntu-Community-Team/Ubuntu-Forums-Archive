---
title: "Remote file systems in /etc/fstab"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by mdh on 2006-10-27
Hello ubuntu users,

A question regarding mounting remote file systems. I have added mount commands in my /etc/fstab file to mount a couple of remote file systems through nfs. I am just wondering whether my system would boot normally if the machines containing those file systems are down. Is it safe to have these mount commands in /etc/fstab or should they be put in bash (or shell) startup scripts.

---

### Post by handy on 2006-10-27
Hi, from my experience you will have no problems if the rfs's are not online:  

Device not found, & carry on...

Out of interest did you mount them using IP's?

I did that having my machines all set up as server's, my cludgy NFS P2P home network.  But the problem that that caused, was that the addresses changed from time to time!

I also ran a script on each machine at boot time that automatically did a 2nd **mount -a**, after logging on, on each one to get  NFS working on all the "***server's***" :D 

It is pretty funny way to do it I think.  Eventually went back to 2 server's with 1 client each, as that is all that we needed.

---

