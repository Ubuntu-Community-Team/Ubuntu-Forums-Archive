---
title: "Monitor mode on AR5416 chipset"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by clausjuhl on 2008-08-16
Hi

I am trying to set my AR5416 Card to monitor mode.

I am using "iwconfig wlan1 mode monitor" (wlan1 is the interface of my wireless card).

I just get the following err. message

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Device or resource busy.

Is this because I do something wrong or because my card/driver does not support monitor mode

---

### Post by tturrisi on 2008-08-16
Your interface is athX, not wlanx.
Type iwconfig & press Enter key.  If wlan1 is the interface then you don't have an atheros chipset.

If you are using ndiswrapper then monitor mode is not possible.

Atheros chipsets:
```
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up
```

---

### Post by clausjuhl on 2008-08-18
> **tturrisi said:**
> Your interface is athX, not wlanx.
Type iwconfig & press Enter key.  If wlan1 is the interface then you don't have an atheros chipset.

If you are using ndiswrapper then monitor mode is not possible.

Atheros chipsets:
```
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up
```

I did also wonder why my interface was WLAN1. However my interface is WLAN1 and my PCMCIA Card is a Linksys WPC300N. If I run "lspci -v | grep Atheros" I get

"16:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)"

So it seem like it is indeed an Atheros chipset. I had a lot of trouble getting this card to work in Ubuntu 8.04. However after installing "ath9k" drivers it was working. Maybe the "ath9k" drivers is the reason why it is detected as wlan1?

Otherwise I do not know why this is detected as wlan1 and not athx.

I am not using ndiswrapper.

I will try your suggested code (using wlanconfig). I did not try this before posting this thread. I just have to install/active wlanconfig because I can not seem to find the command.

I will let you know the results and hopefully you will be able to help me furhter. thanks

---

### Post by clausjuhl on 2008-08-18
Since I am using athk9 drivers I can not do wlanconfig since this is related to madwifi (old version of ath9k).

Does anyone know how to activate monitor mode in when using ath9k drivers (i am using 20080806 version)

---

