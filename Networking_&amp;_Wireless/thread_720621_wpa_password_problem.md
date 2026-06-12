---
title: "wpa password problem"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by arno77 on 2008-03-10
Hi.
I just updated from 7.04 to 7.10 but now my WPA password seems not to be recognized anymore:(. I am asked over and over again for my password without connecting to my wireless net. It's a pity because everything worked fine with 7.04.
Anybody who has a similar problem and/or solution to it?

---

### Post by wieman01 on 2008-03-11
Odd but I have heard similar things.

Please post the terminal output of:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
What wireless adapter have you got?

---

### Post by arno77 on 2008-03-11
Hi! Thanks for your reply. Here are the outputs you requested.

[QUOTE=wieman01;4493380]Odd but I have heard similar things.

Please post the terminal output of:
arno@CM1032710-A:~$ sudo iwlist scan
[sudo] password for arno:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0C:F6:08:AF:AA
                    ESSID:"Sitecom SJL"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:16  Signal level:0  Noise level:0
                    Extra: Last beacon: 1692ms ago

arno@CM1032710-A:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:9f:6f:d1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5705-v3.16 ip=137.120.175.201 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:a0:92:f9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
arno@CM1032710-A:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


My wireless adapter is a  PRO/Wireless LAN 2100

---

### Post by wieman01 on 2008-03-11
Please update "/etc/network/interfaces":
> sudo gedit /etc/network/interfaces
Then paste (thereby replacing the contents:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

Then restart the PC. Should you have no Internet connection at all after you have restarted the PC, then make the file read:
> auto lo
iface lo inet loopback
Once again restart the PC.

The ipw2100 is well supported, but seems to be the cause of some issues lately. You aren't on your own...

---

### Post by arno77 on 2008-03-16
Thank's a lot. ... and sorry for my silence for the last two days.

Strangely enough my WPA password is now recognized without me having changed anything. The only thing what's still strange is that it keeps me asking for the keyring password although I am already connected to the wirleless network :confused:

Would you recommend to still follow the procedure you proposed?

---

### Post by wieman01 on 2008-03-16
> **arno77 said:**
> Thank's a lot. ... and sorry for my silence for the last two days.

Strangely enough my WPA password is now recognized without me having changed anything. The only thing what's still strange is that it keeps me asking for the keyring password although I am already connected to the wirleless network :confused:

Would you recommend to still follow the procedure you proposed?
No, not anymore. It's ok now.

---

