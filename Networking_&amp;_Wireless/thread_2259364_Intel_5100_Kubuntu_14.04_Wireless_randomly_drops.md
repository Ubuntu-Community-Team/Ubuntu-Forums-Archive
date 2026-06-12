---
title: "Intel 5100 Kubuntu 14.04 Wireless randomly drops"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by gideond2 on 2015-01-03
I'm running an HP Pavillion DV4 with Kubuntu 14.04. It's been on there ever since June with no issues. After a few updates earlier this week I'm having wireless issues. Wireless does work and speeds are great. However, I randomly get a prompt to enter the wireless key several times per session. I can cancel the prompt, which deactivates the connection, but then I can open the network widget and click connect and it connects fine again with no need to enter the wireless key. So it isn't like it's really forgetting the key. Any idea what this is and how to fix it? I've already tried deleting the connection details and creating it again with the option to allow all users to use the connection. That seemed to work for a day, but now it's right back to the same issue again. Script output is attached.

Thanks,

---

### Post by praseodym on 2015-01-04
Deactivate the N-mode and queue of the driver:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot.

---

### Post by gideond2 on 2015-01-04
Thanks, I'll give it a try this evening. Any particular reason N-mode should suddenly be an issue after working for the past 5 years with Kubuntu on this machine? Or has N-mode not been used for all that time?

---

### Post by gideond2 on 2015-01-11
Well I tried the fix last weekend and I've been running it off an on this week with no apparanet problems. I figured maybe since this card is listed as Draft-N that N functions just don't work well. However, I've had the problem recur twice this evening. Here is the new wireless script output.

---

### Post by praseodym on 2015-01-12
There is a lot of traffic on channel 6, try 13. Additionally, there is a network with the same ESSID "TheWorld" in the 5 GHz-band. Try a fixed channel in either band.

---

### Post by gideond2 on 2015-01-12
I have a dual band router, Asus RT-N66U flashed with the latest Merlin firmware. Both SSIDs are mine. One in each band. Hidden-Realm is also my guest network but my personal devices do not have login credentials stored for these. Maybe having both bands named the same is not a good idea, but it hasn't been an issue for the past few years. I've changed the channels on both bands to channel 1 and 44 respectively. Using WiFi Analyzer on my phone shows that I am the sole AP in the 5 GHz band and I am now alone in the lower end of the spectrum on the 2.4 GHz band. Other APs are shown in the mid to upper channels.  I'll give it some more time and see what happens.

---

### Post by gideond2 on 2015-01-22
Problems persisted with no changes. Finally I noticed that I didn't seem to be getting any updates either, but I could install packaged from synaptic or terminal with no issues. I logged into the XFCE desktop I also have on this machine and immediately got update notifications. After running a series of updates I logged back into KDE. Now I am getting update notices like normal and I've only seen the wireless drop a single time in the past week, which could be a fluke. Looks like I got a bad update causing issues. I'm hoping it's completely resolved no.

---

