---
title: "DNS name resolution problem...I think..."
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-03-22
Someone sent me this e-mail.  I'm thinking the problem he is having has to do with DNS resolution, but I'm not sure how to fix it:

> I am trying to get Ubuntu working to access the internet. I have a window’s XP machine connected to a 2Wire combination dsl modem/rounter. I have the Ubuntu machine connected to a Linksys WET54G wireless ethernet bridge. The link is fine. If I connect the window’s machine to the bridge, I can access the internet. On the Ubuntu machine, I can see the WET54 AND the 2Wire gateway if I set the ethernet to a fixed IP address. However, when I try to access the internet, I cannot see any sites that are not explicit IP addresses. When I switch the Ubuntu machine to dhcp, I cannot see either the bridge or gateway or the internet either. I did connect the Umbuntu box directly to the rounter and it did work OK for the internet when set to DCHP. So… What is different when I connect the Umbuntu machine to the WET54? I’m lost and neither AT&T or Linksys tech support will talk to me when I mention Linux is part of my system.

Thanks!

What do you think the cause of his problem is?

---

### Post by daniel. on 2008-03-22
It sounds like DHCP from Ubuntu to the WET54 is failing completely.

First, regarding static IP addressing, did this person explicitly set the DNS server (/etc/resolv.conf or through network manager)?

It would be nice to see

```
cat /etc/resolv.conf
```

Second, regarding DHCP,
we need the output from

```

sudo dhclient
sudo ifconfig 
sudo iwconfig

```

At one point my Ubuntu box wasn't running dhclient automatically, and everything would work once I ran it. If dhclient fails, the link actually is fine, AND windows can connect via DHCP, then we'll have to go back to the drawing board.


Cheers,

Daniel

---

### Post by diablo75 on 2008-03-23
It appears to be a problem with the wireless bridge.  From what I found on the web about that particular bridge, it doesn't function as a DHCP server, so when you set Ubuntu to DHCP, nothing works.  I think the reason it did work with his Windows system is (possibly) a pre-cached DNS address being reused before it expired.  Just a chance...

I've asked him to modify his resolv.conf file, and set his address statically.  I'll check back when I hear from him if it works.

---

