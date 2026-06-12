---
title: "Renew IP Address Too Often"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by elicoten on 2007-05-28
[FONT="Franklin Gothic Medium"]Hi

I'm trying to use the built-in VNC server in Ubuntu, and all seems to be working well except one extremely infuriating problem. I don't know why or how this started, but it seems that every few minutes the IP Address changes. I'm using DHCP configuration, and when I run dhclient manually I get told that the lease time. Each time I run dhclient I get a different lease time but they're all around 200-250 seconds, which if my understanding is correct means that I would not be able to use VNC for more than about 4/5 minutes before needing to reconnect it using the new IP address.

How can I stop this problem and change the lease time to something more reasonable?

Thanks,
Eli[/FONT]

---

### Post by elicoten on 2007-05-29
Bump

---

### Post by elicoten on 2007-06-18
Bump...

---

### Post by \\slash on 2007-06-18
DHCP lease times are set at the DHCP server, not the client. Check your router's DHCP settings for a way to reconfigure your lease time.

---

### Post by kevdog on 2007-06-18
Just my two cents

I used to run a VNC server on Linux Box (now FreeNX), anyway the point is that why do you want to use a dynamic IP address.  Why dont you set up your /etc/network/interfaces file so that your computer is assigned a static IP address.  That way your router will always know the IP address to port forward to.

---

### Post by Mr. C. on 2007-06-18
A DHCP client will request the same IP address, and the server should grant that IP if it is available.

I'm guessing that you have a wireless router and that the connection is being dropped periodically, and upon renewal attempt, the DHCP server on your router cannot grant the lease request for the previous IP, as it sees the IP as still in use.  When the connection is dropped, a RELEASE message is not sent, so the router cannot provide the previous IP address, so you get a new one.

Solve the disconnect problem and this will sort itself out.

MrC

---

### Post by elicoten on 2007-12-24
The computer in question wasn't wireless - it was actually a virtual machine with a virtual ethernet connection - but I think it has may now been corrected by an update of Ubuntu.

---

