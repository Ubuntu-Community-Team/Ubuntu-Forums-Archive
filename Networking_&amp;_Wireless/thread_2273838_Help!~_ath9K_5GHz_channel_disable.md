---
title: "Help!~ ath9K 5GHz channel disable?"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by melvinc on 2015-04-16
Hi, 

I am new in Linux, and I am seeking for some help to disable the 5GHz channel in the ath9k card.
our system is using a very old kernel 3.10.55 which country code setting is not applied, so we check in forum and found that we could probably have the 5GHz disable option by patch the ath9k driver?

[https://dev.openwrt.org/browser/trunk/package/kernel/mac80211/patches/543-ath9k-allow-to-disable-bands-via-platform-data.patch?rev=37766](https://dev.openwrt.org/browser/trunk/package/kernel/mac80211/patches/543-ath9k-allow-to-disable-bands-via-platform-data.patch?rev=37766)

By the way, is there anyone help can advise how can I use the patch above? I need a step by step guide if possible, I am too new to linux.
Besides, is there anyone verified it works?

thanks

Melvin

---

### Post by melvinc on 2015-04-16
Hi I find that Ubuntu kernel3.19 and 4.0 already have a latest ath9k driver which have the enable and disable 5GHz and 2.4GHz option
[http://lxr.free-electrons.com/source/include/linux/ath9k_platform.h](http://lxr.free-electrons.com/source/include/linux/ath9k_platform.h)

however, I don't know how to enable it, is there any one could help and suggest?

---

### Post by jeremy31 on 2015-04-16
> **melvinc said:**
> Hi I find that Ubuntu kernel3.19 and 4.0 already have a latest ath9k driver which have the enable and disable 5GHz and 2.4GHz option
[http://lxr.free-electrons.com/source/include/linux/ath9k_platform.h](http://lxr.free-electrons.com/source/include/linux/ath9k_platform.h)

however, I don't know how to enable it, is there any one could help and suggest?
I am using kernel 4.0 and I can't find a parameter option for disabling 5 GHz, just has
```
debug:Debugging mask (uint)nohwcrypt:Disable hardware encryption (int)
blink:Enable LED blink on activity (int)
btcoex_enable:Enable wifi-BT coexistence (int)
bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
ps_enable:Enable WLAN PowerSave (int)
use_chanctx:Enable channel context for concurrency (int)

```

---

### Post by melvinc on 2015-04-17
Hi jeremy31, that's why my finding too, i use modinfo to check almost all relative modules and can't see there is a parameter option to disable 5GHz, but I could see the 3.19/4.0 code did add a bool in the ath9k_platform.h and some code in the hw.h, hw.c, init.c

see the patch files below...
[https://dev.openwrt.org/browser/trunk/package/kernel/mac80211/patches/543-ath9k-allow-to-disable-bands-via-platform-data.patch?rev=37766](https://dev.openwrt.org/browser/trunk/package/kernel/mac80211/patches/543-ath9k-allow-to-disable-bands-via-platform-data.patch?rev=37766)


Anyway, I hope there is a expect could explain what's the function of the code??

---

### Post by melvinc on 2015-04-27
Hey Guy, 

Thanks for your help, and Code developer Felix provided some hints to me to hack the driver, and now the problem solved.

thanks for the discussion.

melvin.

---

