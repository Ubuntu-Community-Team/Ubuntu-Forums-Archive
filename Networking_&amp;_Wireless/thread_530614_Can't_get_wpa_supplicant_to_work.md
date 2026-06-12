---
title: "Can't get wpa_supplicant to work"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by phreephall on 2007-08-20
I started by looking at this thread:
[http://ubuntuforums.org/showthread.php?t=517644](http://ubuntuforums.org/showthread.php?t=517644)
I have the exact same laptop with the same card, Realtek 8185.

I then went through the maze of ndiswrapper and wpasupplicant wikis and discussions, but I'm still spinning the wheels.

I did get as far as correctly configuring ndiswrapper:
```
[B]
root@BASE:~# lspci -n[/B]
...
08:09.0 0200: 10ec:8185 (rev 20)

**root@BASE:~# lspci**
...
08:09.0 Ethernet controller: Realteek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

**root@BASE: ~# ndiswrapper -l**
net5416 : driver installed
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

```

Trouble is with the wpa_supplicant part. I don't understand where it's supposed to come into play. The card does recognize the wireless networks nearby, but I'm only getting WEP 128/64 bit options in Network Manager when trying to connect to them. No WPA.

How does it know to even look in /etc/default/wpasupplicant? I haven't seen any reference to that file anywhere. Is it correct to use the option "-Dndiswrapper"? Is another wireless manager required to have all encryption options at your disposal?

I'll post the relevant files:

```
**root@BASE:~# cat /etc/default/wpasupplicant **

  ENABLED=1
  OPTIONS="-iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w"
```

```
**root@BASE:~# cat /etc/wpa_supplicant.conf **

#ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="my company network ssid"
        key_mgmt=WPA-EAP
        eap=PEAP
        identity="my.username"
        scan_ssid=1
        psk=233a243740a76d7e9a930e6a94dcffa3d5b072215ec329a16e60f9e1ddc75
}

```

```
**root@BASE:~# cat /etc/network/interfaces **
auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 10.1.22.111
netmask 255.255.255.0
gateway 10.1.22.1

auto eth1
iface eth1 inet dhcp
...

iface wlan0 inet dhcp
wpa-driver ndiswrapper
wpa-conf /etc/wpa_supplicant.conf
```

---

### Post by Jamie Jackson on 2007-08-20
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=529807"), which talks briefly about NetworkManager (which is a confusing name). I just want to make sure you haven't overlooked this roaming networking app.

---

### Post by kevdog on 2007-08-21
Have you just tried to make the connection using wpa_supplicant from the command line, independent of network manager to generate some debugging output

---

### Post by phreephall on 2007-08-21
Yeah I tried to launch wpa_sup like that, getting errors like "Operation not permitted.' I'll post the exact output in a bit.

---

