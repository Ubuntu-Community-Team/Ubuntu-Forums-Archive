---
title: "Belkin desktop G wont associate"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by tamray on 2006-12-05
I am having trouble getting a Belkin PCI dektop G card to come alive on Ubuntu 6.06. It seems to see it is there, but it will not associate with the AP, with and without wep.

Here is the info pertaining to the card:

root@tamray-1:/etc/init.d# iwconfig ath0
ath0      IEEE 802.11  ESSID:"lctn"
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3205-8381-50   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw shows:

  *-network:0
             description: Wireless interface
             product: Atheros Communications, Inc.
             vendor: Atheros Communications, Inc.
             physical id: d
             bus info: pci@00:0d.0
             logical name: ath0
             version: 01
             serial: 00:11:50:d5:06:80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) 



lspci

0000:00:0d.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

---

