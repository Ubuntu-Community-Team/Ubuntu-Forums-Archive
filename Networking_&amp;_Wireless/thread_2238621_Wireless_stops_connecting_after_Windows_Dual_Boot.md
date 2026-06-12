---
title: "Wireless stops connecting after Windows Dual Boot"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by Ryan_MacDowell on 2014-08-09
Hi,
   I've been using ubuntu for about a month now and I have really liked it.  My previous wireless usb adapter was not supported by linux and after trying for awhile to get it to work with ndiswrapper I gave up and bought the Asus USB-N53 adapter.  I plugged it in and everything worked great with the generic drivers and firmware.  I needed to use windows for work so I booted into my windows partition and it installed the windows driver for my adapter, internet worked there and I was able to get my work done.  Ever since then my wireless will not connect to my router in Ubuntu.  It lists all the networks around me and tries to connect for awhile but ultimately will not.

Things i have tried

[LIST]
[*]Installing latest firmware and proprietary drivers for my adapter
[*]Running ipconfig /release on windows before restarting and booting into Ubuntu
[*]Manually releasing the DHCP table reservation from my router and then trying to connect with ubuntu
[/LIST]

Below is the output of some commands I have seen posted while researching myself, hopefully they help

Here is the output of iwconfig
```
[INDENT]ra0       Ralink STA  ESSID:"c225"  Nickname:"RT3572STA"[/INDENT]
[INDENT]          Mode:Managed  Frequency=2.462 GHz  Access Point: C8:D7:19:EE:86:58   [/INDENT]
[INDENT]          Bit Rate=117 Mb/s   [/INDENT]
[INDENT]          RTS thr:off   Fragment thr:off[/INDENT]
[INDENT]          Encryption key:3D88-AA5E-3890-9D44-055C-2922-17AB-E90C   Security mode:restricted   Security mode:open[/INDENT]
[INDENT]          Link Quality=71/100  Signal level:-68 dBm  Noise level:-68 dBm[/INDENT]
[INDENT]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/INDENT]
[INDENT]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT]

```
Here is the output of lsusb
```
[INDENT]Bus 002 Device 007: ID 0461:4d75 Primax Electronics, Ltd Rocketfish RF-FLBTAD Bluetooth Adapter[/INDENT]
[INDENT]Bus 002 Device 006: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)[/INDENT]
[INDENT]Bus 002 Device 005: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)[/INDENT]
[INDENT]Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)[/INDENT]
[INDENT]Bus 002 Device 003: ID 046d:082c Logitech, Inc. [/INDENT]
[INDENT]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/INDENT]
[INDENT]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/INDENT]
[INDENT]Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/INDENT]
[INDENT]Bus 007 Device 003: ID 04a9:1904 Canon, Inc. CanoScan LiDE 100[/INDENT]
[INDENT]Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver[/INDENT]
[INDENT]Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/INDENT]
[INDENT]Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/INDENT]
[INDENT]Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/INDENT]
[INDENT]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/INDENT]
[INDENT]Bus 003 Device 002: ID 0b05:179d ASUSTek Computer, Inc. USB-N53 802.11abgn Network Adapter [Ralink RT3572][/INDENT]
[INDENT]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/INDENT]
[INDENT]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/INDENT]
[INDENT]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/INDENT]

```
Here is the output of lshw -C network```
[INDENT]  *-network
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: c8:60:00:36:d4:b7
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:91 memory:fa700000-fa71ffff memory:fa728000-fa728fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: ra0
       serial: 60:a4:4c:ec:52:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA
[/INDENT]

```


Finally here is the output of iwlist scanning (reduced to my network of interest)```
[INDENT]ra0       Scan completed :
          Cell 12 - Address: C8:D7:19:EE:86:58
                    Protocol:802.11b/g/n
                    ESSID:"c225"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/100  Signal level=-69 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: C8:D7:19:EE:86:59
                    Protocol:802.11a/n
                    ESSID:"c225"
                    Mode:Managed
                    Frequency:5.745 GHz (Channel 149)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-80 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK[/INDENT]

```

---

### Post by Ryan_MacDowell on 2014-08-24
I'm no longer sure why it wasn't working in the first place.  A friend suggested I test and see if it works booting ubuntu from CD in try mode and the wireless was working.  I reverted my change to the new driver and everything seems to be working now. 

I removed the firmware and vendor driver and on restart everything seems to be working.

---

