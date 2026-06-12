---
title: "No wireless since I got nm-applet &quot;working&quot;"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by futz on 2006-09-27
In this post 
[http://ubuntuforums.org/showthread.php?t=265490]("http://ubuntuforums.org/showthread.php?t=265490")
I asked about getting Network Manager Applet working, then posted that I had it fixed. 

Well it's not fixed. It works great for the two wired connections, but I haven't been able to connect to wireless since then. I can't even get it to work the old way anymore.

The wireless connections get listed (after I manually attempt to connect) and even (sometimes) show signal strength, but they won't connect. I watch the lights on the router and there's no sign that anything is coming from the computer. Usually you can see the wireless LED flashing when you try to connect.

Anyone know what config file I have to change this time? It's always one more config file that I had no idea was there.

---

### Post by futz on 2006-09-28
Got it cured! Here's the thread that gave me the fix:
[http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml)

Specifically this section:
> To be completely compatible with NetworkManager, the firmware and driver of your wireless adapter must be able to receive and process the beacons from wireless APs. If you wireless driver does not return a list of APs when you issue the command

  iwlist iface scan

then it is not completely compatible with Network Manager.

I entered that command and got a message saying that my card couldn't scan. "Aha!", I thought to myself. I pulled out the generic RT2500 wireless card I had installed and snagged the D-Link DWL-G520 out of my Fedora box and installed that instead. Booted back up and Network-Manager now works as advertised.

EDIT: Funny thing - tried "iwlist iface scan" with the DWL-G520 and it says "Interface doesn't support scanning", same as the other card. But it works, and that's good enuff for me.

---

