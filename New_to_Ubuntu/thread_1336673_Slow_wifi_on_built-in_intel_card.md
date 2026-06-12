---
title: "Slow wifi on built-in intel card"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-11-24
Hi All,

I am having an issue with slow internet response on a Sony Vaio.  Per lspci, it seems this is my wireless controller (its all built in) 
```
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

My connection is a DSL that I have personally seen hit 1.5 mb/s on torrents.

Any suggestions on how to speed this puppy up?  It used to be pretty fast on windows, at least 500 kb/s, but now I never see over 160 kb/s in the browser (downloading images, etc) torrents, or from the repos on apt-get upgrades.

**EDIT**  

I just flipped back to windows to do a few different speed tests, and I am getting the same results there.  I tested DLing an image, and also speedtest.net, and the results were IDENTICAL for both os's.  I guess I am going to have to call AT&T.  I know it used to be a lot faster.

By the Way, going back over to windows reminded me why I switched in the first place.  Thank God for Linux!

---

### Post by Paqman on 2009-11-25
If you've got an ethernet cable try plugging in and re-running the speed tests. That'll tell you if it's your ADSl or the wifi. If it's the former, gripe at your ISP, if it's the latter try repositioning your router or switching to a different channel.

---

