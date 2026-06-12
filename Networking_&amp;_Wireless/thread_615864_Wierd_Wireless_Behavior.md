---
title: "Wierd Wireless Behavior"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Zipster90 on 2007-11-17
I was at my local coffee shop this morning when my wireless wigged out on me. I booted up my laptop and was going to connect to the shop's wireless network with wicd as I usually do, but no wireless networks were detected, when it usually finds four. I rebooted multiple times, and fiddled with a few settings to no avail. I ran iwlist scanning to see if it could find the hotspots that way, and this is the output:

[HTML]zach@zach-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable[/HTML]

I had never seen that error message before on wlan0, so I decided to work on it when I got home.

I got home, expecting to have to plug in my ethernet, but as soon as I booted up it connected to my home wireless network and all was well. I did iwlist again and the error message was gone, however wlan0 reported that there were no scan results, even though I was connected to a wireless network. Very odd. Anyone have any idea as to what happened to me this morning? Thanks.

---

### Post by Zipster90 on 2007-11-17
bump

---

