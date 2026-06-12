---
title: "OpenVPN stopped working, no error messages"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-09-22
I have OpenVPN from my machine, so that my wife can access a specific folder from her machine.

It has been working flawlessly since I installed it a couple of months ago. My wife last used it on Friday.

Today, however, it has stopped working. There is no error message when my wife tries to connect.

I've tried loading all the programs manually so that I can see the message logs, but the only error message I see is from openvpn:
> TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
TLS Error: TLS handshake failedThat's hardly helpful to me.

Both computers are connected to the same router; both can access the Internet; both can ping each other over the network; my wife's machine can ping mine via dnsalias.org.

What to do next?

---

### Post by sahabcse on 2009-09-22
similar issue,this may help [https://forum.openwrt.org/viewtopic.php?pid=67828](https://forum.openwrt.org/viewtopic.php?pid=67828)

---

### Post by Paddy Landau on 2009-09-22
> **sahabcse said:**
> similar issue,this may help [https://forum.openwrt.org/viewtopic.php?pid=67828](https://forum.openwrt.org/viewtopic.php?pid=67828)
Thank you!

I had to reboot my router a couple of days ago. It turns out that it changed the IP address it had reserved for my computer, so it was forwading the requests to the wrong place.

I changed it and it all works now.

---

