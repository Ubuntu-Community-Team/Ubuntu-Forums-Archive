---
title: "IOGEAR GWU625 USB Adapter keeps dropping with Ubuntu 12.04."
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by Hanjaya on 2014-05-25
Hi,

I just bought the IOGEAR GWU625 WiFi USB Adapter and plugged in to my Ubuntu 12.04, then with little configuration it started working. However after a while, I notice that the connection keeps dropping frequently then I have to wait until it gets connected again to use the internet.

Here are some hints:

```

root@han-ubuntu:/home/chanjay# lsusb
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

root@han-ubuntu:/home/chanjay# nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unmanaged
  Default:           no
  HW Address:        00:15:C5:7B:10:27


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             unmanaged
  Default:           no
  HW Address:        00:21:79:C5:C0:79


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 



```

I am not sure what's going on? Are there any conflicts or should I blacklist some drivers?

Please help.

Thank you.

hc.

---

