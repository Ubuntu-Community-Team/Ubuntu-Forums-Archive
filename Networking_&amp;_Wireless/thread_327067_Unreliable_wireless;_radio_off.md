---
title: "Unreliable wireless; radio off?"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by gpaciga on 2006-12-28
I've been having trouble with my wireless network lately. For days it worked fine, so I know that the wireless card I have works and the encryption is all configured correct. Now I'm having problems with the radio of the wireless card spontaneously turning off.

If I restart the computer, it starts to work for a while, but then will (seemingly randomly) stop working, throwing Destination Host Unreachable errors. If I open up the Wireless LAN Manager (wlassistant), it says: **Radio of your wireless card is off**. I can turn it on again, and the internet will work for a few minutes, but then it goes off. Each time I do this, it works for less and less time until it doesn't turn on at all.

My computer, a HP/Compaq Presario X1010CA, has a hardware RF kill switch. As described at [http://ipw2100.sourceforge.net/#issues]("http://ipw2100.sourceforge.net/#issues") I can check the status of the radio using:

```
cat /sys/bus/pci/drivers/ipw2100/*/rf_kill
```

The output of which corresponds to whatever the LED light is trying to indicate, regardless of what wlassistant says. That is, if the light is on I get a 0, meaning radio is on, and if the light is off I get a 2, meaning the radio has been disabled with a hardware swtich. However, regardless of all of that, wlassistant tells me that the radio is off.

I've gone through the [wireless troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") but couldn't find anything to help. Wireless works if I can turn the radio on... I just can't seem to turn the radio on.

Here's the relevant output of the commands they introduce in the troubleshooting guide.

```
$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:63:6c:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:90300000-903000ff irq:10
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:59:a9:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=1.1.4 firmware=712.0.3:3:00000001 link=no multicast=yes wireless=unassociated
       resources: iomemory:90000000-90000fff irq:5

```

```
$lspci -v
0000:02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation MIM2000/Centrino
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

```

```
$lspci -n
0000:02:02.0 0280: 8086:1043 (rev 04)

```

```
$ lsmod | grep 'ipw2100'
ipw2100                88628  0
ieee80211              37064  1 ipw2100

```

```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0

sit0      no wireless extensions.


```

```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:04:23:59:A9:F8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:369182 errors:16 dropped:15 overruns:0 frame:0
          TX packets:364337 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:170591928 (162.6 MiB)  TX bytes:273209753 (260.5 MiB)
          Interrupt:5 Base address:0x6000 Memory:90000000-90000fff

```

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:95:3D:6B:DF
                    ESSID:"Gobo"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:44  Signal level:0  Noise level:0
                    Extra: Last beacon: 180ms ago
          Cell 02 - Address: 02:16:6F:02:31:6C
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Ad-Hoc
                    Channel:10
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:65  Signal level:0  Noise level:0
                    Extra: Last beacon: 1144ms ago

sit0      Interface doesn't support scanning.

```

The network I'm trying to connect to is Gobo. To summarize, if I restart my computer wireless works fine until the computer convinces itself that the radio is off. Any help would be greatly appreciated.

---

