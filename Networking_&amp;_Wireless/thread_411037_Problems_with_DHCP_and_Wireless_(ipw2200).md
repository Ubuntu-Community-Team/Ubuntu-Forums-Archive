---
title: "Problems with DHCP and Wireless (ipw2200)"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by nukie77 on 2007-04-16
I am having problems getting a DHCP offer over wireless.  I have a card set up with the default ipw2200 drivers under eth1.  A 'iwlist eth1 scan' shows many results (I live in NYC) including my unencrypted network that I set up to get things working.  When I duel boot into windows, I can get a DHCP offer from it right away, however I always seem to timeout waiting for a DHCP offer with ubuntu.  Now, if I connect to the router through a cat5 cable, I will get a DHCP offer and be on the internet in no time.  Anyone have any ideas?

---

### Post by reauthor on 2007-04-16
which ubuntu you using,dapper.edgy,feisty.?

---

### Post by nukie77 on 2007-04-16
Oh, sorry.  I am using feisty now.  I couldn't get edgy to work either, but that was before I figured out it it wasn't a WPA issue.  I now have WPA off until I can get it to work.

---

### Post by reauthor on 2007-04-16
There is a litle bug in feisty network manager and many users complained..I have trouble too.So when I updated a feisty whith latest updates I dont take a updates for network manager & network-manager-gnome and wireless work perfectly...Does your wireless connection work whit no encryption?

---

### Post by nukie77 on 2007-04-16
NO, it does not work even without encryption.  I think that I am going to re-install feisty tonight without any updates to network-manager and see if I can connect that way.

---

