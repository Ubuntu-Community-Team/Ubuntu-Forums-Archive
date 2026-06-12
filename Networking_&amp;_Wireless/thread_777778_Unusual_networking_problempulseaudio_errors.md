---
title: "Unusual networking problem/pulseaudio errors"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by jeluranni on 2008-05-01
I've been using Hardy for a few months with few problems. The past couple of weeks I have experienced networking problems that I felt were due to my broadband provider. However, I now know that is not the case. Hardy is connected to my wireless router through ethernet. When I log into my desktop on Hardy, the computer starts sending data at 180 kbps. After a few minutes, none of my computers are able to access the internet. If I log out of my desktop everything goes back to normal. This mysterious sending of data does not happen if I log into other accounts on Hardy. I have stopped all system services that are unneeded and unchecked everything set to auto start on login. The problem still persists. The only way I can get it to stop is by unplugging the wireless router or stopping networking on Hardy. If I unplug the wireless router, Hardy stops sending data. However, it starts sending again as soon as the router is plugged in. If I stop networking, Hardy stops sending data. If I restart networking, Hardy does not start sending data again until the computer is rebooted. I've run software to check for root kits and not found any concerns. Nothing unusual shows up in the logs until networking is stopped. Then I start getting pulseaudio errors about not being able to send to memblockq.

Anyone have any ideas about what is causing this?

I have solved this problem. After much searching I discovered a blog describing the same problem I was experiencing. The problem was Pulseaudio. Thankfully, it is easily fixed. I opened Pulseaudio Preferences (System,Preferences). Click on the multicast/RTP and uncheck Enable Multicast/RTP sender. That immediately solved my networking problem. I have no idea what Multicast/RTP sender is or why it was checked by default. 

If you are experiencing slow network connections/networking issues check to see if the this option is checked in Pulseaudio Preferences.

---

### Post by JRAlkire on 2008-10-12
Thank you! I had the same problem. I use the multicast thing to share my audio over the network, but I had already set it up in the system-wide pulse.conf (don't remember where that is located off the top of my head), so it was sending the audio data multiple times over the network, flooding my router with traffic. Ping on the default gateway changed from ~1 to ~1500 and sometimes even ~4400. This simple fix made all that go away, and my sound still works over the network just fine (perhaps even better).
Thanks!

---

