---
title: "wpa_supplicant SSID mismatch problem"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by sdaven on 2007-06-09
I'm having a problem with wpa_supplicant on Feisty. Hardware is a Dell 1390 card, using
the bcm43xx drivers, and that much is working fine as I can run Kismet without issue. But
having problems connecting to my WPA wireless network. Running wpa_supplicant, I get:

```

$ **sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd**
...
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flats=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 255 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:09:5b:XX:XX:XX ssid='<hidden>' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
    skip - SSID mismatch
No suitable AP found.
```

The MAC addr of the '<hidden>' SSID is the MAC of my access point. And it is hidden.
I really hope that wpa_supplicant doesn't require me to enable SSID broadcast. Some
old posts (circa 2004) hinted at such.

My wpa_supplicant.conf is:

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
network={
    ssid="myssid"
    scan_ssid=1
    psk=########
}
```

Perusing the forums led me to add the ap_scan and ssid_scan directives since my
AP is hidden. I've tried several variations of the .conf file with no luck. Other (potentially)
relevant information:

```

$ **wpa_supplicant -r**
wpa_supplicant v0.5.5
Copyright (c) 2003-2006, Jouni Malinen <jkmaline@cc.hut.fi> and contrubutors
$ **uname -r**
2.6.20-16-generic
```

Any help is appreciated!

---

### Post by sdaven on 2007-06-09
Ah! Setting ap_scan=2 in wpa_supplicant.conf and letting wpa_supplicant do the scanning did the trick!

---

