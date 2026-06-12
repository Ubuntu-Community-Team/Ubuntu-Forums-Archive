---
title: "Two Internet connections, 1 doesn't get IP"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by beckols on 2008-07-14
I have three ethernet connections on my Ubuntu 8.04 server.  One goes to LAN, the other two are supposed to be hooked up to two separate DSL lines.  One plugged in works fine (either modem), but when I plug both of them in, only one gets an IP address, the other doesn't.  I've tried ifdown && ifup on both, /etc/init.d/networking restart, etc..  I don't know what to do.  Once I get both of them up and running, I can set up the split access and load balancing, but until it receives an IP address from the ISP, I can't do anything.  Any ideas??

---

### Post by minimec on 2008-07-14
Hi

When I read your question, I said to myself... 'easy one...'. Then I opened my /etc/network/interfaces and... the file only mentioned my 'lo' device and not my 'eth0'... So I had to think.

It seems clear for me now, that the network-manager handles all that stuff, and so the /etc/network/interfaces file is less important (...and not configured for the network devices).

I guess, that if you configure your DSL devices in the /etc/network/interfaces file, both cards will get an ip.

Configuration would probably be like this...

# The primary network interface
iface eth0 inet dhcp

# The secondary network interface
iface eth1 inet dhcp


regards... Minimec

---

### Post by beckols on 2008-07-14
My /etc/network/interfaces file is configured just like that.  Both are set to DHCP, and my LAN is set to static with all the right options, so that's not it.  Thanks for the reply, though.

---

### Post by minimec on 2008-07-14
Hi again..

found a german post with a similar problem. [http://www.tecchannel.de/forum/linux-unix-andere/6679-ubuntu-8-04-2-network-interfaces.html]("http://www.tecchannel.de/forum/linux-unix-andere/6679-ubuntu-8-04-2-network-interfaces.html"). 

He found out, that using a 2.6.22.* Kernel solved his problem. Could be worth a try...

regards minimec

---

### Post by beckols on 2008-07-14
Google translation was brutal for that post, I couldn't understand most of what it was saying.  I'm not sure if I want to downgrade the kernel, shouldn't there be a fix for the current kernel for this?  I have no experience in messing with the kernel either.  I will look into it, but it seems like this would be a major feature that would need to be fixed.

---

### Post by beckols on 2008-07-14
Anyone else have any input on this?  Could there be a way to get it working without downgrading the kernel?

---

### Post by beckols on 2008-07-15
bump

---

### Post by wuzer on 2008-07-19
Hello,

In the german post is the solution for his problem:
[http://www.tecchannel.de/forum/linux-unix-andere/6679-ubuntu-8-04-2-network-interfaces-3.html#post30419](http://www.tecchannel.de/forum/linux-unix-andere/6679-ubuntu-8-04-2-network-interfaces-3.html#post30419)

post: "BIOS-Reset mittels Jumper setzen."

He made a BIOS-Reset by setting a Jumper

---

### Post by beckols on 2009-05-19
This was a while ago, but I thought I would close the ticket. Apparently, the ISP (or possibly it's the fault of the modem(s)) will not allow a machine to receive a new DHCP lease so quickly while the current lease is still good. This seems moderately obvious now or else people would be taking out multiple leases all the time. I just have to remember in the future to have room for bit of downtime if I'm going to switch hardware.

---

### Post by Iowan on 2009-05-19
Have you tried releasing the lease with **dhclient -r**, then trying to acquire a new one?

---

### Post by beckols on 2009-05-20
> **Iowan said:**
> Have you tried releasing the lease with **dhclient -r**, then trying to acquire a new one?

Yea, sure did.  No good unfortunately.

---

