---
title: "wireless adapter - Edgy vs Gutsy"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by crzdude on 2008-02-16
Hey there,

I have experienced a curious issue with my tew424ub wireless adapter. It works flawlessly on Edgy (ndiswrapper 1.23) but it is very flaky on Gutsy (ndiswrapper 1.9). After installing Gutsy, nm-applet was showing my home network with a signal level below 50% (in contrast to 100% on Edgy) and my wireless adapter was having a hard time connecting and/or maintaining a connection to it. Unfortunately, I could not test ndiswrapper 1.23 on Gutsy because I wasn't able to build it (I reckon due to changes on some of the kernel header files). 

Does anyone know what can be the cause of this problem? Could it be the case that I have to set the "power level" of my adapter to a higher value on Gutsy or something like that (I'm not sure if such a setting exists)? I had to downgrade back to Edgy due to this problem but I would like to fix it and move to Gutsy.

Thanks in advance

---

