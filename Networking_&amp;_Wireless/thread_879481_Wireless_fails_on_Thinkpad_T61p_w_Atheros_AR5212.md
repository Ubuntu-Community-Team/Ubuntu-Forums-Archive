---
title: "Wireless fails on Thinkpad T61p w/ Atheros AR5212"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by juu on 2008-08-04
I'm running Ubuntu 8.04 on a Thinkpad T61p and trying to connect to a Linksys WRT54G running OpenWRT "White Russian". I've set encryption as WEP on the router (WPA had trouble with my Windows system) and I'm quite sure I'm getting the key right.

But I cannot connect. The wireless connectivity LED on the laptop also doesn't shine, although the Bluetooth one does and can be turned on and off by pressing Fn-F5 as usual.

Any ideas would be appreciated.

```
juu@juu-laptop:~$ lspci | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: IBM ThinkPad 11a/b/g Wireless LAN Mini Express Adapter (AR5BXB6)
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at df2f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1


juu@juu-laptop:~$ ifconfig -a
ath0 Link encap:Ethernet HWaddr 00:1f:3a:4d:34:56
          inet6 addr: fe80::21f:3aff:fe4d:3456/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet HWaddr 00:1f:3a:4d:34:56
          inet addr:169.254.3.249 Bcast:169.254.255.255 Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

eth0 Link encap:Ethernet HWaddr 00:1c:25:76:89:43
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:24433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:28279677 (26.9 MB) TX bytes:2496594 (2.3 MB)
          Base address:0x1840 Memory:fe200000-fe220000

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:1689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:84806 (82.8 KB) TX bytes:84806 (82.8 KB)

wifi0 Link encap:UNSPEC HWaddr 00-1F-3A-4D-34-56-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:342511 errors:0 dropped:0 overruns:0 frame:128693
          TX packets:4645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:34062011 (32.4 MB) TX bytes:213958 (208.9 KB)
          Interrupt:22

juu@juu-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"linksys_SSID" Nickname:""
          Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
          Bit Rate:0 kb/s Tx-Power:8 dBm Sensitivity=1/1
          Retry:off RTS thr:off Fragment thr:off
          Power Management:off
          Link Quality=0/70 Signal level=-90 dBm Noise level=-90 dBm
          Rx invalid nwid:337488 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

juu@juu-laptop:~$ iwlist ath0 scanning
ath0 Scan completed :
          Cell 01 - Address: 00:14:BF:42:54:EA
                    ESSID:"linksys_SSID"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=56/70 Signal level=-39 dBm Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

juu@juu-laptop:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-key aaaaaaaa04
wireless-essid linksys_SSID

auto ath0

juu@juu-laptop:~$ uname -a
Linux juu-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

---

### Post by juu on 2008-08-04
It does, however, work with the Windows driver over ndiswrapper.

---

### Post by montemj on 2008-09-23
I have the same laptop and wireless card, after having played around with it for many months I think the problem stems with the txpower setting. Usually setting it higher seems to resolve troubles for me for awhile, however after a certain period the power setting seems to drop back down and I lose the connection.

Do you see any problems when connecting to a non-wep access point?

Right now I also use ndiswrapper, but that has a host of it's own problems.

---

### Post by willca on 2008-09-24
Try this out.

Edit /etc/network/interfaces

     iface eth0 inet dhcp
             wireless-essid myessid
             wireless-key 123456789e

Change the info to how your wifi nic is identifeid (e.g. wlan0, ath0, etc.). And put in the right essid and key.

Then /etc/init.d/networking restart.

---

