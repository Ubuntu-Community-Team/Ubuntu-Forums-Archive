---
title: "Wireless network solution"
date: 2021-05-05
forum: Networking &amp; Wireless
---

### Post by jerrywo on 2021-05-05
I feel like Rip Van Winkle.  Our 7-year old Linksys WRT54GL conked out during a thunderstorm.  Looking for a replacement, or better
yet a simple wireless solution.  Previously I had my Linux machine hooked to the router via a CAT5 cable and my wife connected to
the WIFI signal.  That's the sum total of our internet needs.

Now I see there are USB WIFI adapters.  I assume this is a viable alternative to a router?  Or do I get another router?

Looking at the Panda Wireless PAU09 N600 or equivalent.

Thanks in advance
Jerry W
Warrenton, VA

---

### Post by TheFu on 2021-05-05
No.  USB Wifi adapters are NOT routers. They are for laptops that have a broken wifi adapter or for a desktop computer that doesn't have wifi, but you wish to add it.

You need a new router, if you want a router, firewall and easily setup solution.

There are lots of trade-offs when picking a router. Most cheap routers have short support periods, perhaps 1 yr.  If you want longer support, then usually paying more is needed.  Or you can look up aftermarket firmware for specific cheap router hardware that is still supported and use one of those.  I've been burned a few times over the decades.  An unpatched router is a security risk - basically, it makes the firewall useless.

Router brands known to provide longer support are:
[LIST]
[*]AsusThey provide patches for known issues quickly and have 1-click patching.
[*]Mikrotik
[*]Ubiquiti
[/LIST]

Asus is the most expensive on the cheap side, but not usually as capable as mikrotik or Ubiquiti small-business routers. Asus was legally forced into a false claim settlement by the US FTC over security failures. Part of the settlement has forced them to basically follow best practices for maintaining the firmware for routers. There is a price for that effort. I think they have a checkbox to automatically patch as needed. 

Ubiquiti tends to have separate routers and wifi-APs. They make good versions of both. Often, people like to upgrade the wifi standard AP much faster than they want to upgrade their router.  Ubiquiti became famous for the excellent wifi-APs. I've deployed them when other wifi routers were having wifi issues at clients (cough netgear).  We tried to get a netgear wifi router working with about 20 clients and it seemed to connect, but got confused.  Disabled the wifi on that router and used it purely as a wired router and connected a ubiquiti AP - 50 clients were fine after that change.  Ubiquiti is used by many hotels as well.  If you'd like to use the wifi from the far end of your back yard, Ubiquiti makes an AP that does that and it isn't very expensive. They provide patches for known issues quickly and have 1-click patching.

Mikrotik has a normal web-gui like you are used to, but with more capabilties like an enterprise router would have, just with an approachable GUI. They provide patches for known issues quickly and have 1-click patching.

A few weeks ago, a friend was showing his linksys router.  There were 3 versions of this AC router. 2 of the 3 had recent patches, but the highest version of that model hadn't gotten new firmware since 2018.  It was a complete failure.  Beware, if you get linksys. Check when the last firmware was released and if it was over 2-3 months ago, then avoid that model.  There are always, always, patches for all routers every month or so.

You might wonder what I use?  I'm sorta "in the business", so I use an APU2 hardware running OpnSense as the routing software. No internal wifi.  I don't trust wifi after designing and deploying wifi for 1200+ locations in a corporate setup. All the current wifi standards, including wifi-6, have known security issues.  The wifi in the house is outside our internal network, basically on the internet. All wifi devices that want to connect to internal systems must use a VPN that I host.  Never trust wifi without a VPN.  The IoT devices we have (roku, chromecast, Android phones/tablets, etc) are all on the external, untrusted, wifi network.  Guests get put onto a different LAN from our devices and only have internet access.  I would get an APU4 today, if I were in the market for a new router. An APU4 is an AMD-64, low point single-board-computer with 3 or 4 NICs. I think my APU2 will last another 5 yrs, perhaps 15 yrs. I'm extremely happy with OpnSense, but it isn't for everyone and I wouldn't recommend it to most people. It is for network nerds or people who are tired of having perfectly working hardware become obsolete because a vendor got bored and wanted money.  APU2/APU3/APU4 hardware can run almost any x86 router software.  I know ddwrt, openwrt, and a number of linux-based x86 router software works well on it.  pfSense and OPNSense work well too, though the NIC drivers are single threaded under BSD, so 650Mbps is about all the throughput possible to the WAN under BSD.  Linux drivers are MT and easily use the full 1 Gbps on all the ports.

You know how some routers need to be rebooted monthly or they get slow or crash?  I patch the OPNSense software weekly and it reboots as needed after patching.  
# uptime
 2:51PM  up 13 days, 21:04, 10 users, load averages: 0.73, 0.62, 0.62

