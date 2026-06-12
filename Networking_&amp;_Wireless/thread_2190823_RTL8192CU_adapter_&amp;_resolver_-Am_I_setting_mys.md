---
title: "RTL8192CU adapter &amp; resolver -Am I setting myself up for a problem?"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-11-29
First, a little background.  As I've posted elsewhere, I'm a sucker for cheap (<$10)USB wifi adapters.  I have two of these generic RTL8192CU adapters:
> 
ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter

I bought them from an Ebay vendor - Sunbelt power tools - that sells power tools .................. and these WiFi adapters :D

These work perfectly using the patched driver found here:  [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes).  I wanted to see if I could get them to work reasonably using the 'baked-in' driver in 13.10.  They worked pretty well, recognized when plugged in and connected okay but speed was less 72.2 Mb./sec using the included driver vs. 300 Mb./sec. using the patched Realtek driver.  The most noticeable problem was that when switching from web site to another,  it would either do so slowly or not at all.  Ping would either show nothing or 'host not found'.  I'd not seen a problem for instance reading posts here, going back to the index page, clicking on another topic, no problem.  Trying to switch from Ubuntuforums.org to weatherunderground.com for example was a problem, it'd just stall.  Disabling WiFi, waiting a second then re-enabling WiFi would fix the problem.  I was using Chromium for one site and this problem showed up.  There was a message in the lower left corner about resolving a page but nothing happened.  Hmmm, I looked at resolv.conf but that file said to not edit anything manually, any changes would be overwritten.  

Okay, what overwrites them? I did some searching and found that Network-Manager may have something to do with it.  I found this file in my /etc/Network-manager folder:

> 
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


I recalled a post where Praseodym talked about namerservers.  Hmmm, I wonder if that's where the resolving problem was coming from?  I renamed the original NetworkManager.conf file then changed it to this:

> [main]
plugins=ifupdown,keyfile,ofono
dns=nameserver 208.67.222.222\nameserver 208.67.220.220

[ifupdown]
managed=false

I rebooted and the problem switching between web sites seem to have disappeared, or at least greatly lessened.  Absent openDNS.org being unavailable, have I set myself up for a problem at some future date?  This is a simple home network using two routers, one in extender mode.  I'm connecting to the router in extender mode.

---

### Post by mikewhatever on 2013-11-30
Not sure what you are asking..., the RTL8192cu chipset has been crappy on linux for years, which unlikely to change, ... but you seem to be doing alright, are you not?

---

### Post by kurt18947 on 2013-11-30
> **mikewhatever said:**
> Not sure what you are asking..., the RTL8192cu chipset has been crappy on linux for years, which unlikely to change, ... but you seem to be doing alright, are you not?

Yes, the performance on 13.10 using the included driver is pretty decent with the 8192CU based adapter.  8192CUs adapter (Edimax EW7811Un) using the open drivers sucks.  I was mostly asking if I was setting myself up for hard-to-diagnose problems down the road.  My understanding of the nuts & bolts of linux+networking is weak but I'm having a good time hackin' away :cool:.

---

### Post by praseodym on 2013-12-01
[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

Do you know these?

---

### Post by kurt18947 on 2013-12-04
> **praseodym said:**
> [http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

Do you know these?

Yes I do, thanks.  I'm using 13.10 and the  I'm just experimenting with the 'baked-in' driver to see if I can find any tricks to improve its function.  I didn't want to unwittingly compromise security.  The git fix works perfectly - except if I remove the adapter while it's active.  Removal will cause a kernel panic.  I find the 'baked-in' driver works quite well on a Gigabyte Motherboard home built desktop.  I need to disable/enable wifi perhaps once an hour, it takes a few seconds.  A Thinkpad T61 running 13.10 Ubuntu-Gnome is not quite as reliable, I need to stop/start wifi perhaps 3 times/hour. 

I am thinking of those who only have a wifi connection, no ethernet cable.  If nothing else, this adapter will function long enough to install one of the replacement drivers you linked.  The other case for using the 'baked-in' driver is during a distro's development period.  Tweaked Realtek drivers may not be available until the distro is stable.

---

