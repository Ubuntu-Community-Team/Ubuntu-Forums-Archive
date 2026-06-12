---
title: "Hardware to avoid or not"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by barfobulator on 2009-03-18
I am going to buy a new computer soon, and I would like to know what hardware brands are not recognized by Ubuntu so that I can avoid a computer with those parts. I am not very savvy, so I would prefer to know the ones not supported out of the box. For example, I have had trouble in the past with Broadcom wireless cards and whatever sound card I have now. I would like to buy a computer whole and have Ubuntu run the wireless and the sound from the get-go, so I would like to know what hardware to avoid in my shopping around.

---

### Post by TheUnderTaker on 2009-03-18
Avoid ATI Gpus although AMD/ATI supports them there drivers kinda stink.

---

### Post by LowSky on 2009-03-18
You can buy a Dell with Ubuntu preloaded or a system76 machine and they are guaranteed to work.

Otherwise I can say my Lenovo S10 Netbook worked with Ubuntu just fine, so did my Lenovo T60 that I use at work.

---

### Post by TheUnderTaker on 2009-03-18
Yeah i seemed to have good luck with intel machines. My 1000HD EEEpc netbook works out of the box. Although the native wifi driver is flaky i used ndiswrapper instead and its perfect.

---

### Post by coolbrook on 2009-03-18
Here's a handy guide I bookmarked.

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by sloggerkhan on 2009-03-18
I haven't had an ubuntu machine for about 3 years with any unsuported hardware.

Note that with AMD/ATI graphics you get better open source performance than with nvidia, but binary performance may lack some features (such as gpu video decoding). People whine about ATI graphics more than they're really a problem for typical users IMO. They have some nice features that nVidia's lack, like being able to easily build deb packages for ubuntu from which to install the driver. Intel driver seems like it's been losing performance over last several releases, but feature wise, you shouldn't have any issues with intel. VIA chrome integrated graphics are hopeless to get a good experience out of from what I've encountered, there are like 3 or 4 drivers and none worked properly last I checked, at least if you want more than basic features.

Used to be a lot of problems with wireless, but all my cards/usb sticks/etc now work with linux even if they didn't use to.

Most mobos are fine, I have ASUS and ASrock mobos, have worked with gigabyte mobos, all were fine with linux. However I don't get mobos with weird fancy features, so that could be related. I've heard of problems with a few vendors.

One thing I've noticed is if you look at reviews on newegg.com, a lot of the time someone will comment about linux compatibility. Can be helpful.

---

### Post by cariboo on 2009-03-18
I  would also stay away from SIS and Via graphic chipsets as the are not very well supported if at all.

Jim

---

### Post by leomelo on 2009-03-19
Intel all the way.CPU and motherboard.The GPU:Nvidia,with the driver of its official site.
If you wanna build a goog gaming pc,you can buy these:DX58SO,i7-920.and 8800GT

---

### Post by leomelo on 2009-03-19
correction:DX58SO.You can check them out in Amazom.

---

### Post by leomelo on 2009-03-19
What ia happening? Instead of the letter D ia appearing the smiley.Here i go again:DX58SO

---

### Post by TheUnderTaker on 2009-03-19
I have had luck with the chipset nforce 405 with geforce 6100 on linux. Thats a powerful integrated gpu for the games i used to play on it until i got a power surge.

---

