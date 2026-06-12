---
title: "Unable to access PC from public IP"
date: 2023-02-16
forum: Networking &amp; Wireless
---

### Post by JimLS on 2023-02-16
Have a pfsense firewall box with VPN client for access to local network from other locations.  Until recently I could access the 3 local boxes.  Recently the box running Ubuntu 20 cannot be reached.  The older (very old) ubuntu box and a raspberry pi both have web pages that can be accessed.  The Ubuntu 20 box has two network cards - one for local network and one for isolated camera network (runs zoneminder).  Have done some investigation and pfsense seems to be passing the traffic ok. It seems the problem box does not respond to ping requests or anything else with the external IP of the vpn tunnel.  I tried adding the IP to the Ubuntu 20 box with:
sudo ufw allow from 100.x.x.x   (used the actual IP - the x's are just placeholders)
That didn't solve the problem.  It still doesn't respond to pings or traffic from the public address.

What should I be looking at?  Seems strange that this worked until a few weeks ago.

---

### Post by TheFu on 2023-02-16
I'd check the routing priority for the 2 subnets.

---

### Post by JimLS on 2023-02-16
> **TheFu said:**
> I'd check the routing priority for the 2 subnets.

Could you give me some details on how to do this?  Haven't dealt with this before...

---

### Post by TheFu on 2023-02-16
```
ip r
```
is the command I'd use to start.  Then it is basic networking knowledge.  There are lots of tutorials about that. Google for "how the internet works", if you need more.

---

### Post by The Cog on 2023-02-17
**ip route** doesn't always tell you the whole story, it just *usually* does. The final check would be to ask for the route to the destination you are worried about, e.g. **ip route get 100.1.2.3** .
You may find that the box ignores packets arriving on the "wrong" interface (i.e. not the one that ip r g says). In your case, that would be because the routing is configured wrongly.
Use tcpdump to see if the packets are actually arriving and leaving the interface.

---

