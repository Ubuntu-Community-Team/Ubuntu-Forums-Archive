---
title: "Network Manager miscategorizes wireless card as ethernet (16.04)"
date: 2016-08-06
forum: Networking &amp; Wireless
---

### Post by john-lindgren on 2016-08-06
I have an intermittent problem where Network Manager miscategorizes my wireless card (a TP-LINK USB adapter with an Atheros chipset) as a wired ethernet adapter.  The only "fix" I've found so far is to physically unplug the adapter and plug it in again, or to reboot the machine.

The problem appears to be specific to Network Manager.  Command-line tools such as "iwlist scan" work fine.  I don't recall having this issue in Ubuntu 15.10; it seems to have started appearing after the update to 16.04.

Output of the wireless-info script in a "bad" state and a "good" state (after unplugging the adapter and plugging it in again) are attached.  The blank DRIVER-VERSION and FIRMWARE-VERSION lines in the "bad" file make me wonder if this is a timing issue; i.e. Network Manager is querying the card too soon, before it's fully initialized.

Significant lines:

```
(bad)
GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               

vs.

(good)
GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               1.4
```

---

### Post by wildmanne39 on 2016-08-06
The network being seen as an ethernet connection is a bug and it happened to me too but it was fixed after I upgraded to 1604.1.

Even when my wifi connection showed as an ethernet connection I could still connect to the internet.

---

### Post by wildmanne39 on 2016-08-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by john-lindgren on 2016-08-07
I searched the bug tracker again and found this one (and several others marked as duplicates):
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574347](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574347)

That one is marked as "Fix Released", but I have the most recent version (1.2.0-0ubuntu0.16.04.3) of network-manager installed, so evidently there's more work to be done.

I don't think I've seen this issue after a suspend/resume, only on a cold boot.

---

### Post by wildmanne39 on 2016-08-07
I went and reread all the bug reports and there was a lot of different results when people updated network manager.

One report said that people were updating to the new version before the patch was applied to the new version of network manager so it depends when you installed the new version you might want to reinstall it and see if it works now.

---

