---
title: "Can't access internet"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Paul1944 on 2010-09-22
Hi!  I am very new to Ubuntu - running Desktop 9.04 - I can't ping -or- access the internet.  My ifconfig says:
eth0  Link encap.......
        UP BROADCAST MULTICAST......
        RX.....
        TX.....
        collisions 0......
        Interrupt 29
eth1  all the same - except
        Interrupt 31
lo      Loopback
        inet addr 127.0.0.1
The eth0 and eth1 do not have 'inet addr' entries
Can anyone give me some clues - I have installed the same version on another box -but- have upgraded it to 9.10 (via: internet)  I haven't done anything different (that I know of) but somehow the internet is unavailable on the new box...  The new box is a HP proliant DL-380
Thanks,
Paul

---

### Post by spiky001 on 2010-09-22
Dose Network manager have a tick by enable networking, I assume eth0 is a wired connection

---

### Post by Paul1944 on 2010-09-22
Yes it is a Wired Connection
Network Connection Window says:
   Auto  eth0   never
   Auto  eth1   never
Device - Network Tools says:
ipv6      ::      0             Unknown
ipv4  0.0.0.0   0.0.0.0  
Looking again at the ifconfig I see that I both eth0 and eth1 have
   inet6 addr   some hex stuff /64 Scope:Link

---

### Post by spiky001 on 2010-09-22
try 
```
sudo ifconfig eth0 up
```

---

### Post by Paul1944 on 2010-09-22
I tried the   sudo ifconfig eth0 up  -but-  nothing seems to have changed...

---

### Post by nlsthzn on 2010-09-22
DHCP enabled?  (I am at work currently and not in front of an Ubuntu box so I am not sure how to let you check :o)

---

