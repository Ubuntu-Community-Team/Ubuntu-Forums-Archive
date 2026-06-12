---
title: "Reverting back to ipw3945"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by SniperSlap on 2008-05-06
While I appreciate using good software, it seems pointless to merge to a wireless driver that offers *less* features than ones previously available.

I'm disappointed that using Hardy Heron has actually required me to abandon certain functionality I require?!

I have a 3945ABG WiFi and VMWare was bridging to it perfectly earlier - now, it can't!  This is infuriating.

How do I downgrade from the less developed iwlwifi drivers and go back to using ipw3945 until iwlwifi has reached feature parity with ipw3945?

Grrr.....

---

### Post by chili555 on 2008-05-07
Have you tried:```
sudo apt-get install linux-backports-modules-hardy-generic
```That seems to tune up the 3945ABG for many, including me.

---

### Post by SniperSlap on 2008-05-07
What problems were you experiencing?

I'm mostly interested in getting bridging functionality back in VMWare and maybe even kvm/qemu.

---

### Post by chili555 on 2008-05-07
I was just having slight problems getting and staying connected. The *backports* package fixed them entirely.> bridging functionality back in VMWareI have no experience to offer.

I tried:```
sudo rmmod -f iwl3945 iwlwifi_mac80211
sudo modprobe ipw3945
```and even:```
 sudo modprobe /lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
```But I had no luck. I think the fix may be rather complex, sort of like taking the vermouth out of the martini.

You could try using the GRUB menu to boot into your 2.6.22 kernel, or even remove 2.6.24. (Ouch!)

---

