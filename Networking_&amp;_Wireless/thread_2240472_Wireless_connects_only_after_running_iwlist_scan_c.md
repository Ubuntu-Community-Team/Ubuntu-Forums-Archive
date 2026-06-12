---
title: "Wireless connects only after running iwlist scan command -broadcom"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by asadajk on 2014-08-20
I have a old dell inspiron laptop with on board broadcom wireless version:
```
0# lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial:  xx:xx
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:fe5fe000-fe5fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0 
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-25-generic firmware=478.104 ip=192.168.1.101 link=yes multicast=yes wireless=IEEE 802.11bg
```
Wifi is from a MTS Huawei E315 Wifi modem(CDMA broadband). Ubuntu fails to detect and up the wireless interface every time, unless I manually run as root: "iwlist wlan0 scan". I have to try 2 times to get wlan0 to configure with wifi the above command. see below:
```

1st try: ~# iwlist wlan0 scan
wlan0     No scan results

2nd try: ~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-14 dBm  
                    Encryption key:on
                    ESSID:"xysgsgsgs"


```
I ran tail -f /var/log/syslog to trace what happens when the command iwlist scan wlan0 is run. it is attached here:

[http://tr.im/1f1Jy](http://tr.im/1f1Jy)
I have couple of wireless devices including notebooks and mobile phones which sync with the Wifi fine, except for this one. can somebody help me to resolve this issue?

---

### Post by chili555 on 2014-08-20
Please reboot the computer. Before you do anything, run and capture:```
iwconfig
```Note it as iwconfig-before. Now do the scan trick and connect. Then run and capture:```
iwconfig
```Note it as iwconfig-after. Post them both here.

By 'capture,' I mean copy and paste the result into a text document or similar, so you have and can paste into your reply, the two results.

I'm working on a theory about power management.

---

