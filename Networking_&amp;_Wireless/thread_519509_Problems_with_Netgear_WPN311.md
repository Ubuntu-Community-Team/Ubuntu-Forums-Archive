---
title: "Problems with Netgear WPN311"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by diminuto on 2007-08-07
Hi,
This device is supposed to be working "just-out-of-the-box" but I am having problems. I am using Kubuntu Feisty with the last updates. Using lspci I obtain:

>  Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (                                   rev 01)


I installed the madwifi drivers using apt-get. The device is properly detected, this is the information provided by iwconfig:

> ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

However, when I try to scan for routers I do not reach any. Using Windows i can access to mine with more than 90% signal quality.

> sudo iwlist ath0 scan
ath0      No scan results

I have tried different configurations with KNetworkManager also. Any idea what else may I do?

Thank you!

---

### Post by diminuto on 2007-08-07
By the way, this is my lshw -C network output. Any idea, please?

```
*-network:0
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 30
       serial: 00:01:02:a0:af:ca
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.13.33 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a07f iomemory:fb010000-fb01007f irq:20
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@02:04.0
       logical name: wifi0
       version: 01
       serial: 00:18:4d:76:3a:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) ip=192.168.13.33 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fb000000-fb00ffff irq:18
```

---

### Post by TuZhao on 2007-08-09
Hi,
I have the same problem. I replaced my DELL Latitude D505 IntelPro Wireless 2100 MiniPCI card with an **Atheros 5006X** and now I cannot detect any access point.
In Windows I have no problems, works like a charm.
I bought specifically an Atheros card because of compatibility with aircrack-ng suite, but now after having lost a couple of nights of sleep trying to get this thing working I'm really upset.

Is it a problem with Ubuntu only? Is it a kernel issue? I've seen various threads about Atheros cards not working or not being detected and such.

Please can anyone help us?

```
  *-network:0             
       description: Wireless interface
       product: AR5006X 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@01:03.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:ac:a4:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fcfe0000-fcfeffff irq:5

```
```
01:03.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
        Subsystem: Fujitsu Limited. Unknown device 1329
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at fcfe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
```
```
dmesg | grep ath
[   54.472000] ath_hal: module license 'Proprietary' taints kernel.
[   54.472000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   54.940000] ath_pci: 0.9.4.5 (0.9.3.1)
[   55.716000] ath_rate_sample: 1.2 (0.9.3.1)
[  103.660000] ath0: no IPv6 routers present
[  168.264000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  178.280000] ath0: no IPv6 routers present
[  288.388000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  300.336000] ath0: no IPv6 routers present
[  417.784000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  428.512000] ath0: no IPv6 routers present
[  458.896000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  469.640000] ath0: no IPv6 routers present
[  600.656000] ath0: no IPv6 routers present
[ 1192.480000]  [<e0a76575>] ath_vap_delete+0xf5/0x310 [ath_pci]
[ 1768.020000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 1778.856000] ath0: no IPv6 routers present
[ 1845.472000] ath0: no IPv6 routers present

dmesg | grep wifi
[   55.716000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   55.716000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   55.716000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   55.716000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   55.716000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   55.716000] wifi0: mac 10.5 phy 6.1 radio 6.3
[   55.716000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   55.716000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   55.716000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   55.716000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   55.716000] wifi0: Use hw queue 8 for CAB traffic
[   55.716000] wifi0: Use hw queue 9 for beacons
[   55.876000] wifi0: Atheros 5212: mem=0xfcfe0000, irq=5
```

---

### Post by Sendervictorius on 2007-08-09
There are many forum threads devoted to problems with feisty and wireless cards that use the AR5212 chipset. For some reason the madwifi driver seems not to work well with feisty, while it worked fine on edgy and dapper.

In my case I had poor network speed and low signal strength. I tried all manner of solutions suggested on the forums. In the end I disabled the madwifi drivers and installed ndiswrapper - which fixed the problem.

I suggest a search on the forums using "AR5212 Feisty" should turn up something relevant to your problem.

---

