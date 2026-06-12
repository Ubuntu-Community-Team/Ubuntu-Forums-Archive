---
title: "[SOLVED] VoIP in a university network (VPN etc.)"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by der_vegi on 2007-09-28
Hi!

I've got the following problem: My only internet connection is over the network of my university, I connect with vpnc and internet only works over a proxy. Not even POP and SMTP ports are opend, only SSH and port 443. Skype connects over that port, Jabber and email are running over a SSH tunnel. But I really want to get rid of Skype, using Ekiga, Wengophone or so. Is there the possibility to let them use a SSH tunnel or port 443 like Skype does?

Thanks for the help!

---

### Post by der_vegi on 2007-10-06
Okay, I got Wengophone working, using the same method Skype uses automatically:

In the advanced configuration window, I set 'proxy detected' to 'true' and set the proxy port and server. I also set 'network tunnel needed' to 'true', 'network tunnel port' to '443' but left the 'network tunnel server' blank (I think, Wengophone uses the proxy then.).
Wengo works now and if I use a jabber account, I have to set the network settings for this separately (forwarding ports over SSH).

Didn't get Ekiga to work, though. :(

---

