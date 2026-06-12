---
title: "STA/B43 network manager internet stalling constantly"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by venom104 on 2010-10-23
My internet seems to be acting up. First when I tried using the restricted STA driver for my firmware (BCM4312) my internet would randomly stall about once every 10 minutes; when it would stall downloads would stay stuck and pages wouldn't load. This ended after about 30 seconds. I recently uninstalled the STA driver and installed the b43 kernel module (from the package b43-fwcutter) and am having a similar problem. Sometimes (and I stress somtimes { about once very 20-30 minutes} my internet stalls out...downloads stay stuck and webpages take forever to load. This happens for about 30 seconds.

I have a windows install on this same machine and it works fine (so I believe this eliminates a hardware issue). I should also note that I've had various distros of linux installed on this machine which ALL used the fwcutter package (arch,ubuntu earlier versions, linux mint, and debian) and they all worked FINE. Please assist me.

---

### Post by venom104 on 2010-10-23
> **venom104 said:**
> My internet seems to be acting up. First when I tried using the restricted STA driver for my firmware (BCM4312) my internet would randomly stall about once every 10 minutes; when it would stall downloads would stay stuck and pages wouldn't load. This ended after about 30 seconds. I recently uninstalled the STA driver and installed the b43 kernel module (from the package b43-fwcutter) and am having a similar problem. Sometimes (and I stress somtimes { about once very 20-30 minutes} my internet stalls out...downloads stay stuck and webpages take forever to load. This happens for about 30 seconds.

I have a windows install on this same machine and it works fine (so I believe this eliminates a hardware issue). I should also note that I've had various distros of linux installed on this machine which ALL used the fwcutter package (arch,ubuntu earlier versions, linux mint, and debian) and they all worked FINE. Please assist me.

I forgot to add when this happens ping (pinging to [www.google.com](www.google.com)) stalls as well.

---

### Post by venom104 on 2010-10-24
After reading some similar posts about similar issues I disabled the ipv6 module; it didn't help at all. I'm currently unable to find any other possible solution to this problem.

---

### Post by venom104 on 2010-10-30
I ended up wiping my partition and installing ubuntu 10.10 (I had ubuntu 10.4 installed) and have not seen this problem sense. Sense this is the first link that comes up in google when using the query "internet stalling ubuntu", I would encourage anyone that is having the same problem to post on this topic (according to the forum rules, of course) sense this problems seems to be local to ubuntu 10.4.

---

### Post by venom104 on 2010-10-30
> **venom104 said:**
> I ended up wiping my partition and installing ubuntu 10.10 (I had ubuntu 10.4 installed) and have not seen this problem sense. Sense this is the first link that comes up in google when using the query "internet stalling ubuntu", I would encourage anyone that is having the same problem to post on this topic (according to the forum rules, of course) sense this problems seems to be local to ubuntu 10.4.

I forgot to add I am using the same computer, same hardware, and the same wireless driver (the STA driver listed in restricted drivers for BCM4312 cards)

---

