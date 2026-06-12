---
title: "Is there an *easy* way to use my computer as a wireless router?"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2008-05-25
I have an old laptop with an ethernet card and a wireless device.  I'd like to use it as a wireless router for a few days, because I'm in the middle of moving and won't have my real router for that time.  Ideally, I would like to be able to just have the laptop broadcast an essid that other machines (including Windows ones) can connect to as if it were any other normal router.

I've tried to follow a couple how-to's on the forums but have not had much luck.  What I'd really like is to find some kind of live CD distribution that I could pop into my laptop to get it working as a router without much effort.  Does anything like this exist?  I looked at freesco, which looks nice, but it's not clear how well it supports wireless devices; it seems designed more to serve as a wired router.

The next best thing would be a GUI where I could point and click and have a wireless router set up.  Are there any utilities like this?

Otherwise, if anyone has links to any simple tutorials for setting up an Ubuntu/Linux box as a router, I'd appreciate it.  I've tried [http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283) and [http://ubuntuforums.org/showthread.php?t=73406](http://ubuntuforums.org/showthread.php?t=73406) but haven't gotten it to work; I'm not sure why.

I don't care about doing anything fancy like monitoring the traffic, and I don't care how secure the laptop is.  I don't even care whether I can encrypt the wireless or not.  I just want to create a wireless network in my house for a few days with minimal effort; otherwise it's not worth the time, since it's only for a few days.

Any suggestions of where I could find an easy live CD to use, a nice GUI utility or a good tutorial would be very appreciated.

---

### Post by superprash2003 on 2008-05-25
with a wireless LAN card you could connect wirelessly to only one pc.. not multiple windows pcs

---

### Post by pytheas22 on 2008-05-25
> with a wireless LAN card you could connect wirelessly to only one pc.. not multiple windows pcs

Are you sure?  I was pretty positive that it was entirely possible to connect  to multiple machines using just one network interface, forwarding packets to different clients as appropriate.  After all, aren't wireless routers just stripped-down computers with one wireless interface that connects to multiple machines?

---

### Post by pytheas22 on 2008-05-26
Update: I realized that the source of my trouble was that my laptop's wireless card, which uses the bcm43xx driver (as my laptop is still on Gutsy), doesn't seem to really support master or ad-hoc modes.  It will go into them without a problem and iwconfig says that it's in whichever mode I assign, but apparently it doesn't really work.  Other people report similar problems, so I'm guessing it's the driver.  This is why the tutorials that I was trying to follow weren't working.

I plugged in a Ralink card (rt73) and things appear to be going better.  I haven't gotten all the way there yet but I've at least made an ad-hoc network.  I think that if I spend a little more time, I can get what I need.  I'll post if I end up succeeding.

---

