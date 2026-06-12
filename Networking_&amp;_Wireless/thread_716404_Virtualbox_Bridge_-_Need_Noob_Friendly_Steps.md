---
title: "Virtualbox Bridge - Need Noob Friendly Steps"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by TheSe7enthSin on 2008-03-05
Ok, so I have searched around & read many different guides. But honestly, most of them are a little confusing. I'm not too much of a noob, I've been using Ubuntu for a little over a year. But I just want things told to me in a step-by-step that is easy to understand layout.

I want to bridge Virtualbox running Windows XP (guest) with Ubuntu (host), so that Windows can have an ipaddress assigned from the router.
I have Ubuntu 7.10 & I'm using wireless.

One of the guides I tried was: [http://ubuntuforums.org/showthread.php?t=346185&highlight=virtualbox+bridge+network](http://ubuntuforums.org/showthread.php?t=346185&highlight=virtualbox+bridge+network)
From this guide, I keep getting an error when entering the command

```
sudo /sbin/dhclient br0
```

I would get: No DHCPOFFERS received. No working leases in persistent database - sleeping.

Please help me out here. =)

---

### Post by ulver on 2008-03-06
You got that message beacuse you dont have a DHCP server on the network or the router isnt in routing mode. Try assigning static IPs, for example 
```
ifconfig eth0 192.168.0.2 netmask 255.255.0.0
```

---

### Post by TheSe7enthSin on 2008-03-06
Hmm. My router seems to be in routing mode & is also set to DHCP. Every device that connects to my networks automatically gets an IP assigned. I'm using the Linksys WRT54GS.

I'll try that command though. But isn't eth0 the wired connection?

---

