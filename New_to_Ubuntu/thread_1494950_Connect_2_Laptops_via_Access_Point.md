---
title: "Connect 2 Laptops via Access Point"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2010-05-27
Hi

I am trying to connect two Ubuntu laptops via an Access Point, but have no joy.  The laptops are not able to connect to the Access Point. The Access Point (D-Link DAP 1150)named: dlink is listed when I click on the Network button.  Also, the switch on the Access Point is set to AP

Any help will be appreciated.

Thanks

ARNOLD

---

### Post by mikewhatever on 2010-05-27
What type of connection are you trying to establish, wired or wireless. What happens when you try to connect? Any errors?

---

### Post by arnold.pietersen on 2010-05-27
Hi mikewhatever

I am trying to share files between the two laptops wirelessly.  Later on I would want to share the Internet between the two laptops.  

When  I click on dlink, it attempts to connect, but then I get the disconnect message.  This happens on both laptops.

Thanks

---

### Post by mikewhatever on 2010-05-27
> **arnold.pietersen said:**
> Hi mikewhatever

I am trying to share files between the two laptops wirelessly.  Later on I would want to share the Internet between the two laptops. 

Before doing that, you'll have to connect to the access point, so let's leave it for now. 

> When  I click on dlink, it attempts to connect, but then I get the disconnect message.  This happens on both laptops.

Thanks

Open applications->accessories->Terminal and post the output of the following:

cat /etc/lsb-release

nm-tool

---

### Post by arnold.pietersen on 2010-05-27
Hi mikewhatever

The details for the first command is as follows:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

The details for the second command is as follows:
NetworkManager Tool

State: disconnected


** (process:5175): WARNING **: Tried to set deprecated property gsm/band
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        0C:60:76:37:07:AD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    dlink:           Infra, 00:21:91:F8:CB:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    Mega Lube:       Infra, 00:04:ED:55:2D:77, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        00:26:22:27:93:EF

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

Thanks for your assistance

ARNOLD

---

### Post by mikewhatever on 2010-05-27
Thanks for the outputs. I am just trying to gather more info about the hardware and what's going on. So far, it looks like you have an Atheros wireless. Is the router far away from the laptop (just noticed low signal strength)?
Please post some more info from a terminal: 

sudo lshw -C network

tail -n 20 /var/log/daemon.log

---

### Post by arnold.pietersen on 2010-05-27
Hi mikewhatever

Thanks for your reply.  Here is the output:

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 0c:60:76:37:07:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d4600000-d460ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:27:93:ef
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:d3500000-d353ffff ioport:1000(size=128)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 4
       logical name: ib0
       serial: 00:c0:ee:0d:2c:f9
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Here is the output for the second command:

May 27 23:38:46 arnold-laptop ntpd[2855]: frequency initialized -35.581 PPM from /var/lib/ntp/ntp.drift
May 27 23:38:47 arnold-laptop ntpd[2855]: bind() fd 21, family 10, port 123, scope 6, addr fe80::2c0:eeff:fe0d:2cf9, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
May 27 23:38:47 arnold-laptop ntpd[2855]: unable to create socket on ib0 (6) for fe80::2c0:eeff:fe0d:2cf9#123
May 27 23:38:47 arnold-laptop ntpd[2855]: failed to initialize interface for address fe80::2c0:eeff:fe0d:2cf9
May 27 23:38:48 arnold-laptop ntpd_initres[2769]: parent died before we finished, exiting
May 27 23:38:48 arnold-laptop ntpd_initres[2856]: host name not found: ntp2a.mcc.ac.uk
May 27 23:38:48 arnold-laptop ntpd_initres[2856]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
May 27 23:39:01 arnold-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 27 23:39:01 arnold-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 27 23:40:03 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:41:33 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:43:03 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:43:47 arnold-laptop ntpd[2855]: Listening on interface #7 ib0, fe80::2c0:eeff:fe0d:2cf9#123 Enabled
May 27 23:43:47 arnold-laptop ntpd[2855]: Listening on interface #8 ppp0, 41.213.70.38#123 Enabled
May 27 23:44:33 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:46:03 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:47:33 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:49:03 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:50:33 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 
May 27 23:52:03 arnold-laptop wpa_supplicant[1227]: CTRL-EVENT-SCAN-RESULTS 

Thanks for your help

ARNOLD

---

### Post by mikewhatever on 2010-05-27
Right, the following two threads suggest a rather straight forward solution - installing wireless backport modules.
[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341618&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341618&page=2)

I hope there is a way to connect a cable to that laptop. You'll need inernet connection to install the backport modules.

```
sudo apt-get install linux-backports-modules-karmic-generic
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

Reboot when done.

---

