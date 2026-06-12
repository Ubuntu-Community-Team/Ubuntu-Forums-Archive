---
title: "Can't restart wireless"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by neilmanson on 2008-06-17
Hi All

I am running Ubuntu Gutsy on a Lenovo ThinkPad T61. I have an ADSL router with built-in wireless access point. This is configured with WPA1 Pre-shared key security. 

When I start the laptop, it correctly detects the wireless network, asks me for my password and connects. However, after some time (1 ~ 3 hours) the network connection dies. When I click on the nm-applet, my home network is listed, but not selected. When I select it, the nm-applet shows that it is trying to connect, but it never does and eventually times out.

I have tried restarting the network by calling /etc/dbus-1/event.d/25NetworkManager, by switching off and on the physical switch on the front of laptop but nothing seems to get the network to restart. I have to reboot the computer to reconnect, which seems like a very un-Linux thing to have to do.

Any ideas or suggestions?

T.I.A.
  Neil

---

### Post by kevdog on 2008-06-17
Have you tried to manually connect?:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by neilmanson on 2008-06-17
> **kevdog said:**
> Have you tried to manually connect?:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Thanks for the link. I will try it next time the network goes down.

---

### Post by neilmanson on 2008-06-17
> **kevdog said:**
> Have you tried to manually connect?:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Hi kevdog

I tried

```
#lshw -C network
```

and got 

```

  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:ed:60:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

However, the interface name is wlan0, not wmaster0

I then created the /etc/wpa_supplicant.conf file, but when I came to run

```
wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd
``` 

I wasn't sure what to use for the driver or the interface (wlan0 or wmaster0).

If I run ```
wpa_supplicant -w -iwlan0 -c/etc/wpa_supplicant.conf -dd
``` 
it generates many lines of output, and then repeats 

```

Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again

```

until I ctrl-C to abort.

Any suggestions?

Thanks

---

