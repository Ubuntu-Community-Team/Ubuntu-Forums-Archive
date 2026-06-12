---
title: "Realtek RTL8139/810x Family Fast Wired Connection don't work. (Lubuntu 13.04)"
date: 2013-10-19
forum: Networking &amp; Wireless
---

### Post by pacer2 on 2013-10-19
[COLOR=#333333][FONT=UbuntuRegular]I need help with my network card, Realtek RTL8139/810x Family Fast, I've trying a lot of things and nothing work. Its what I've do so far..[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Change the driver to 8139cp and 8139too but the CP driver does not do anything, with the "too" start charging but nevers gets connected to internet. Here is all my information maybe you will need :C

[/FONT][/COLOR][HTML]]aguilar@aguilar-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8f:eb:65:b4  
          inet6 addr: fe80::213:8fff:feeb:65b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:293204 (293.2 KB)  TX bytes:293204 (293.2 KB)

aguilar@aguilar-desktop:~$ lsmod | grep 813
8139too                23071  0 


aguilar@aguilar-desktop:~$ lspci -nn | grep Ethernet
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

aguilar@aguilar-desktop:~$ dmesg | grep eth0
[    1.711606] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x0001a800, 00:13:8f:eb:65:b4, IRQ 22
[   13.379267] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.154786] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   25.824075] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   28.832163] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   40.832057] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   64.832122] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   76.832068] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   88.832095] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  106.832156] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  118.832106] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  130.832077] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  154.832081] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  324.248155] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x0001a800, 00:13:8f:eb:65:b4, IRQ 22
[  324.302220] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  334.016074] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  346.016082] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  358.016137] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  370.016093] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  382.016128] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  406.016134] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  418.016051] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  430.016075] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  454.016095] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  466.016048] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  478.016083] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  490.016339] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  502.016116] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  514.016149] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  526.016079] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  556.016087] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  664.016080] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  676.016082] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  718.016074] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  730.016090] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  742.016079] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  766.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  778.016107] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  790.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  830.368249] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x0001a800, 00:13:8f:eb:65:b4, IRQ 22
[  830.438719] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  840.032091] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  852.016129] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  864.016144] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  876.016069] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  888.016072] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  900.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  912.016071] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  924.016143] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  948.016073] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  960.016072] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  972.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1002.016073] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1014.016290] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1026.016129] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1050.016047] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1062.016085] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1074.016116] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1092.016093] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1104.016088] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1116.016052] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1128.016081] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1146.016087] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1158.016092] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1170.016095] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1194.016052] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1206.016082] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1218.016057] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1230.016083] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1

aguilar@aguilar-desktop:~$ dmesg | grep 8139
[    0.102592] pci 0000:01:05.0: [10ec:8139] type 00 class 0x020000
[    1.709759] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.709807] 8139cp 0000:01:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.710780] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.711606] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x0001a800, 00:13:8f:eb:65:b4, IRQ 22
[   19.154786] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   25.824075] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[   25.824077] Modules linked in: ppdev(F) snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) bnep rfcomm snd_rawmidi(F) bluetooth microcode(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) serio_raw(F) soundcore(F) lpc_ich shpchp parport_pc(F) i915 mac_hid video(F) drm_kms_helper drm i2c_algo_bit lp(F) parport(F) hid_generic usbhid hid usb_storage(F) 8139too(F) 8139cp(F) floppy(F)
[   28.832163] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   40.832057] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   64.832122] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   76.832068] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   88.832095] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  106.832156] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  118.832106] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  130.832077] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  154.832081] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  324.242026] 8139too: 8139too Fast Ethernet driver 0.9.28
[  324.248155] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x0001a800, 00:13:8f:eb:65:b4, IRQ 22
[  324.302220] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  334.016074] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  346.016082] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  358.016137] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  370.016093] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  382.016128] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  406.016134] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  418.016051] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  430.016075] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  454.016095] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  466.016048] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  478.016083] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  490.016339] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  502.016116] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  514.016149] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  526.016079] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  556.016087] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  664.016080] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  676.016082] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  718.016074] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  730.016090] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  742.016079] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  766.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  778.016107] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  790.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  798.729069] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[  830.356962] 8139too: 8139too Fast Ethernet driver 0.9.28
[  830.368249] 8139too 0000:01:05.0 eth0: RealTek RTL8139 at 0x0001a800, 00:13:8f:eb:65:b4, IRQ 22
[  830.438719] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  840.032091] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  852.016129] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  864.016144] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  876.016069] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  888.016072] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  900.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  912.016071] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  924.016143] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  948.016073] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  960.016072] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  972.016076] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1002.016073] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1014.016290] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1026.016129] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1050.016047] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1062.016085] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1074.016116] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1092.016093] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1104.016088] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1116.016052] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1128.016081] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1146.016087] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1158.016092] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1170.016095] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1194.016052] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1206.016082] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1218.016057] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[ 1230.016083] 8139too 0000:01:05.0 eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1



aguilar@aguilar-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


> aguilar@aguilar-desktop:~$ sudo lshw -C network PCI (sysfs)   
> *-network               
>        description: Ethernet interface
>        product: RTL-8139/8139C/8139C+
>        vendor: Realtek Semiconductor Co., Ltd.
>        physical id: 5
>        bus info: pci@0000:01:05.0
>        logical name: eth0
>        version: 10
>        serial: 00:13:8f:eb:65:b4
>        size: 10Mbit/s
>        capacity: 100Mbit/s
>        width: 32 bits
>        clock: 33MHz
>        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
>        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=yes maxlatency=64
> mingnt=32 multicast=yes port=MII speed=10Mbit/s [COLOR=#333333][FONT=UbuntuRegular]>        resources: irq:22 ioport:a800(size=256) memory:ff0ff800-ff0ff8ff[/FONT]
[/COLOR][/HTML]
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I really really will apreciate any help, I'm new at Linux so please help me. That PC have not wireless card, so I can't access to internet and its the only Realtek divice installed on the PC.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Sorry for my bad english, im 16 old and I'm from Latin America. 

[/FONT][/COLOR]

---

