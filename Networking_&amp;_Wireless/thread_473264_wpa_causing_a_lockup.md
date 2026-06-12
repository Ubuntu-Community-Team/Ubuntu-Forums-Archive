---
title: "wpa causing a lockup"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by gregtrob on 2007-06-13
I have a T42P.  I've tried madwifi (the driver could not keep the signal for anyting) so I migrated to ndiswrapper. With ndiswrapper I can connect to an open router with no problems whatsoever.  However my router is set up to use WPA.  I've read the WPA information around and used the information from the sticky for security. 

My /etc/networking/interfaces looks like

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP RSN
wpa-group TKIP RSN
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>

There appear to be no message in the logs via dmesg.  

When I say lockup I mean lockup.  I have to power the machine down and restart it in order to do anything (not healthy at all).  KDE won't respond to either keyboard or mouse.  

This is on Feisty Kubuntu

---

### Post by spd106 on 2007-06-15
If you're not using the latest version of ndiswrapper then I suggest you download and try that instead. While reading the changelog I noticed that there were some Atheros fixes since Feisty was released.

---

### Post by gregtrob on 2007-06-23
I installed the latest version of ndiswrapper and while things have gotten a little better they still don't seem as stable as that other OS.  Essentailly I can connect and it will stay up for a bit, and then the connection randomly drops.  Anyone have thoughts on that?  At least the lockups appear to have disappeared.  The other weird thing that when I installed the latest ndiswrapper the interface went from being called wlan0 to being called ath0

---

### Post by spd106 on 2007-06-23
[QUOTE=gregtrob]The other weird thing that when I installed the latest ndiswrapper the interface went from being called wlan0 to being called ath0[/QUOTE]

Hmm, are you sure that ndiswrapper is being used and not madwifi. If you run this command it will tell you which driver is in use.
```
sudo lshw -class network
```

---

