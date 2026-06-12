---
title: "Shall I just buy a 2nd Router as Bridge to bypass Wlan Card Problems?"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by sulu on 2007-02-28
Soo, I have a RT2500. And it doesn't work. I've been trying since Dapper release day, and I haven't managed to get it to work with WPA2. I'm sure there is some way, but I'm no Guru yet and it' s hard to do stuff when you don't have a Inet connection in the first :D

So.. I've been to a friend of mine and installed 2 Linksys WRT54GL's at his house. The first one is connected to the Modem the second one is connected to the first one, as Bridge. And his computer is simply plugged into the second router. We did this for a number of reasons but they are of no concern to this now.

So I've been thinking, before i buy 2 more cards for 40 Euro that won't work, why not buy a 2nd router for 60 euro directly and use a similiar setup for myself.

So what do you folks think about this? Are there any Problems to be expected by using this on daily basis ?

Are higher pings in games to be expected or other problems with port forwarding or anything? Is there anything speaking against using this to simply circumvent all the Wlan Setup Stress?

I appreaciate all your suggestions and opinions, best regards.

---

### Post by dmizer on 2007-02-28
this doesn't sound like a very decent solution for a number of reasons.  first of all, the only place you will be able to use this set up is at your residence.  that is, unless you decide to carry your second router around with you everywhere you might want to make a wireless connection to.  if you're going to go through this much trouble to make an internet connection for home use only ... just run ethernet cable, it's safer, more reliable, and way more secure.

otherwise ... just purchase a wireless card you know will work in ubuntu: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by chili555 on 2007-02-28
You need a wireless ethernet bridge, such as, but not limited to this: [http://www.amazon.com/D-Link-DWL-G810-Ethernet-Wireless-Adapter/dp/B0000CEPCH](http://www.amazon.com/D-Link-DWL-G810-Ethernet-Wireless-Adapter/dp/B0000CEPCH)

I used a Linksys WET11 (doesn't support WPA) for many years for exactly the reasons you mention. I could never quantify that downloads, etc. were any slower than my wife's machine that is wired directly to the router. In this case, 11 Mb/s is far faster than the throughput I was able to get from my ISP. When I got a new kernel, it worked. When I switched from Mandrake to Red Hat, it worked. No matter what, it worked. Actually it still works!

Works well, but deprives you of the joy of screaming, "I got it! I flippin' got it!" at 2:35am and knocking a cold cup of coffee into your keyboard when your wireless card from hell finally works.

---

### Post by sulu on 2007-02-28
> **dmizer said:**
> this doesn't sound like a very decent solution for a number of reasons.  first of all, the only place you will be able to use this set up is at your residence.  that is, unless you decide to carry your second router around with you everywhere you might want to make a wireless connection to.  if you're going to go through this much trouble to make an internet connection for home use only ... just run ethernet cable, it's safer, more reliable, and way more secure.

otherwise ... just purchase a wireless card you know will work in ubuntu: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)


We're talking about a workstation computer here that weighs, due to some modifications like 40 pounds. If im gonna move it moving the router will be no problem.


What im plannign to use is 2 of these: [http://www.amazon.com/Linksys-Cisco-WRT54GL-Wireless-G-Broadband-Compatible/dp/B000BTL0OA/sr=8-1/qid=1172713373/ref=pd_bbs_sr_1/002-0329917-1856861?ie=UTF8&s=electronics](http://www.amazon.com/Linksys-Cisco-WRT54GL-Wireless-G-Broadband-Compatible/dp/B000BTL0OA/sr=8-1/qid=1172713373/ref=pd_bbs_sr_1/002-0329917-1856861?ie=UTF8&s=electronics)
and flash their software to DD-WRT.

Mainly because I already have one of these, they're not much more expensive than a decent wlan card and because I have installed such a system at a friend already. 1 Router at the Modem, one router in a different room bridged to the first, and a notebook plugged into the router with a lan cable.

---

### Post by sulu on 2007-02-28
> **chili555 said:**
> When I got a new kernel, it worked. When I switched from Mandrake to Red Hat, it worked. No matter what, it worked. Actually it still works!


Yes I think thats what im looking for :D Mainly concerned about pings and latency and that now though.

---

