---
title: "[SOLVED] Is someone hacking me?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Redrazor39 on 2008-05-27
Comodo firewall pro in vista business stopped 32 intrusion attempts to SYSTEM

screenshot is attached.

Is someone hacking me? What do I do?

---

### Post by Tatty on 2008-05-27
The source IP addresses seem to be coming from within your own network. 192.168.x.x is usually reserved for home networks.

---

### Post by amingv on 2008-05-27
I don't think so. The remote IP looks like it's part of your LAN (at least the ones one can see), and if someone is indeed cracking you from inside your network they're already in too deep.
If you have a router then check the logs and see if there's been an external attack attempt and it's not some 'system' program looking for services in another pc.

---

### Post by zmjjmz on 2008-05-27
You have a Linksys router I suppose?

---

### Post by Dr Small on 2008-05-27
[http://www.iss.net/security_center/advice/Exploits/Ports/139/default.htm](http://www.iss.net/security_center/advice/Exploits/Ports/139/default.htm)

But that doesn't mean a thing. I have been packet sniffing my own network before and seen NetBIOS packets being broadcasted by the Windows machine.

No, I do not think you are under attack, unless someone has already gained access to another system on your network and are attempting from that system as a network proxy.

Dr Small

---

### Post by tcpip4lyfe on 2008-05-28
No.  Those are just netBIOS browser elections.

---

### Post by 3rdalbum on 2008-05-28
> **Redrazor39 said:**
> Comodo firewall pro in vista business stopped 32 intrusion attempts to SYSTEM Is someone hacking me?

You really answered your own question: Comodo *stopped* 32 intrusion attempts, so with the information you gave us, it looks like nobody is hacking you, because they can't get in.

But with less humour, the 192.168 looks like it's coming from your own network. Probably another computer sending useless packets to the network - believe me, they can do this even when turned off. One of mine does.

EDIT: Why do you have a personal firewall as well as one in your router? Is there a reason why you don't trust the fabric of your own network? If you suspect someone on your local network is doing this, you should check on everyone currently using your network.

---

### Post by Redrazor39 on 2008-05-28
Thanks. We just bought a new iMac and it may be looking for other comps on the network. I just wanted to make sure.

Idk if I have a firewall in my router. It's only WEP security and I just enter a pass and get in, so I thought Comodo firewall would be a wise choice for my Vista partition just in case.

I'm no expert on wireless security or anything, but thanks for all the help :)

---

### Post by Dr Small on 2008-05-28
WEP can be cracked within minutes. Use WPA for security.

---

### Post by Redrazor39 on 2008-05-28
1) How do I get WPA instead of WEP

2) Can someone crack into it from anywhere online or does it have to be in range of the wireless network?

---

### Post by K.Mandla on 2008-05-28
Moved to Networking and Wireless.

---

