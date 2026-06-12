---
title: "Wireless Compaq R3000 ndiswrapper Breezy Badger"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by notanxious on 2008-03-28
Greetings,

I admit that I am very new to linux and have come for answers concerning the ndiswrapper in conjunction with windows drivers to utilze broadcom card.

Pretty sure I goofed this one up. I installed ndiswrapper, says driver is working, no hardware present (atleast no indication or address). There's nothing in the /lib/src directory either. Not sure since I don't have much linux experience, but I assume there should be something in there... 

Please help... 

Thanks in advance:confused:

---

### Post by dstew on 2008-03-28
Post the output of```
lspci
```and```
ndiswrapper -l
```and```
iwconfig
```

---

### Post by articpenguin on 2008-03-29
why are you on breezy? that hasnt been supported for 12 months.

---

### Post by notanxious on 2008-03-29
Thanks in advance guys/gals, 

So i've upgraded to 7.1 since my original post. 

ls pci - BCM4306 

So, I assume that I need to go grab a driver... I will try this now and post the results... Any hints would be appreciated!!!!

Thanks again in advance

---

