---
title: "Atheros AR9285 works but internet VERY Slow"
date: 2018-06-01
forum: Networking &amp; Wireless
---

### Post by robertpmcmahon on 2018-06-01
here is a screen shot..... my question is, if I download a linux driver from HP website they only have .rpm downloads.  I can open the files and drill down to the .bin files for the card, but how do I install them?  Nothing shows up in my drivers & software (additional drivers)



lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: e4:11:5b:52:81:11
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.125 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:30 ioport:5000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 01
       serial: 44:6d:57:13:62:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:d5000000-d500ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by chili555 on 2018-06-01
May we also see the result of:```
dmesg | grep ath
sudo iwlist wlo1 scan
```Only show your network and please disguise the MAC address like this:```
Cell 01 - Address:[COLOR="#FF0000"] XX:2B:B0:DC:45:XX[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000049a4087f52
                    Extra: Last beacon: 664ms ago
                    <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

---

