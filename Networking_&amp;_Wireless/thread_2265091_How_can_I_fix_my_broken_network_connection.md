---
title: "How can I fix my broken network connection?"
date: 2015-02-12
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2015-02-12
I'm running Lubuntu 14.04 LTS, dual boot with Windows XP. In Lubuntu, I could connect to the Internet on my home wireless connection, but not on the wired connection. In Windows, neither would connect. I contacted the Microsoft forum and somebody there was very helpful but their suggestions could not fix the problem. So I looked here:

[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

I followed the third method suggested, omitting the steps involving downloaded drivers (as my drivers are included in the kernel, I am told). This involved removing Network Manager, editing /etc/network/interfaces and /etc/resolv.conf, and restarting networking.

That didn't work and now my problem is that I have also lost the ability to connect wirelessly. The hard button on my old HP laptop which turns on wireless no longer lights up.

Can anybody help, please?

---

### Post by rdh61 on 2015-02-12
I've got the hard button for wireless to work again (light on) after booting into Windows then back into Lubuntu. But how do I make the wireless connection when I am missing network manager?
Thank you.

---

### Post by chili555 on 2015-02-12
May we see your /etc/network/interfaces file? Please disguise your wireless password; something like xxxx or <my_password>.

---

### Post by rdh61 on 2015-02-13
/etc/network/interfaces:

```
auto lo
iface lo inet loopback
```

That is all there is in it. (I removed the lines I had appended early - see my original question - when I found it didn't work, so the above is the original content).

---

### Post by rdh61 on 2015-02-13
I have got network-manager and network-manager-gnome back by downloading the .deb packages from Ubuntu Packages and copying them over to the broken system, where they installed without errors. But still no connection. If I click on the "Manage Networks" icon, I can see the name of my connection. When I click on it I am asked for my encryption key but when I enter it nothing happens. The "Manage Networks" icon has an exclamation mark on it. If I right click it, it offers me the possibility to "disable" or "repair". If I click "repair" nothing happens.

---

### Post by chili555 on 2015-02-13
> **rdh61 said:**
> I have got network-manager and network-manager-gnome back by downloading the .deb packages from Ubuntu Packages and copying them over to the broken system, where they installed without errors. But still no connection. If I click on the "Manage Networks" icon, I can see the name of my connection. When I click on it I am asked for my encryption key but when I enter it nothing happens. The "Manage Networks" icon has an exclamation mark on it. If I right click it, it offers me the possibility to "disable" or "repair". If I click "repair" nothing happens.I suggest you delete all existing networks.          

[ATTACH=CONFIG]259950[/ATTACH]


Then reboot and see if the disable or repair warning is gone and, furthermore, if you are able to see and connect to your network.

---

### Post by rdh61 on 2015-02-13
Thank you, that has got me back my wireless connection. :p

But the wired connection ("auto ethernet") still does not work. If I hover my mouse arrow over it while it is trying to connect, , it says "Requesting an ethernet network address for 'Auto Ethernet'..." But it always fails. Can you help me mend this as well?

---

### Post by chili555 on 2015-02-13
I can certainly try. What does this tell us as you are trying to connect?```
dmesg | grep eth
```It might also be helpful to know the ethernet driver from:```
sudo lshw -C network
```

---

### Post by rdh61 on 2015-02-13
```
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ dmesg | grep eth
[    1.811702] 8139too 0000:06:06.0 eth0: RealTek RTL8139 at 0x0001a000, 00:16:d4:43:14:1e, IRQ 22
[    9.036169] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.769712] ACPI Error: Method parse/execution failed [\_SB_.WMID.Z00A] (Node f581e498), AE_AML_OPERAND_TYPE (20131115/psparse-536)
[   20.769723] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f581e678), AE_AML_OPERAND_TYPE (20131115/psparse-536)
[   38.091096] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   50.832056] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   53.840075] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   65.840096] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   77.840106] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   89.840122] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  101.840101] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  113.840105] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  125.840099] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  137.840114] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  149.840126] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  161.840155] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  173.840129] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  185.840139] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  197.840122] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  209.840125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  221.840142] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  233.840122] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  245.840137] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  257.840143] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  269.840143] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  281.840149] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  293.840125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  306.016150] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  318.016139] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  330.016149] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  342.016155] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  354.016168] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  366.016137] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  372.714348] 8139too 0000:06:06.0 eth0: link down
[  375.659384] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  385.024173] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  391.097578] 8139too 0000:06:06.0 eth0: link down
[  392.751216] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  394.262490] 8139too 0000:06:06.0 eth0: link down
[  395.896937] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  405.024137] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  435.024098] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  447.024124] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  459.024145] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  471.024125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  483.024104] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  495.024150] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  507.024153] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  519.024117] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  531.024119] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  543.024149] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  555.024139] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  567.024141] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  579.024127] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  591.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  603.024148] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  615.024126] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  627.024123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  639.024116] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  651.024140] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  663.024135] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  675.024123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  687.024390] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  699.024154] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  711.024128] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  723.024150] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  735.024154] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  747.024155] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  759.024113] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  771.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  783.024140] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  795.024141] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  807.024140] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  819.024119] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  831.024130] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  843.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  855.024119] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  867.024112] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  879.024113] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  891.024124] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  903.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  915.024144] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  927.024094] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  939.024118] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  951.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  963.024136] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  975.024142] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  987.024136] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  999.024112] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1011.024146] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1023.024106] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1035.024147] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1047.024124] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1059.024123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1071.024125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1083.024125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1095.024138] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1107.024131] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1119.024114] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1131.024125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1143.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1155.024150] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1167.024134] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1179.024120] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1191.024136] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1203.024138] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1215.024143] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1227.024140] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1239.024112] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1251.024140] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1263.024137] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1275.024132] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1287.024132] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1299.024119] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1311.024101] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1323.024135] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1335.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1347.024130] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1359.024110] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1371.024131] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1383.024130] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1395.024122] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1407.024123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1419.024120] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1431.024158] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1443.024163] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1455.024147] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1467.024139] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1479.024120] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1491.024141] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1503.024133] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1515.024165] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1527.024123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1539.024118] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1551.024120] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1563.024135] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1575.024101] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1587.024125] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1599.024116] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1611.024093] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1623.024151] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1635.024123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1647.024120] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1659.024122] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1671.024132] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1683.024134] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1695.024153] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$
```

```
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ sudo lshw -C network
[sudo] password for robert: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:43:14:1e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:e4:68:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-45-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ 

```

---

### Post by chili555 on 2015-02-13
This looks perfect:> [ 1695.024153] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1...but this does not:> [   20.769712] ACPI Error: Method parse/execution failed [\_SB_.WMID.Z00A] (Node f581e498), AE_AML_OPERAND_TYPE (20131115/psparse-536)
[   20.769723] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f581e678), AE_AML_OPERAND_TYPE (20131115/psparse-536)We wonder if there are more clues here:```
dmesg | grep -i -e acpi -e 8139
```Sometimes ACPI errors can be reduced or eliminated by setting the BIOS to defaults.

---

### Post by rdh61 on 2015-02-14
```
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ dmesg | grep -i -e acpi -e 8139
[    0.000000] BIOS-e820: [mem 0x0000000037ea0000-0x0000000037eabfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000037eac000-0x0000000037efffff] ACPI NVS
[    0.000000] ACPI: RSDP 000f7c20 000014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 37ea3ed4 000034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 37eabe3b 000074 (v01 HP     Piranha  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 37ea3f08 007F33 (v01     HP     309B 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 37eacfc0 000040
[    0.000000] ACPI: SSDT 37eabeaf 0000CF (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 37eabf7e 000046 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 37eabfc4 00003C (v01 HP     PORSCHE  06040000 LOHR 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.025949] ACPI: Core revision 20131115
[    0.030096] ACPI: All ACPI Tables successfully acquired
[    0.088000] PM: Registering ACPI NVS region [mem 0x37eac000-0x37efffff] (344064 bytes)
[    0.090008] ACPI: bus type PCI registered
[    0.090011] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.092007] ACPI: Added _OSI(Module Device)
[    0.092009] ACPI: Added _OSI(Processor Device)
[    0.092012] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.092014] ACPI: Added _OSI(Processor Aggregator Device)
[    0.094700] ACPI: Interpreter enabled
[    0.094715] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.094720] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.094737] ACPI: (supports S0 S3 S4 S5)
[    0.094740] ACPI: Using IOAPIC for interrupt routing
[    0.094830] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.094947] ACPI: No dock devices found.
[    0.185369] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.185379] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.185386] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.186678] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.186682] acpi PNP0A03:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.186686] acpi PNP0A03:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.186689] acpi PNP0A03:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
[    0.186693] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.186696] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.186705] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-06] only partially covers this bridge
[    0.189491] acpiphp: Slot [1] registered
[    0.189761] pci 0000:06:06.0: [10ec:8139] type 00 class 0x020000
[    0.189960] pci 0000:06:06.0: System wakeup disabled by ACPI
[    0.190326] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.190395] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.190461] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.190527] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.190594] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.190659] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.190725] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.190791] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.216116] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.216126] ACPI: \_SB_.PCI0: notify handler is installed
[    0.216158] Found 1 acpi root devices
[    0.216199] ACPI : EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
[    0.216798] ACPI: bus type USB registered
[    0.217027] PCI: Using ACPI for IRQ routing
[    0.227441] pnp: PnP ACPI init
[    0.227466] ACPI: bus type PNP registered
[    0.227722] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.228021] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.228073] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.228120] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.228155] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.228211] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.228256] pnp 00:06: Plug and Play ACPI device, IDs SYN0120 SYN0100 SYN0002 PNP0f13 (active)
[    0.228396] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.228514] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.252036] pnp: PnP ACPI: found 9 devices
[    0.252038] ACPI: bus type PNP unregistered
[    0.252044] PnPBIOS: Disabled by ACPI PNP
[    0.288633] Switched to clocksource acpi_pm
[    1.190946] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.196046] ACPI: AC Adapter [ACAD] (off-line)
[    1.196149] ACPI: Lid Switch [LID]
[    1.196202] ACPI: Power Button [PWRB]
[    1.196261] ACPI: Power Button [PWRF]
[    1.196323] ACPI: Sleep Button [SLPF]
[    1.196385] ACPI: acpi_idle registered with cpuidle
[    1.214122] ACPI: Invalid active0 threshold
[    1.217338] ACPI: Thermal Zone [THRM] (0 C)
[    1.542029] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.542037] ACPI: Battery Slot [BAT1] (battery present)
[    1.802310] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.802347] 8139cp 0000:06:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.825168] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.868139] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    1.870512] 8139too 0000:06:06.0 eth0: RealTek RTL8139 at 0x0001a000, 00:16:d4:43:14:1e, IRQ 22
[   20.978216] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.014150] acpi device:11: registered as cooling_device1
[   23.893518] ACPI Error: Needed [Buffer/String/Package], found [Integer] f59349c0 (20131115/exresop-590)
[   23.893532] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20131115/dswexec-461)
[   23.893539] ACPI Error: Method parse/execution failed [\_SB_.WMID.Z00A] (Node f581e498), AE_AML_OPERAND_TYPE (20131115/psparse-536)
[   23.893552] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f581e678), AE_AML_OPERAND_TYPE (20131115/psparse-536)
[   27.135204] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   33.824160] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   33.824162] Modules linked in: cuse zram(C) hp_wmi sparse_keymap rfcomm bnep bluetooth arc4 binfmt_misc snd_atiixp snd_atiixp_modem snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi radeon snd_seq_midi_event snd_rawmidi b43 snd_seq bcma ttm snd_seq_device drm_kms_helper snd_timer mac80211 joydev drm snd k8temp serio_raw cfg80211 i2c_algo_bit soundcore ati_agp shpchp i2c_piix4 video wmi parport_pc ppdev lp parport mac_hid pata_acpi 8139too ssb 8139cp psmouse mii pata_atiixp
[   36.832116] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   48.832112] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   60.832077] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   72.832123] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   84.832114] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   96.832142] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  108.832156] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  120.832140] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  132.832217] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  144.832130] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  156.832149] 8139too 0000:06:06.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ 
```

Setting BIOS to defaults did not mend my network connection.

---

