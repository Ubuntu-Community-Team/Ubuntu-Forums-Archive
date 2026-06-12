---
title: "[SOLVED] Can't access WEP networks"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by FiReSTaRT on 2008-09-04
Yep, another thread on this topic. I'm running 8.04, the network is using a 128bit passphrase. The adapter detects the network (and a few others in the area), with solid signal strength. 
When I try to connect, it fails and displays the key as 128/40 bit hex for some reason. I've never had such problems with the same machine running Vista or 3 other machines running XP. I even tried upgrading the Network Manager to 0.7 to no avail.
Any other tips on an easy, idiot-proof way to handle this? I travel around a lot with my laptop and I'd prefer to be able to connect to secure networks while running Ubuntu.

---

### Post by scrooge_74 on 2008-09-04
Check here first

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by FiReSTaRT on 2008-09-05
Finally managed to install WiFi Radar.. That did the trick after none of the others did. It took me most of the day to get the right driver and get WEP configured. The rest of the hardware config shouldn't be too too bad and I can get into customizing my baby. Thanks for making me take another look at this, as WiFi Radar was one of 2-3 GUI apps on that list that I haven't tried.

---

### Post by FiReSTaRT on 2008-09-05
I spoke too soon.. Obviously my brain went to crap.. The cable was plugged in.. As soon as I unplugged it, WiFi Radar saw the network but I'm having trouble connecting with it as well.. I'll try playing with it some more tomorrow.

---

### Post by Crafty Kisses on 2008-09-05
> **FiReSTaRT said:**
> I spoke too soon.. Obviously my brain went to crap.. The cable was plugged in.. As soon as I unplugged it, WiFi Radar saw the network but I'm having trouble connecting with it as well.. I'll try playing with it some more tomorrow.

Post the results of this command: ```
lshw -C network
```

---

### Post by FiReSTaRT on 2008-09-05
I finally got it up and running.. For some reason the Network Manager is having issues with 128bit ascii passphrases. This is what I did to get it up and running:
1: I used an online ascii to hex converter
2: I entered the hex version off the password
Now I have full wireless connectivity under Linux. 
The Network manager has absolutely 0 issues with entering 40/64bit ascii passphrases. When I tested it with a 5 character ascii password, it worked like a charm. Only 128-bit was buggin' on me, but obviously, just converting it to hex worked like a charm. 
Now it's time to reconfigure the network settings in Vista and on the other laptop to account for the new password.

---

