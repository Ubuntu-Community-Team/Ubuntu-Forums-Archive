---
title: "wireless not in nm-applet"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by Remasis on 2006-09-23
Thanks in advance for any advice. Here is the issue:

I have had wireless working fine with WEP on my system before using the nm-applet. I have ndiswrapper working and the device shows up in ifconfig and iwconfig fine along with the properly loaded modules. This happened once before for a few reboots but then it worked fine and now it's happening again but it's more persistant than the first time.

I don't have any wireless options in the nm-applet. It's not a problem with the applet itself as I have also used wifi-radar to attempt to connect to networks. I can iwlist and scan available networks and they show up perfectly. The problem comes with attempting to actually connect with the networks. wifi-radar hangs on the "acquiring IP address" box and returns with a message "could not get IP address." Then wifi-radar shows "Connected to <my essid> ip(None)"

I've connected on my home network before as well as other ones. There are also a lot of other AP's in my area. I just can't figure out why it's having trouble with nm-applet and wifi-radar. Any help is GREATLY appreciated.

Update:
I seem to be able to get it to work if I run "invoke-rc.d networking restart" it manages to get an IP from my router then. If I attempt to connect via wifi-radar after this however, I still cannot get an IP. Any ideas??

---

