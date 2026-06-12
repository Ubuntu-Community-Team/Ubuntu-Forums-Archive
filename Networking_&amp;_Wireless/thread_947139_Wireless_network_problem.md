---
title: "Wireless network problem"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by andrewchang on 2008-10-14
Well, I recently purchased a Dell Mini 9 and I finally received it today on an Ubuntu OS. However, I don't know why but it doesn't connect with my router (Westell Versalink 327w) when I try to wireless connect to it. I tried turning off the WEP and turning it back on, making it shared and open, making 64 bit and 128 bit, changing the router from sending mixed, b, g but it doesn't work. However, I tried to connect to another person in my neighborhood's router who's network is unsecured and it works just fine. Then I thought maybe it was just my router. Then I tried it with another person who has the exact router as me and it doesn't work on their's as well. Can anyone help me here? Stealing internet is a pain in the **** + illegal... :(

---

### Post by hyper_ch on 2008-10-14
(1) disable any security on your router
(2) try to connect then with your wireless

if that works then

(1) activate security again
(2) try to connect again with your wireless

does this work?

---

### Post by andrewchang on 2008-10-14
> **hyper_ch said:**
> (1) disable any security on your router
(2) try to connect then with your wireless

if that works then

(1) activate security again
(2) try to connect again with your wireless

does this work?

Yeah, I already tried that. I turned off the WEP and turned it on. I tried it on a few people who has the same router (Westell Versalink 327w) and everytime it failed. :confused:

---

### Post by hyper_ch on 2008-10-14
can you connect when WEP is turned off?

P.S.: WEP does not provide any security and can be hacked in a matter of minutes.

---

### Post by andrewchang on 2008-10-14
> **hyper_ch said:**
> can you connect when WEP is turned off?

P.S.: WEP does not provide any security and can be hacked in a matter of minutes.

Yeah I tried to connect with WEP off. I know WEP can be hacked in a matter of minutes but I don't think that many people in my neighborhood knows how to do it :). I'm pretty sure it's the settings on the router because I tried the dell mini on the exact same router that belonged to my neighbors (it's funny how verizon has a complete monopoly on DSL here) and not even just one neighbor, I tried it on four neighbors and it didn't work. However, I tried it on my school network, my neighbor who has a linksys router, and my other neighbor who has a generic one and it worked fine.

---

### Post by hyper_ch on 2008-10-15
run
```

iwconfig

```

---

