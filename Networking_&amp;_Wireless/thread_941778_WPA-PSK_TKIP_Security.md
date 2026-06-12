---
title: "WPA-PSK TKIP Security"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by cloudstrife_uk on 2008-10-08
Hi guys & girls,

Managed to get my Linksys WUSB54GS V2 setup pretty easily with Ndiswrapper.

Now then the WUSB54GS will show as being connected to the network but mm-applet connection details shows no IP address etc. Popped into Terminal and tried a dhclient command but comes back that it can't find an address to use.

Figured it maybe the security, so switched off all security on the router and it connected fine and I got online!!! But thought this is not too clever so moved to WEP at 128k and again no problems! Anyways thought I would move back to the routers default WPA-PSK security settings and it all grinded to a halt (luckly I have another laptop which connects fine with WPA-PSK as does my Pocket PC.).

Here is my specs:
Ubuntu - 8.04 Hardy Heron
Ndiswrapper - 1.52
Ndiswrapper Utils - 1.9
Wifi Card - Linksys USB54GSV2
Router - Netgear DG834GT (the special 'Sky' version)
Router Security - 8 character WPA-PSK TKIP code

Anyone got any ideas or is it a case of giving up and lowering the security levels on the router?!

Cheers,
Cloud

---

### Post by Swagman on 2008-10-08
I would be interested in an answer to this as well as my mate uses a laptop and sky and has the same issue.

He has XP installed but uses Ubuntu 8:04 installed via wubi.

Annoyingly XP connects without issue but even though the network is detected and asks for password etc...

No connection

Grrr

I even set my netgear router up with the same key and ssid as his and it connected no problems when he brought his laptop round my place.

[Exasperation]

---

### Post by tl3000 on 2008-10-08
> **cloudstrife_uk said:**
> 
Anyone got any ideas or is it a case of giving up and lowering the security levels on the router?!


Your posted symptoms resemble this confirmed bug at:

```
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207446)
```

The possible workaround with two implementations are at:

```
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207446/comments/46](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207446/comments/46)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207446/comments/52](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/207446/comments/52)
```


Swagman, this workaround will probably not work for you since from your description you may have a different issue.

---

### Post by Swagman on 2008-10-09
No worries.

Lets hope Intrepid Ibex cures it.

---

