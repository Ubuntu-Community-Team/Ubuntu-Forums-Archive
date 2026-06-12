---
title: "Networking Issue"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by HarisShahzad on 2014-03-16
I have 3 laptops at home. Two run windows and my personal laptop runs ubuntu which I installed a couple of days ago.
Now call me a retard or paranoid even though im not sure if thats the correct word to use here but every time I turn on ubuntu and start using the internet, it slows down on my other two laptops and my family constantly complain of a very slow internet. The internet also slows down on my windows phone, Lumia 620. It slows down to the extent that even google wont open and thats on a 4Mb connection.
The second I shut down ubuntu, the internet seems to speed up again.

---

### Post by SeijiSensei on 2014-03-16
That's certainly not a common experience.

Not running torrents, are you?

---

### Post by untrustytahr on 2014-03-16
Check for conflicting (duplicate) IP addresses.  Particularly with the gateway address if all devices are affected.

---

### Post by HarisShahzad on 2014-03-17
Not running torrents at all.
Could you elaborate on the duplicate IP address issue

---

### Post by SeijiSensei on 2014-03-17
If all the devices on your network are using DHCP to get their IP addresses from your router, then there should be no conflicts.  If you haven't customized your router configuration, you might consider resetting it to factory defaults just to make sure.  Usually there is a small button on the back of the router for this task.  

If some of the machines on the network have static IP addresses, it's possible that two machines are configured to use the same address.  As untrustytahr observes, that could cause the problems you are reporting.  How did you configure your Ubuntu machine to get an address?

---

### Post by untrustytahr on 2014-03-17
SeijiSensei is correct.  Misconfigured static IP's and incorrectly configured (or rogue) DHCP servers could cause duplicate ips.  You didn't happend to install the DHCP server during the ubuntu install did you?  It's been a while since I've run through the ubuntu installer. I don't think the desktop version would give you that choice, but the server version might.

Most OS'es today play well resolving conflicts, but not always.

---

### Post by HarisShahzad on 2014-03-19
tried everything
nothing worked :/

---

### Post by SeijiSensei on 2014-03-19
I presume the laptop uses a wireless connection?  If you're using Ethernet instead, try a different cable.

---

### Post by HarisShahzad on 2014-03-20
Using wirless connection

---

