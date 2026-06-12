---
title: "IPW3945 causes deadlock"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by arcanus on 2007-12-31
I have a problem caused by the WLAN card in some way...

When connected to a AP, everything works fine. UNTIL I get high load, or download with a high speed, the card disconnects. The WiFi lamp on the computer is still lit indicating high activity, but the nm-applet tries to reconnect to the AP for ever, and the computer seems to enter a deadlock state. If i catch the disconnect point quick enough, I might be able to disable the wlan card via a hw-switch and reenable it. If i do this, it will work a little bit, then, if the load persists, it will disconnect again.

Some relevant info:
```
 lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:9b:33:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.0.199 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g

lsmod | grep ipw3945
ipw3945               119840  1 
ieee80211              35656  1 ipw3945

lspci | grep Network
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

 dpkg -l | grep network-manager
ii  network-manager                            0.6.5-0ubuntu16.7.10.0
    network management framework daemon
ii  network-manager-gnome                      0.6.5-0ubuntu10          
    network management framework (GNOME frontend

```

Any help would be appreciated...

---

