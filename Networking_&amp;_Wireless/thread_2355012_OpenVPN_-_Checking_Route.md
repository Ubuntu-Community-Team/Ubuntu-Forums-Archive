---
title: "OpenVPN - Checking Route"
date: 2017-03-08
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-03-08
Folks,

I am experimenting with OpenVPN on a RaspberryPi running Mate and using 16:04 to access it.

I have enabled forwarding on the Mate device and I can PING the machine. I can ping another IP address but am not sure if it is going through the VPN.

I do not have the Firewall enabled (at the moment) but do I have to enable masquerading?

Traceeroute just gives me asterisks, any suggestions how I can check if traffic is going through the VPN?

Geffers

---

### Post by The Cog on 2017-03-08
Use tcpdump to print all the packets going in and out of the interface you are concerned about. e.g.
```
sudo tcpdump -np -i tun0 host 1.2.3.4
```
Specifying host 1.2.3.4 (use the VPN IP address of the host you are trying to make connections from) will stop it from reporting all the packets on your SSH session you are fault-finding from and all the packets the VPN is travelling over. If you sniff both tun0 (the VPN) and eth0 you should be able to work out where packets are going missing.

---

### Post by Geoff_Lane on 2017-03-08
Thank you for prompt reply and suggestion. Would this be run on the server or client machine?

Geffers

---

### Post by The Cog on 2017-03-09
This would be run on whichever machine you want to check that packets are passing on. I would first do it on the client. to make sure the packets are being sent into the tunnel. Then on the server tunnel to make sure the packets arrive, then on the server ethernet to make sure they are being forwarded. Also if the forward pathi is delivering packets OK, don't forget the return path for the reply packets - both directions need to work.

---

### Post by Geoff_Lane on 2017-03-09
Thanks Cog - will work at that.

---

