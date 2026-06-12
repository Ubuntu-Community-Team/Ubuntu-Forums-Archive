---
title: "Conflict between ndiswrapper and restricted drivers?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by sonicmaker on 2008-07-18
Hey all,

I just did a fresh install of Hardy to try to get rid of some problems. I have a Netgear WG311v3 for wireless networking and an ATI HD 2600 XT video card.

My main problem with my previous install was that at almost every boot NetworkManager would ask me for my wireless key (WPA) at least 4 times and never connect.

Everything was hunky dory with this fresh install until I installed Envy NG and got it to install the ATI drivers. From that point, it would do the same old trick with the wireless network - it would ask me for my wireless key multiple times and then fail to connect.

I got Envy to uninstall the ATI drivers and restarted, and could then connect to the wireless network.

I installed the ATI drivers manually from the repository, and then the same old trick - it would ask me for my wireless key multiple times and then fail to connect.

Does anyone have any idea what the heck is going on here?

And if this is worthy of a bug report, where should I aim it?


BTW, running Ubuntu Studio 8.04 x64

---

### Post by sonicmaker on 2008-07-20
Just to bump this, I've updated ndiswrapper, the ati video drivers and the wireless drivers to the latest versions.

More info: dmesg shows the following error numerous times when trying to connect to the network:

> [  214.000074] ndiswrapper (set_essid:59): setting essid failed (C0010015)

Hope someone can help! This totally has me stumped.

---

### Post by JagDragon on 2008-07-20
Check here under the WPAsupplicant step: [http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

Make sure that is configured correctly.

---

### Post by sonicmaker on 2008-07-21
Ok... got it working...

I'd been using the latest stable version of ndiswrapper (1.53), compiled from the source. That wasn't working.

I ditched that and installed ndiswrapper-common, ndiswrapper-utils-1.9 and linux-ubuntu-modules-2.6.24-18-generic (had to re-install that one because ndiswrapper 1.53 had deleted the kernel module) from the Ubuntu repositories, which is equivalent to ndiswrapper 1.50, and it worked fine! So very, very odd. I guess there's a reason the Ubuntu folk haven't upgraded the version in the repository yet, but it just seems strange.

Now to get the ndiswrapper module to load on boot, and I'm all set!

Thanks for your help JagDragon... i tried what you suggested but it didn't work. It was a problem with ndiswrapper not being able to associate with the wireless network, so it was happening before wpa_supplicant could even get its hands on things.

---

