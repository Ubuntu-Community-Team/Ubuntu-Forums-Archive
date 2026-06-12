---
title: "Sharing USB 3G modem internet connection over wifi network"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by skinnny on 2007-08-13
Hi, I'm new to Linux and networking stuff and I'm having trouble with this, and I don't know if it's even possible.

I'm running Ubuntu 6.10 on a desktop pc.  It's connected to the internet using a Huawei E220 3G USB modem.  I also have Belkin Wireless G Router, which I want to use to set up a wireless network at home, that other computers (mostly XP based laptops) can use to connect to the internet.

I have the router connected to the ubuntu pc, and have used the web-based interface to set up the SSID, security and stuff.  I can see and connect to the wifi network (but not the internet) from a laptop.  I have no indication that the ubuntu pc is "aware" of the network... it doesn't have wireless capabilities... I didn't think this would be a problem as it's wired to the router.  Is that correct?

The router has a network socket to connect a modem to it, and I'm guessing that if I was connected to the internet by a wired modem, I wouldn't be having these problems.  Does a router have to sit between the modem and the pc to share the connection?

Is what I'm trying to achieve (ie sharing this internet connection over the wifi network) possible?

If so, please could someone point me in the right direction?

Thanks in advance.

---

### Post by antieco on 2007-08-15
Im on the same dance, if you got any answer please let me know.
Best wishes!

---

### Post by utakubeta on 2007-08-16
Hi I'm also in the same boat.
I THINK... you want to set up a bridge between ppp0 and your wifi card (whatever it&#347; called)

look here [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) for how to make a bridge.

since the box im doing this on HAS to work (IE not get screwed up by a bad bridge setting I can not yet try out this theory... so see if it works and let me know :)

---

### Post by skinnny on 2007-08-21
Well I gave up and took the router back :(

Sorry guys, hope you have better luck.

---

### Post by Ozibozi on 2008-02-16
Hi just went over your post. i found a product that could do the trick for you. it is called draytek. check it out on [http://www.draytek.com/product/adsl2plus/vigor2800i.php](http://www.draytek.com/product/adsl2plus/vigor2800i.php) but befor you buy check compatibility with your usb modem. here [http://www.draytek.com/support/support_note/router/faq/usb/10.php](http://www.draytek.com/support/support_note/router/faq/usb/10.php) i hope the information i provided is useful.

---

### Post by Neilbedwin on 2008-03-08
I am running something similar......

My Win desktop connects to the interent via the 3G dongle and the wifi router via ethernet cable. I can connect with my laptop using wifi and surf the web through the desktop machine.

How? I use the AnalogX proxy. It forwards all requests to servers that don't exist on my network to the internet connection. Surely Squid or someother Linux proxy would do the same (not tried it yet).

Neil

---

