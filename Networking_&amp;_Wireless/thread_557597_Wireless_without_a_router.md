---
title: "Wireless without a router?"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by FuturePilot on 2007-09-22
Is there a way to set up a wireless network without a router? I'm thinking of something like this:
[IMG]http://www.microsoft.com/library/media/1033/windowsxp/images/using/networking/setup/68588-diagram-ad-hoc.gif[/IMG]

If so, is there a guide somewhere on how to do this, or can someone tell me how to do this?

---

### Post by reckless2k2 on 2007-09-22
you'd have to buy an aircard from verizon, t-mobile, or att.

---

### Post by HermanAB on 2007-09-22
Some WiFi adaptors can act as an access point.  You need to install special software to do that:
[http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html](http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html)
[http://www.ibm.com/developerworks/linux/library/l-wap.html](http://www.ibm.com/developerworks/linux/library/l-wap.html)
[http://wireless.gumph.org/content/4/7/071-linux-based-ap.html](http://wireless.gumph.org/content/4/7/071-linux-based-ap.html)

Cheers,

Herman

---

### Post by reckless2k2 on 2007-09-22
i guess you threw the pic up after i replied. better description helps. 

yes you can do that. easy way is if you have an old box laying around and use smoothwall or ipcop.   you can do it off a workstation but there is no "easy" way to do it and instructions are everywhere. 

"easy" way is with a firewall router with like smoothwall. works on OLD boxes.

---

### Post by FuturePilot on 2007-09-22
Yes, probably should have explained more. I thought the picture was enough:p
So basically what I want to do is have one of my desktop PCs act as a router, so then I could get a connection to my laptop. The PC is hooked up to a land line so I was wondering how I could get a wireless connection to the laptop by just using the PC as the router.

---

### Post by Dark Hornet on 2007-09-22
--Just wondering...but why wouldn't you just buy a wireless router?

---

### Post by mojoguy on 2007-09-22
Answer: Yes

How to: Don't know.
Presuming you got the gateway nics configured correctly and the wireless one to act as an access point, then perhaps you could use squid?  

I'm really talking out my kiester, but it's a cool question and I haven't tried to do anything like this.

---

### Post by FuturePilot on 2007-09-22
> **Dark Hornet said:**
> --Just wondering...but why wouldn't you just buy a wireless router?

Yes, I have thought about that. But the last time (and the first time) I tried a router it was the worst experience ever. It completely slowed my connection speed way down on my PC that was connected to the land line. I mean painfully slow, and by the end of the day I couldn't connect to the internet anymore. Ended up returning it. So I've been somewhat wary of buying another one.

---

### Post by jabagawee on 2007-10-07
I'm gonna take a REALLY wild guess here. You bought a Linksys router. Then you used BitTorrent. And then your internet slowed to a halt. If I'm right, then you should look into DD-WRT or another alternative firmware for a router and changing some configs. It solves all Linksys-BitTorrent problems.

---

