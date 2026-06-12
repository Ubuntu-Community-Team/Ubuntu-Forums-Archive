---
title: "vpnc Timeout?"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by JimmyJam4PHP on 2008-10-16
I am attempting to switch over from the Cisco VPN Client to vpnc.  I am connecting properly and I can ping and query systems on the VPN.  However, if I leave the connection idle for what seems like only a few seconds, it seems to disconnect.  I get no access to the systems on the VPN and I cannot access the Internet any longer. Once I run vpnc-disconnect I get my Internet connection back.  I am using the following to start the connection:
```
sudo vpnc --natt-mode force-natt --dpd-idle 0 ClientVPN
```

I have tried this with dpd-idle set to 86400 but it makes no difference.

Thanks in advance,
~JimmyJam

---

### Post by JimmyJam4PHP on 2008-10-17
Ok, a little more detail.  I've done some researched that suggested using --nat-keepalive, but that does not exist for the latest version of vpnc in the Ubuntu Repository (0.5.1r1).  I have also tried 0.5.1r334 with no luck.  I attempted to continue pinging a system on the other network but even that fails after about 30 seconds.  Any help is greatly appreciated.

---

### Post by JimmyJam4PHP on 2008-10-17
Ok, so I fired up wireshark and created a new connection.  By looking at the ESP Packets I can tell that I am receiving a response from the other end for the first 23 or 24 seconds.  I see no other traffic on eth0 or tun0 that would suggest a disconnect, I just stop receiving packets.  I have included a screen shot (note that the connection was established at 31.5 seconds).

---

### Post by bunchipe on 2009-10-08
Alternatively add the line

DPD idle timeout (our side) 0

to your .conf file in /etc/vpnc and I think that will effectively resolve the timeout problem.

For example:

IPSec gateway <your_gateway>
IPSec ID linux
IPSec secret <your_group_password>
Xauth username <your_username>
DPD idle timeout (our side) 0

---

