---
title: "Missing wifi? AR500EG"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by theodore_kh on 2007-12-25
I typed lshw -C network and it shows below.

*-network UNCLAIMED
          description: Ethernet controller
          product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@0000 : 02 :00.0
          version: 01
          width: 64bits
           clock : 33 mhz
           capabilities: cap_list
           configuration: latency = 0
*-network
          description: Ethernet interface
          product: RTL8101E PCI Express Fast Ethernet controller
          vendor: Realtek Semiconductior Co. LTd
           physical id: 0
           bus info: pci@0000:06:00.0
           logical name: eth 0
           version: 01
            serial: 00:1a:80:41:00:51
            width: 64bits
             clock: 33 mhz
             capabillities: bus_master cap_list ethernet physical
            configuration: broadcast=yes driver=r8169 driverversion=.2LK latency= 0 m
odule=r8169 multicast = yes



I'm trying to install ndiswrapper [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
and one of the steps require me to determine my logical name for the wifi adapter. But it doesnt seem to have any. 

How ?

---

### Post by GSF1200S on 2007-12-26
> **theodore_kh said:**
> I typed lshw -C network and it shows below.

*-network UNCLAIMED
          description: Ethernet controller
          product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@0000 : 02 :00.0
          version: 01
          width: 64bits
           clock : 33 mhz
           capabilities: cap_list
           configuration: latency = 0
*-network
          description: Ethernet interface
          product: RTL8101E PCI Express Fast Ethernet controller
          vendor: Realtek Semiconductior Co. LTd
           physical id: 0
           bus info: pci@0000:06:00.0
           logical name: eth 0
           version: 01
            serial: 00:1a:80:41:00:51
            width: 64bits
             clock: 33 mhz
             capabillities: bus_master cap_list ethernet physical
            configuration: broadcast=yes driver=r8169 driverversion=.2LK latency= 0 m
odule=r8169 multicast = yes



I'm trying to install ndiswrapper [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
and one of the steps require me to determine my logical name for the wifi adapter. But it doesnt seem to have any. 

How ?

Do the following command:

```
iwlist scanning
```

Whichever one reports "no scan results" instead of "interface doesnt support scanning."

As an example, this is my iwlist scanning:

```


eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:12:17:D9:68:85
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-65 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
```

In this case, ath0 is my wireless interface- is this what you mean?

---