The media players we really use (raspberry pi w/ OSMC) are wired ethernet and on our media-only subnet.

---

### Post by jerrywo on 2021-05-05
Thanks "Fu"
It was shortly after I hit the "send" button on my query when I realized my error (blush).  Oh well.
I see our aging WRTGL router is still available for $40 - it had the advantage of me being able to
talk to it via my Linux box.

But Lemme look at the routers you suggest.  I may have further questions!

Thanks

Jerry

---

### Post by chili555 on 2021-05-05
> I see our aging WRTGL router is still available for $40 - it had the advantage of me being able to
talk to it via my Linux box.The WRT54GL is about ten generations behind. There have been many improvements in speed, security, etc. since this dinosaur was released in 2005. I say this as an owner of a WRT54 in my junk pile/museum.

Most obvious is that the WRT54GL is limited to 802.11G speeds, that is, 54 Mbps and the somewhat congested 2.4 gHz band. 

Almost every router can talk to our Linux and Mac machines through the browser interface.

---

### Post by morrownr on 2021-05-05
Build your own. Give a look at this little repo of mine:

[https://github.com/morrownr/7612u](https://github.com/morrownr/7612u)

Take a look at the two files...

Bridged_Wireless_Access_Point-1.md
Bridged_Wireless_Access_Point-2.md

These two files give an example of settings up a "dumb ap" with either single band 5g or dual band. You can even turn it into a wifi router with some software additions. You have the ability to change out parts and this is powerful enough to use it for some other things in addition to being an access point/router.

Be glad to offer advice if you go this way.

Nick

---

### Post by morrownr on 2021-05-05
> **jerrywo said:**
> I feel like Rip Van Winkle. 

Now I see there are USB WIFI adapters.  I assume this is a viable alternative to a router?  Or do I get another router?

Looking at the Panda Wireless PAU09 N600 or equivalent.



Hey Rip,

That Panda PAU09 N 600 is not a bad adapter but for less money, you can get a far more capable adapter. I've been tracking adapters with in-kernel support here...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

I've lost count of the number of links to adapters that have in-kernel support that I have posted on that site but it was around 60 when I counted last. Using a good AC1200/AC1300 adapter to build a wifi router/access point is a lot of fun.

Regards,

Nick

---

### Post by jerrywo on 2021-05-07
Well this was easy.  I was fretting about setting up a new router and made note of all the settings on my ancient WRT54GL.
Bought a Linksys AC1750.  Accessed it via the browser (192.168.1.1) and up popped a nice little GUI that walked me 
through the set up.  Rather a pleasant surprise.  My wife is a happy camper again.  Wife happy = happy husband.

Thanks to all

---

### Post by TheFu on 2021-05-07
> **jerrywo said:**
> Well this was easy.  I was fretting about setting up a new router and made note of all the settings on my ancient WRT54GL.
Bought a Linksys AC1750.  Accessed it via the browser (192.168.1.1) and up popped a nice little GUI that walked me 
through the set up.  Rather a pleasant surprise.  My wife is a happy camper again.  Wife happy = happy husband.

Thanks to all


Not to scare you, but ... you should be scared. [https://www.linksys.com/us/support-article?articleNum=148365](https://www.linksys.com/us/support-article?articleNum=148365)
V2 of that device last firmware update was:
```
Version:  1.1.42 (build 203057)
Latest Date:  **[COLOR="#FF0000"]11/10/2020[/COLOR]**
Download 17.2 MB
```

V1 of that device **has not** been updated since [COLOR="#FF0000"]_**2014**_[/COLOR]!!!!

Both of those are much too long to be secure.  TAKE IT BACK ASAP, is my advice. Any date longer than about 3 months means the device isn't supported and shouldn't be put onto any network, unless your goal is to test being cracked.  It is certainly at the outer edge for how long most home routers get updated.

Web search: "linksys EA6500 hacked" to see er ... 5+ pages of examples.  Google says 30,000+ results.  The EA6500 is the SKU used by Linksys for your model.

If the device can run an after market firmware like openwrt or dd-wrt, then if you want to keep it, please, please, install one of those and patch it every few weeks.

Every week, I see lists of hacks against routers.  All of them, even my fantastic router, show up in the list from time to time.  The only protection we have is having current, patched, firmware for our routers and installing it quickly - within a week or so - of the announced crack.  The more features enabled in the router software, the more likely any bug/crack will impact your security.

---

### Post by jerrywo on 2021-05-07
Goodness - what a world we live in!

So, one of the very first steps the GUI asked was "getting update info" and I said yes,
and yes to automated updates as well.

That count for anything?

Jerry

---

