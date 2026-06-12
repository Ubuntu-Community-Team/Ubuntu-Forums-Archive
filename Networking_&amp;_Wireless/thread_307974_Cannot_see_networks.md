---
title: "Cannot see networks?"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by CrazyDesi on 2006-11-27
Hey even though I have network manager I cannot see the networks in edgy.  I could in dapper however.  Anyone know how to fix this?  I know you can do it in command line i just forgot how to refresh the dhcp.  I know you can iwlist scan and then iwconfig eth1 essid "essid" but I forgot how to refresh.  So if someone doesn't know the reason I can't see networks can they just tell me that command I can't find it on google.

---

### Post by cilynx on 2006-11-27
```
ifdown eth1 && ifup eth1
```
that'll take the interface down and back up however you have it configured to do so

---

### Post by CrazyDesi on 2006-11-27
Thank you.  Anyone know how to make it be seen in Network Manager.

---

### Post by cilynx on 2006-11-27
Verified by a few others -- it's broken in Edgy and Feisty

---

### Post by CrazyDesi on 2006-11-27
Ah.  Well is there a way to compile it yourself or apt-get something to make essid hunting working again?

---

### Post by cilynx on 2006-11-27
Unfortunately not that I've discovered.  I'm pretty sure if you try to downgrade just that part, you're going to run into dependency hell.  I just setup profiles for the three different networks I'm on and leave it at that.

---

