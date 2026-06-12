---
title: "broadcom / dell intermittent failure"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by bkantelis on 2007-01-08
All,
I am having a tough time with my dell laptop and broadcom wireless chipset. It works with ndiswrapper just fine but dies after about 15 minutes of use. It appears that it keeps transmitting fine but nothing is received. I ran iwconfig, any help appreciated.

# lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"kantfam"  Nickname:"kantfam"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:12:88:45:01:A9   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=45/100  Signal level=-67 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by trubblemaker on 2007-01-08
can you post

```
dmesg | grep ndis
ndiswrapper -l
lspci | grep roadcom

```

it will help to figure things out

---

