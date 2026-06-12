---
title: "KNetworkManager Hangs at 28%"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by khoda on 2007-06-01
I have a Lenovo T60 laptop with an Atheros AR5212 wireless card. KNetwork manager recognized my card. 

When I click on the KNM icon, it picks up signals from wireless routers around my house. When I try to connect to my router, it hangs at:

"Activation Stage: Configuring Device" (28%). 

At first I thought it was a problem with WPA, so I changed to WEP (didn't work). Next I thought it was a problem with encryption, so I disabled encryption (same problem). Any advice would be great!

Thanks

P.S. : I saw that a similar question was asked, but not answers. Hope this is okay :)

---

### Post by handydan918 on 2007-06-01
This appears to be a common problem. There is a threas on this problem at the mepislovers.com site [here.]("http://www.mepislovers.org/forums/showthread.php?t=7427&page=2")
Perhaps you can glean some info from it, although some of the recommendations are specific to MEPIS.

---

### Post by auisce on 2007-06-02
We're all having the same problem. I'm looking for a new, USABLE distro.:(
[http://kubuntuforums.net/forums/index.php?topic=3082946.0](http://kubuntuforums.net/forums/index.php?topic=3082946.0)

---

### Post by khoda on 2007-06-02
After broadcasting my SSID I was able to connect to my WPA encrypted connection.

---

### Post by handydan918 on 2007-06-02
> **auisce said:**
> We're all having the same problem. I'm looking for a new, USABLE distro.:(
[http://kubuntuforums.net/forums/index.php?topic=3082946.0](http://kubuntuforums.net/forums/index.php?topic=3082946.0)

I wouldn't be too quick too jump ship. I also use MEPIS, and the same problem exists there. I got around it by uninstalling knetworkmanager and using knemo and wlassistant instead.
I thought it was just because of my *%&#$@## broadcom 4318 chip...:D

---

### Post by tekg on 2007-06-03
this is a CRITICAL bug. It makes me severly doubt the KDE / Ubuntu quality control process. Why bother to release something that is _KNOWN_ to not work correctly? not to mention knetworkman is a POS anyways (uses kwallet for saving WEP password??????). Also it has no autoconnect feature. Its a terrible piece of software and a pity it uninstalls wlanassistant when it is added. This and ubuntu's TERRIBLE support for ATI cards are seriously holding the distro back (for example 6.10 at least starts xserver so you can fix ATI problem yet the NEWER version completely brocks on first boot if you install it without first installing 6.10 and then installing ATI drivers manually). Good luck getting this changed as the ubuntu people are obvs nvidia fanboys. /rant

a workaround I have encountered for knetworkman hanging is to attempt to log into a WEP protected network. When this in turn stalls at 58% or so, connect to your regular network. Should work alright, but I'm still looking for a way to disable knetworkmanager.... such a terrible application ack!

---

