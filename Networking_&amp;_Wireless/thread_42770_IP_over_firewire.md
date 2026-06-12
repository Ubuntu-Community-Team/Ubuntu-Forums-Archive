---
title: "IP over firewire"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by coriolan on 2005-06-19
Hello,

I have two computers: a Mac and a Linux box. What I am trying to do is to use the linux with the Mac since I have only one keyboard and monitor. I connected the two tubs with Firewire and I even managed to get the eth1394 working. Now when I add eth1394 to /etc/modules I can no longer connect anywhere with neither eth0 nor eth1! But if I comment that out, reboot, and ```
$ sudo modprobe eth1394
``` everything works fine. I can ping the computers from each other, but I cannot get vnc working. I am using the *Chicken of the VNC from the Mac*, but it says that *The server closed the connection* when I try.

---

