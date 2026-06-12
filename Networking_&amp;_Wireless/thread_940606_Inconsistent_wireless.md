---
title: "Inconsistent wireless"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Trevorius on 2008-10-07
For the last month or so, my wireless has been working somewhat poorly, which is unusual since wireless support, for me, has always been one of Ubuntu's strong points. I've never had any trouble getting it to work - the connection was instant after enabling restricted drivers. But now, the wireless sporatically drops out and often refuses to reconnect without a full restart. Everything works perfectly when wired, and can work perfectly wireless for hours without acting up. However, when running wireless, it's guaranteed to act up eventually.

When this happens, the Knetwork Manager applet doesn't change nor do I receive any error message. The traffic just doesn't flow. Web pages refuse to load, prompting me to check Ktorrent only to discover that everything has stopped. When I try to restart the connection using the applet, it looks like it will restart, but then hangs at 28% saying "activation stage: configuring device". Eventually, a window pops up asking for the wireless passkey (even though it's stored in K wallet) and re-entering the passkey doesn't achieve anything as it just pops up again in 10-15 seconds.

When this happends, the only thing I've discovered to be 100% successful is a full restart. Restarting the xserver has no effect, nor does restarting the modem, router (which always worked with stobborn connections in XP) or network manager. I've put off asking for advice for a couple weeks now hoping I'd find something by researching, but now I'm fed up.

The computer is an MSI L735 notebook with Ralink wireless RT61/2561 running 7.10 gutsy. The router is a Netgear WGR614 with WPA configuration. The connection is broadband dsl for which the login is stored in the router. Max bandwidth is about 650 KB/s down, and 65 KB/s up. Whenever the comp is running, there's generally a consistent up traffic of about 50-55 KB/ from Ktorrent.

---

### Post by willca on 2008-10-07
Try this out.

create this file if not yet there. Change the ssid and psk appropriately.

/etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="YourWiFiSSID"
   psk="YourWiFiPassword"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }


Save file.

sudo apt-get install wpasupplicant

Test your config if it works.

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

This should give a bunch of output. Hit CTRL-C to get out.

Edit /etc/networking/interfaces

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


Save file and restart networking.

sudo /etc/init.d/networking restart

---

### Post by Trevorius on 2008-10-07
Alrite, when I tried the first part, I was bombarded with errors:

```
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Trying to associate with 00:14:6c:24:04:ac (SSID='***' freq=2462 MHz)
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Associated with 00:14:6c:24:04:ac
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
Authentication with 00:14:6c:24:04:ac timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
Trying to associate with 00:14:6c:24:04:ac (SSID='***' freq=2462 MHz)
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Associated with 00:14:6c:24:04:ac
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
Authentication with 00:14:6c:24:04:ac timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
Trying to associate with 00:14:6c:24:04:ac (SSID='***' freq=2462 MHz)
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Associated with 00:14:6c:24:04:ac
WPA: Key negotiation completed with 00:14:6c:24:04:ac [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:14:6c:24:04:ac completed (auth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:14:6c:24:04:ac (SSID='***' freq=2462 MHz)
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Associated with 00:14:6c:24:04:ac
WPA: Key negotiation completed with 00:14:6c:24:04:ac [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:14:6c:24:04:ac completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:14:6c:24:04:ac (SSID='H***' freq=2462 MHz)
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Associated with 00:14:6c:24:04:ac
WPA: Key negotiation completed with 00:14:6c:24:04:ac [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:14:6c:24:04:ac completed (reauth) [id=0 id_str=]
Associated with 00:14:6c:24:04:ac
l2_packet_receive - recvfrom: Network is down
l2_packet_send - sendto: Network is down
Associated with 00:14:6c:24:04:ac
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Invalid EAPOL-Key MIC - dropping packet
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Invalid EAPOL-Key MIC - dropping packet
Authentication with 00:14:6c:24:04:ac timed out.
```
It basically repeated that about 10 more times, then Knetwork Manager crashed. Similar to what happened when i tried to follow the manual networking guide. I don't really know anything about networking, so I'm not sure what I could be doing wrong. Is it possible that there's an issue with the fact that my ssid contains three spaces and an apostrophe?

---

### Post by Trevorius on 2008-10-07
Any suggestions?

---

### Post by willca on 2008-10-07
Exactly what WPA type of encryption are you running on that wireless network?

The defaul is TKIP. Change that portion to what it is.

---

### Post by Trevorius on 2008-10-09
I would assume it's the default, but I really have no idea. :S I didn't even know there were different types of WPA. All I knew about was WEP, WPA, and WPA2.

---

### Post by hyper_ch on 2008-10-09
if you have a drop out again, run```
iwconfig
``` and check what your rate is set to? I notice on my ralink that it is, after a reboot, set to 1M instead of 54M and hence it fails often.

---

