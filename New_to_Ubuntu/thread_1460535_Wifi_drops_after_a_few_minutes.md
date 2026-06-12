---
title: "Wifi drops after a few minutes"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by cloyd on 2010-04-22
I've posted on this in another thread. I've never received a workable answer. Perhaps I haven't given enough information.  I' using a Gateway LT3103u "netbook" with 2 gig ram, and an                             Atheros AR5B95 Wireless Network Adapter. I'm running UNR 9.10, but have disabled to "Fisher Price" interface to look more like regular Ubuntu. My problem is this: If I am at the far end of the house, I may have a 30% or better connection at first, but it quickly drop to 20.  I can use the internet for a few minutes, but it soon drops to 10% or less. After it drops, it may come back a little as far as signal strength, but sometimes I cannot connect with Mozillia . . . times out trying to connect to a page. Maybe I have a signal, but my Conky says "download speed 0.0 Kb/sec"   Reboot, and it goes back up for a few minutes. Clicking on network manager, disconnecting and reconnecting does nothing.  I've tried to get a repeater, but have had no luck setting it up. I really believe I just wasn't savy enough. My wife doen't have this problem in windows. (I hate to admit this) .  I've looked at the router, and the channel is set on "auto". 

Any suggestions?
Thanks s

---

### Post by cloyd on 2010-04-24
The problem appears to be solved. I thought I'd tried everything. I bought repeaters, and couldn't get them to work. I messed with the channels, and that didn't help. Then, yesterday, I looked deeper in some of the things already posted in the forums, and suddenly I found this suggested in a post. 
Go to synaptic and install the following packages:
                                 

linux-backports-modules-karmic-generic.
linux-backports-modules-wireless-karmic-generic.
 
It installed one more package . . . said it was a dependency. I wish I had written it down.  However, wifi is working in the far end of the house as well as it works right next to the router.  This morning, I downloaded a couple albums from emusic out here at the far end of the house.  I don't understand exactly what these packages did, but they worked.

I don't always get the help I want exactly when I want it, but the answers come. The forums are great. Getting closer to the day when the Windows partition disappears. I haven't used it in over a month.

---

### Post by P4man on 2010-04-24
You cam read what backports are here:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Essentially, it looks like you got updates that where made for Lucid, but ported back to your kernel for ubuntu 9.10. So you get newer drivers for your wifi, fixing whatever problem they clearly had.

---

