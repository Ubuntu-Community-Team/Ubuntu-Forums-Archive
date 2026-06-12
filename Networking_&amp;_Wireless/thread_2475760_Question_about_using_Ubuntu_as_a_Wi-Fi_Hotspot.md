---
title: "Question about using Ubuntu as a Wi-Fi Hotspot"
date: 2022-06-07
forum: Networking &amp; Wireless
---

### Post by chewie316 on 2022-06-07
[COLOR=#1A1A1B][FONT=&amp]I am using a raspberry pi 4 8GB to run Ubuntu Desktop 22.04 LTS I have it running and have also configured a wi-fi hotspot and it is working but I did have some questions.[/FONT][/COLOR]
[LIST]
[*]The DHCP of my router gives out 192.168.x.x addresses to connected devices. I noticed devices connected to my hotspot get 10.42.x.x addresses. Is there an easy way to change this?
[*]I would like to restrict devices connected to this hotspot from my other LAN devices but not sure how to go about this. Not sure if I would do it from my router or in OS.
[/LIST]
[COLOR=#1A1A1B][FONT=&amp]If I missed something and you have questions let me know and thanks for any help or suggestions given.[/FONT][/COLOR]

---

### Post by TheFu on 2022-06-07
> **chewie316 said:**
>  Is there an easy way to change this?
[*]I would like to restrict devices connected to this hotspot from my other LAN devices but not sure how to go about this. Not sure if I would do it from my router or in OS.
[/LIST]
 If I missed something and you have questions let me know and thanks for any help or suggestions given.

a) Please don't screw with fonts or colors in these forums. Use the defaults.
b) "hotspot" doesn't say which software is being used.  There are probably 20 different methods.  I'd be surprised if a different LAN subnet couldn't be set.
c) The way that a router works is by having different subnets on different connections.  So, if you want the hotspot to be a router, then the uplink needs to be a different subnet than the devices that connect into the pi-router.  OTOH, if you want no routing on the Pi, then set it up a network bridge instead.

d) R-pi hardware isn't known for being great at network or disk I/O.  Just because something is possible, that doesn't make it a good idea.  There are cheap network bridge devices which would be better than a r-pi at the task.  Or if you just want a wifi AP (access point), you can get cheaper devices, old routers or an excellent enterprise AP to fill that roll. It all depends on the budget and requirements.  If you want 1 wifi device to get access and care little about throughput/performance, using an old router as an AP with replacement, F/LOSS, firmware is probably the best option.  
If you want better performance, support for wifi-6 connections and less hassle connections, then your main router vendor probably sells an AP that will be integrated into the current router interface.  This should be fine for about 5 devices.
If you want the latest wifi-standards support and to allow 100+ wifi devices to connect, that when spending the $120 for an enterprise AP makes sense.

There are differences in all of this.  r-pi would not even be on my list of things for consideration.  I have 2 PIs, BTW.  They are used for specific purposes where they fit well, but not as network routers or APs or backup servers.  Those just aren't good uses for that hardware for a number of reasons.

---

### Post by chewie316 on 2022-06-07
Thanks for the reply!
a) I didn't mean to screw with the fonts. I did copy and paste my question so maybe that changed it form defaults.
b) Sorry I didn't include that info I created the hotspot using [COLOR=#000000]nm-connection-editor
c) I'm ok with a different subnet I just wanted to change it from 10.42.xxx.xxx to 10.55.xxx.xxx
d) I understand it isn't the best but seems to be working fine so far. I just wanted it to provide an AP that I can use while in my backyard as my current connections don't provide a strong enough signal.  I will look for an old router also but was hoping not to spend much as it won't be used all that often.[/COLOR]

---

### Post by TheFu on 2022-06-07
Around here, a r-pi v4 is $100+. There's a supply shortage.  There are so many better uses for that machine that an AP is about the last on my list.

A 5 yr old Ubiquiti AP for $70 would provide phenomenal coverage for a huge area.  Any M2 or LR model should do it.  You'll probably want a PoE solution so power is provided over the ethernet to the AP ... much easier to run 1 cat5e cable in the attic or under the crawlspace to get the AP where you need it with just 1 tiny hole in a closet or floor in the same room as your normal router - that's if that is even needed.  Most wifi routers wifi connectivity really sucks. Whereas a Ubiquiti AP is purpose built to provide access for lots of clients over huge areas.  I've seen tests where people were able to use wifi music streaming when mowing their field of over an acre in size (good wifi to the far end) with the AP inside their home still. I bet that video is still on YT.

My WAN router doesn't have any on-board wifi capability, BTW. That is by choice.  See, I need the router in a locked closet, but need the wifi in a central ceiling of the house to provide coverage where it is used most.  That AP reaches far outside the house about halfway to the far property line in the back and all the way to the street in the front.  My main router is a purpose designed APU2C4 from PCEngines. To expand it, I use a few dumb switches for different subnets and the wifi is connected to the ISP's router, upstream from my router.  I treat wifi like bare internet. Never trusted.

---

