---
title: "Shared Wi-Fi connection not working on 17.04"
date: 2017-04-23
forum: Networking &amp; Wireless
---

### Post by Javier_Acosta on 2017-04-23
Hi there
I've just started to move from my old Kubuntu 14.04.4 install to the 17.04 release. Testing the live CD image, I noticed that even though the wireless interface seems to be working as it should (I can see/connect to other networks), when I create a shared Wi-Fi connection it doesn't appear on the network manager widget, as it would have in 14.04.
I tried changing nearly all parameters on the connection settings but no luck. If anything, the only thing i noticed is ```
IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
``` on dmesg but since the problem persists even when the option* IPv4 is required for this connection* is checked i dont really know what could be the problem! Any ideas? Thanks in advance

Edit: Added [complete wireless-info script output here]("https://pastebin.com/0c8uMhHL")

---

### Post by mörgæs on 2017-04-24
I recommend that you install and apply the first batch of updates using a wired connection. When this works we can take a look at the wirefree connection.

---

