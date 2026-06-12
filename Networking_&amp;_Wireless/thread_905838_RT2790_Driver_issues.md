---
title: "RT2790 Driver issues"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by FallopianJones on 2008-08-30
I recently purchased a laptop with a Ralink RT2790 Internal Wireless card and have been unable to get the drivers to work under Kubuntu 8.04. They seem to compile without issue but when I try to load the module with modprobe it says that it cannot be found. I put the module in /lib/modules. Any help with this problem would be much appreciated. A link to the drivers is below. 
  
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

---

### Post by chili555 on 2008-08-31
> I put the module in /lib/modules.How so? Just copy it? I think if you do:```
cd 2008_0708_RT2860_Linux_STA_v1.7.0.0
sudo make install
sudo modprobe rt2860sta
```you will have better luck. Please let us know.

---

### Post by FallopianJones on 2008-09-09
Thank you, this worked like a charm. I do, however, have another problem. There are 2 options in the config.mk of that driver, HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT. I'm unsure what to mark thees as and also unsure of what driver to use in WPA supplicant (Wext etc.). Any help with this would bve much appreciated.

---

### Post by FallopianJones on 2008-09-12
Anyone know how to fix this?

---

### Post by ttyso4 on 2008-12-13
Hi!

I set both options to "y" and used the wext driver in wpasupplicant, which worked fine for me.

Good luck,
Elli

---

