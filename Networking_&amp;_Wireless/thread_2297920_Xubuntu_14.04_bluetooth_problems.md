---
title: "Xubuntu 14.04 bluetooth problems"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by GammaPoint on 2015-10-07
I've been having problems with my bluetooth on Xubuntu 14.04 (as managed by blueman). At first I could detect my device but would get the error "device added succesfully but failed to connect". After some google searches I saw that some people were able to fix this issue by first issuing the following from the command line

```
pactl load-module module-bluetooth-discover
```

The first time I did this I was able to actually connect to my device, although I was unable to get the sound to actually come out of the bluetooth speakers (it continued to come out of my laptop speakers).
 
So I figured I was close, and thought I'd start over from square one, do things similarly, and see if anything changed. So I removed my discovered device from Blueman. Unfortunately, now that I've done that I can't rediscover the device at all anymore (which was not a problem I was ever having before)! Did I somehow blacklist this device and I need to clear it out before it's discoverable again? And assuming I can discover it again, any pointers to the best way to resolve the bluetooth problem?

---

### Post by GammaPoint on 2015-10-07
Well, after a series of restarts and some magical incantations, I was able to see my Bluetooth device again. I was then able to run the pactl command above and pair the device. Then I was able to select Bluetooth as the output device by messing with Sound Settings (the speaker at the top right).

---

