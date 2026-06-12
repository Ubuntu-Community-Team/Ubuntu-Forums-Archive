---
title: "Force 802.11AC?"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by UnresponsiveBeeVictim on 2016-01-24
I'm running a couple of Airport Extremes in my house for 802.11ac - this has been fine since I hung a switch off my iMac and connected all of my linux stuff / PS4 to it then masqueraded their connections over ac with OSX Connection Sharing.  

I sold my iMac so I ordered a Gigabyte AC adapter and threw it in my new Ubuntu 15 server since it is a known Intel card
```
iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
```

How do I force the thing into using 802.11ac to connect?  It's maxing out around 55mbit transferring across the LAN, so I assume it's running 802.11N.

Should I just buy another Airport Extreme to hang everything off of?

---

### Post by chili555 on 2016-01-25
>  It's maxing out around 55mbit transferring across the LAN, so I assume it's running 802.11N.
It would seem so.

The short answer to your question:> How do I force the thing into using 802.11ac to connect?...is that you may or may not, possibly, if the stars align.

[https://en.wikipedia.org/wiki/IEEE_802.11ac](https://en.wikipedia.org/wiki/IEEE_802.11ac)> IEEE 802.11ac is a wireless networking standard in the 802.11 family (which is marketed under the brand name Wi-Fi), developed in the IEEE Standards Association process,[1] providing high-throughput wireless local area networks (WLANs) on the 5 GHz band.Does your card even do the 5 Ghz band?```
iw list
```Which firmware is loaded? You might have better luck with the latest firmware possible: [https://github.com/OpenELEC/iwlwifi-firmware.git](https://github.com/OpenELEC/iwlwifi-firmware.git) Let me know if you need a step-by-step.

I also recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

---

