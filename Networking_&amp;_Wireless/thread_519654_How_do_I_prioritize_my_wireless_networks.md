---
title: "How do I prioritize my wireless networks?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by dustrho on 2007-08-07
Everytime I boot up my laptop and gets into Ubuntu, the wireless card starts searching for wireless networks. Unfortunately it ALWAYS tries connecting to my neighbor's wireless network instead of mine. Is there way to prioritize which network it should be attempting to connect to (i.e. my wireless network SHOULD be the first option). Actually, it would be nice to only be able to access my wireless network.

Any ideas or suggestions would be great. Thanks!

**My Setup:**
Sony PCG-TR3A
Ubuntu 7.04 Feisty
Intel 2200BG Wireless

---

### Post by dustrho on 2007-08-08
Anyone? :confused:

---

### Post by gavin72 on 2007-08-08
Well, if you only want to connect to your network, then you can left click on your network manager in the tray and choose manual configuration.

Then disable roaming under properties of Wireless Connection and enter your details manually.

Also under the general tab you can disable automatic service discovery.

In fact, you may need to only do the latter.

---

### Post by sgornick on 2007-08-28
GConf, as described in the Answer to my question here:
  [https://answers.launchpad.net/ubuntu/+question/12327](https://answers.launchpad.net/ubuntu/+question/12327)

---

### Post by dustrho on 2007-08-28
> **sgornick said:**
> GConf, as described in the Answer to my question here:
  [https://answers.launchpad.net/ubuntu/+question/12327](https://answers.launchpad.net/ubuntu/+question/12327)

I did what was suggested there, and we'll see if that helps. I'll keep you posted.

Thanks! :)

---

