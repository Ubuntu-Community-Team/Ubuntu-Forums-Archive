---
title: "wireless internet and cross cable connection together"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by ryu kun on 2006-11-08
I have connected my laptop to my desktop computer by a cross cable and transferred files successfully but I can't be online at my laptop while I am doing this.

I use Network Manager on my laptop in order to connect to my WPA secured wireless internet.

My wireless uses DHCP but a cross cable connection AFAIK needs static IP's.

Can you please tell me how can I make it possible? Thank you.

---

### Post by wieman01 on 2006-11-09
As far as I know you cannot have wireless & Ethernet enabled at the same time. Others may disagree but that's what I (and a number of others) have experienced.

---

### Post by FrodoB on 2006-11-09
You need to have both connections in the same subnet and it should work. Obviously you cannot have the same address on both of them. 

I am assuming that the wireless connection is to you access point and that is how you get net access.

You may need to run dhclient after they are both connected to get the routing correct as well, but maybe not.

---

### Post by ryu kun on 2006-11-09
If eth0 (ethernet) and eth1 (wireless) must use the same IP address to work together, it doesn't seem possible because Network Manager doesn't allow us to set an IP anywhere. 

It's sad that WPA isn't natively supported in Dapper (or Edgy) and Network Manager has still a long way to go.

---

### Post by wieman01 on 2006-11-09
Oh well... I is supported, of course. But setting it up is not as convenient as in Windows, I have to agree. NetworkManager is a fairly insufficient solution (DHCP only, etc.). If you are interested in WPA (or WPA2), give this thread a go:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by FrodoB on 2006-11-09
No, they must not have the same network address, only be on the same segment. If they have the same address they will not work.

---

### Post by wieman01 on 2006-11-09
> **FrodoB said:**
> No, they must not have the same network address, only be on the same segment. If they have the same address they will not work.
I was referring to WPA, not the issue you mentioned (same network address). Of course you're right.

---

