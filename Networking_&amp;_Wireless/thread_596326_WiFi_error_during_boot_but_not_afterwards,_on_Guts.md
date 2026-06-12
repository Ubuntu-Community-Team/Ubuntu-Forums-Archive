---
title: "WiFi error during boot but not afterwards, on Gutsy"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by GozzoMan on 2007-10-29
Hello gentlepersons,
I recently installed Gutsy (a fresh install) on my machine. In Network Settings (i.e. System->Administration->Network) I configured the wireless internet connection, via a USB Belkin WiFi adapter (WPA, password specified, DHCP, and NOT in roaming mode: so I suppose that the intended effect should be the connection to the internet without user intervention).

During boot I see the following:

[INDENT]iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register[/INDENT]

and when I log in I can verify that the connection has in fact NOT been established.


Anyhow, if afterwards I access the Network Settings and modify some parameter, e.g. retype the WPA password, the network is now reconfigured and the connection is now properly established without a fuss.


It seems that, somehow, some piece of code that is used during start-up fails, while some functionally equivalent piece of code, used by the GUI when I'm logged in, works. Or something like that.

Has anyone experienced the same? Any ideas to correct it? Should I file a bug?


Thanks all,

---

### Post by GozzoMan on 2007-10-29
[Sorry, ignore this reply.]

---

### Post by scotclose on 2007-10-31
I think I am seeing the same thing after an upgrade to Gutsy. I have an HP laptop with a built-in broadcom card, but I am using a Netgear pcmcia adapter (Atheros). I am able to enter my WPA password and connect to my network, but when I reboot, I am not connected. If I then go to the Network administration app, I can disable and re-enable the adapter (or enable roaming mode, then disable it) and then it connects.
Also, sometimes Network Password field is blank, even though I had entered it previously.
I never had this problem with previous versions.

---

### Post by GozzoMan on 2007-11-01
It may well be the same issue, scotclose. I too have found the password blank at least one time.

Do you see the same iwlwifi_rc80211_simple message at boot?

If you're not sure, please try in a terminal:
```
dmesg | grep wifi
```

---

### Post by scotclose on 2007-11-01
No, I don't see that. Here's what I get:

[   21.612000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.612000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.612000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.612000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.612000] wifi0: mac 7.9 phy 4.5 radio 5.6
[   21.612000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.612000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.612000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.612000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.612000] wifi0: Use hw queue 8 for CAB traffic
[   21.612000] wifi0: Use hw queue 9 for beacons
[   21.632000] wifi0: Atheros 5212: mem=0x34000000, irq=11

---

### Post by Silent Ninja on 2007-12-24
> **scotclose said:**
> No, I don't see that. Here's what I get:

[   21.612000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.612000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.612000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.612000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.612000] wifi0: mac 7.9 phy 4.5 radio 5.6
[   21.612000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.612000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.612000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.612000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.612000] wifi0: Use hw queue 8 for CAB traffic
[   21.612000] wifi0: Use hw queue 9 for beacons
[   21.632000] wifi0: Atheros 5212: mem=0x34000000, irq=11

Sorry for the revival, but i've the same issue.. although it says some errors at the dmesg, when I log on to the ubuntu desktop it asks me for the wpa password and, voilá it works.. 
Anyhow it re-detects the wifi device, and randomly it hangs up and i have to reselect the wifi network and it works again.. really strange.

here's my dmesg output:
```
[   37.476819] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   37.476861] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   37.476898] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   37.476956] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register

```

I'm on a MSI 670 laptop and i think it's a realtek wifi adapter, but i'm not really sure about it.

---

### Post by Silent Ninja on 2007-12-24
Heey =D
I've fixed it.. check this post:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144621/comments/36](https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144621/comments/36)

Seems a bit complicated but it works, so worths the price

---

