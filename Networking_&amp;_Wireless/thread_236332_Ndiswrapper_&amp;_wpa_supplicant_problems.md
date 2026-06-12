---
title: "Ndiswrapper &amp; wpa_supplicant problems"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by skattman83 on 2006-08-14
I have a Linksys wusb54gv2 wireless adapter.  I was able to install the windows driver using ndiswrapper, and with it installed I can see the available wireless networks.  I cannot however, connect to my wireless network.  I am using WPA with TKIP encryption.  Any ideas on how to fix this?  I can provide any necessary info as needed, I'm just not sure where to start.

---

### Post by Fass on 2006-08-14
Tried network-manager? If not, how have you set up your wpa_supplicant and how do you start it?

---

### Post by skattman83 on 2006-08-14
I am starting wpa supplicant by using this command:```
sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -dd
```

My /etc/wpa_supplicant.conf looks like this:```
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="MyNetwork'sName"
key_mgmt=WPA-PSK
proto=WPA
pairwise=TKIP
group=TKIP
psk=(this is a really long string of characters generated using wpa_passphrase)

```

---

### Post by skattman83 on 2006-08-14
Sorry, I forgot to mention I've tried network manager, wifi-radar, and network manager gnome, but none of them seem to have done any good.

---

### Post by skattman83 on 2006-08-15
I'm using the ndiswrapper-utils from the repository.  I saw that theres a higher version on sourceforge, so I think this afternoon I'll try that out, see if that helps.

---

### Post by skattman83 on 2006-08-15
I just compiled and installed ndiswrapper 1.23, but it does not seem to have gotten me any further.  When I issue the wpa_supplicant command, it hangs at this part:

```
WPA: Key negotiation completed with 00:12:17:1c:6d:60 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:12:17:1c:6d:60 completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL: startWhen --> 0

```

Does anyone have any ideas what this means?  I checked the mac address, and it is the mac of my router, if that helps any.

---

### Post by skattman83 on 2006-08-15
Nevermind, I'm stupid.  Once it reaches that, all I needed to do was type in dhclient wlan0 in another terminal and then I was connected.

---

