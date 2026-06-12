---
title: "Erroneous results from &quot;nm-tool&quot;"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by caljohnsmith on 2008-05-01
I'm connected to the internet via wireless (wlan0), and yet running "nm-tool" returns the following:
```
NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            8139too
  Active:            no
  HW Address:        00:10:B5:83:BC:9D

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings
    Hardware Link:   no
```
My wireless is wlan0, not eth0, and in fact my ethernet is completely unplugged; so what's going on here? Any ideas? Thanks for any help.

---

