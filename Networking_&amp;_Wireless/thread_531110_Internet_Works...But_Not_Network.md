---
title: "Internet Works...But Not Network"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by jwhiteman on 2007-08-21
Ok, So I have internet on both my wired cards and my wireless. I have set my server to a static IP.. Server is Ubuntu 7.04 and Laptop is 7.04. I cannot access either computer from the other via remote desktop or vnc. I keep getting "Detination Unreachable" when I ping. But both machines can ping the gateway.

Both machines are on the same net work... 192.168.x.x, etc...

I thought that this would be easier.  I need a network Guru to help!!

:confused:

---

### Post by renzokuken on 2007-08-21
might be a firewall issue. chack that you have the correct ports forwarded for VNC or remote desktop

---

### Post by timcredible on 2007-08-21
the ip address is only half the info - what's the subnet mask?  that will determine if they're in the same subnet or not.

---

### Post by jwhiteman on 2007-08-21
Subnet Mask is

255.255.255.0

---

