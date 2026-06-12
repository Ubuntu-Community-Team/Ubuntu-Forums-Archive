---
title: "DHCP Looping in 12.04.3 Server Wireless Connection .."
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by grahjenk on 2013-12-01
Anyone seen this sort of thing before (using wpa_supplicant to connect during boot)?

--
Dec  2 10:41:06 ubuntu wpa_supplicant[638]: WPA: Key negotiation completed with 00:60:64:88:31:2a [PTK=CCMP GTK=CCMP]
Dec  2 10:41:06 ubuntu wpa_supplicant[638]: CTRL-EVENT-CONNECTED - Connection to 00:60:64:88:31:2a completed (auth) [id=0 id_str=]
Dec  2 10:41:07 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Dec  2 10:41:07 ubuntu dhclient: DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
Dec  2 10:41:07 ubuntu dhclient: DHCPOFFER of 192.168.1.105 from 192.168.1.1
Dec  2 10:41:10 ubuntu dhclient: DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
Dec  2 10:41:15 ubuntu dhclient: DHCPREQUEST of 192.168.1.105 on wlan0 to 255.255.255.255 port 67
Dec  2 10:41:20 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Dec  2 10:41:23 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Dec  2 10:41:35  dhclient: last message repeated 2 times
Dec  2 10:41:35 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
 .. etc.
--

wlan0 never actually gets an address. So what's happening, and how do I get around it?

---

### Post by varunendra on 2013-12-03
I believe I've seen such behaviour a few times, but the reasons can be anything that can cause a dodgy connection (authenticated, but not fully connected or stable).

Can you run the "wireless_script" (follow the link in my signature) and post its result here? Since it's a server, I am assuming it has no GUI, but you can copy the result file (wireless-info.txt) to an external drive and post it here.

I don't have any experience of using wpa-supplicant alone, but if there is any obvious culprit with the driver or related settings, some of us may be able to suggest a few things.

---

### Post by grahjenk on 2013-12-04
I gave up and installed Xubuntu-desktop, then used Network-manager .. and it was still a bit dodgy.  I think it has something to do with the rtl8192cu Realtek USB wireless device deciding that it was operating in Taiwan and and failing to correctly negotiate a Wireless-N connection here in Australia.

If I could find an option to tell it it was in Australia, or to persaude it not to try Wireless-N, that would be good. Shame .. it works fine with NetBSD and OpenBSD (which don't support it doing Wireless-N).

So I'm now using a Realtek r8712u device instead .. still under Network-Manager.

---

### Post by varunendra on 2013-12-05
> **grahjenk said:**
> If I could find an option to tell it it was in Australia, or to persaude it not to try Wireless-N, that would be good.

rtl8192cu uses mac80211 driver which in turn uses cfg80211 driver. There is a parameter in the cfg80211 driver which can be used to force a desired regdomain setting. You may try this -
```
sudo modprobe -rv rtl8192cu mac80211 cfg80211
sudo modprobe -v cfg80211 ieee80211_regdom=AU
sudo modprobe -v rtl8192cu
```
This forced setting will be temporary (will be lost at next boot) and if it seems to help, it can be made permanent -
```
echo "options cfg80211 ieee80211_regdom=AU" | sudo tee /etc/modprobe.d/cfg80211.conf
```

This should make the driver load with regulatory domain settings of Australia. But it is interesting that by default it thinks it is in Taiwan. How do you know that (any hints in dmesg?)? And was the location set to Australia while installation?

The N-channel settings can be adjusted in the router only, there is no option with the rtl8192cu driver to ignore or disable that at the card's level, although it seems you already know that. :)

---

