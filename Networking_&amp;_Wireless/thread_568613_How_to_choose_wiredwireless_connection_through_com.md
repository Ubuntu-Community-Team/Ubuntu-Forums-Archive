---
title: "How to choose wired/wireless connection through commands"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by jasonchewy on 2007-10-06
First, the reason why I'm using linux commands to do networking stuff, is because for wireless at my campus, one ssid has multiple AP's with different MAC's, and only through commands can I connect to a specific AP.

Now back to the main question.

so I'm on my linux laptop trying to see what's wrong with a router, so naturally I plug the test router into my wired jack.  So I go enable my wired network in the "Network" settings in ubuntu.  It connects and all according to the network monitor applet, but the problem now is, 192.168.0.1 has two destination, one to my wireless connection, and one to my wired one.
I physically turned off the wireless on my laptop, then the wired one kinda picked up, so I can go to the wired router's page, but then I wanna switch back...and wireless was a bit messed up and won't let me connect...even though iwconfig shows it's all connected and the network monitor applet shows it's connected....
am I missing a command somewhere?
How do I tell linux to take one of my device to be the main "source"?

Thanks all!

---

### Post by SpiritIsReality on 2007-10-06
howdy
the WifiDocs are pretty good for this stuff
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
try under the heading "using the command line" here
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
sorry I don't know how to "target" a spot on a page yet, but it's about the 4th heading.
buds

---

