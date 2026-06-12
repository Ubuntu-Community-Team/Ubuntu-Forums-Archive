---
title: "Problems with Wireless Access Card List (MAC Address)"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by odelay on 2006-11-17
Since using WEP was annoying me, and using WPA apparently doesn't work with ndiswrapper, I decided my method of security for my home wireless network would be to have the router only allow specific MAC addresses to use the connection.  I have a Netgear WGR614 v6 router.

I would understand if it completely didn't work or if it consistently worked, but the reality of the situation is somewhere in between.  When I first set it up everything was working perfectly.  In fact, it usually works perfectly.  The problem is (now for the second time) it just stops getting an IP address.  I'm able to connect fine to other local unsecured connections, but not my own.  When I first encountered this, I didn't think the problem was coming from the connection so I spent several hours messing around with everything.  Suddenly, it started working again--probably completely independent of my tinkering.

Now it stopped again.  Any ideas what I can do--it doesn't seem to be a problem with ndiswrapper or my wireless card (BCM4311).  Any ideas what I can do?

Thanks in advance.

---

### Post by FrodoB on 2006-11-17
Well WEP is more secure than MAC filtering, so I would just dump it.

I don't use WPA, but it is possible, see this article:

[http://www.enterprisenetworkingplanet.com/netsecur/article.php/3594946](http://www.enterprisenetworkingplanet.com/netsecur/article.php/3594946)

So WEP or WPA is the best way at this point.

---

### Post by odelay on 2006-11-17
Thanks for the info **FrodoB**.  Security isn't really my main fear though.  If I'm just doing MAC filtering, WPA, or merely hiding the SSID there isn't much stopping someone from having their way with me.  I live in a small, semi-isolated apartment with only 4 units, and the chance of someone attempting to hack into my connection is small enough that I can live with it.  My real concern is my neighbors eating up my limited bandwidth.  In reality, simply choosing to hide my SSID would be enough of a deterrence for them--however Ubuntu/ndiswrapper can't seem to handle this (?!?!).  So what I want is the most hassle-free boundary preventing someone from double-clicking my connection in their wireless setup tool...nothing actually "secure" is needed (but wouldn't hurt).

MAC filtering seemed the easiest--my roomate's PC has trouble with using WEP.  If there's no workaround to MAC-filtering working reliably Ubuntu now, I guess I'll go back to WEP in the meantime.

And if I'm not mistaken, WPA-supplicant does not work with ndiswrapper, therefore WPA doesn't work (unless this has changed recently).

---

### Post by FrodoB on 2006-11-17
Well actually it does now supposedly. I am not a big ndiswrapper fan. I admire the folks who did it because they are filling a real need, but I prefer to find devices that have native drivers.

At any rate, I do use it on one device and for that device it does great. Here is a writeup on how to use wpasupplicant and it shows how to work with ndiswrapper. I have not used it, but it looks through:

[http://www.neowin.net/forum/lofiversion/index.php/t399787.html%20Modified=F0783171440AC70120](http://www.neowin.net/forum/lofiversion/index.php/t399787.html%20Modified=F0783171440AC70120)

It may do what you need. 

On my one card I am using ndiswrapper 1.28 on Edgy, so if the one you have does not work you may want to try it.

Here is my experience with the one device that I use ndiswrapper on. It includes all of the links to the ndiswrapper stuff:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

You probably know more about it than I do, and maybe you can answer my only concern about it.  The device/ndiswrapper insist that I use the keyword "wireless-key1" rather than plain "wireless-key".

Good Luck with whatever you decide to do.

---

### Post by odelay on 2006-11-17
Thanks so much--I'll have to give WPA a shot sometime soon.  Perhaps I'll have time to mess around with it on Thanksgiving weekend.  Good to at least know there's a chance; I had already given up on it.

---

