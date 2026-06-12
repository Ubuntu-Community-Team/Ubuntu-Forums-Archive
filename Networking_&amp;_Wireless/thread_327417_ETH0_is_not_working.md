---
title: "ETH0 is not working"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by ashrack on 2006-12-29
In the PC there are 2 NICs.
ETH0--> for LAN
ETH1--> for ADSL PPP0

But only ETH1 is enabled and works. ETH0 is non existant.
```
tom@server:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:08:A1:0E:0A:F9  
          inet6 addr: fe80::208:a1ff:fe0e:af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2852137 (2.7 MiB)  TX bytes:349940 (341.7 KiB)
          Interrupt:3 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11780 (11.5 KiB)  TX bytes:11780 (11.5 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.10.45.154  P-t-P:85.10.0.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2782457 (2.6 MiB)  TX bytes:292734 (285.8 KiB)

tom@server:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
tom@server:~$ sudo ifup eth2
Ignoring unknown interface eth2=eth2.
tom@server:~$ sudo lspci
00:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
00:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

```

ps. in Windows both NIC work as promised. And this is a clean install of EDGY with XFCE

---

### Post by Ashrael on 2006-12-29
give us the output of : lsmod (Feed me Seymore, Feed me.....) ;)

---

### Post by amo-ej1 on 2006-12-29
ifconfig only shows the configured interfaces, so your eth0 interface exists, it's only not UP. Do
```

ifconfig -a

```
the get a list of all detected interfaces, also those that are not configured.

---

### Post by ashrack on 2006-12-29
dmesg registers ETH0 and ETH1
```
[17179597.056000] dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
[17179597.148000] eth0: Davicom DM9102 at pci0000:00:08.0, 00:08:a1:75:1c:87, irq 10.
[17179597.228000] eth1: Davicom DM9102 at pci0000:00:09.0, 00:08:a1:0e:0a:f9, irq 3.
[17179621.820000] eth1: no IPv6 routers present
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:08:A1:75:1C:87  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:08:A1:0E:0A:F9  
          inet6 addr: fe80::208:a1ff:fe0e:af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1935 (1.8 KiB)  TX bytes:2171 (2.1 KiB)
          Interrupt:3 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2368 (2.3 KiB)  TX bytes:2368 (2.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.10.46.15  P-t-P:85.10.0.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:965 (965.0 b)  TX bytes:1057 (1.0 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

lsmod
```
Module                  Size  Used by
ipt_TCPMSS              5376  1 
xt_tcpmss               3456  1 
xt_tcpudp               4480  1 
iptable_filter          4224  1 
ip_tables              15204  1 iptable_filter
x_tables               16132  4 ipt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                  16064  2 
pppox                   4872  1 pppoe
ipv6                  272288  14 
af_packet              24584  2 
ppp_generic            30612  6 pppoe,pppox
slhc                    8448  1 ppp_generic
nls_utf8                3200  1 
ntfs                  112116  1 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
lp                     12964  0 
snd_ens1371            28704  0 
gameport               17160  1 snd_ens1371
snd_rawmidi            27264  1 snd_ens1371
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  1 snd_ens1371
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
tsdev                   9152  0 
snd                    58372  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
pcspkr                  4352  0 
snd_page_alloc         11400  1 snd_pcm
serio_raw               8452  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
i2c_piix4              10000  0 
i2c_core               23424  1 i2c_piix4
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
dmfe                   21916  0 
intel_agp              26012  1 
agpgart                34888  1 intel_agp
floppy                 63044  0 
evdev                  11392  1 
jfs                   199396  1 
uhci_hcd               24968  0 
usbcore               134912  2 uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
piix                   11780  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
capability              5896  0 
commoncap               8704  1 capability
vesafb                  9244  1 
fbcon                  41504  70 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit

```

lspci -v
```
00:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
        Subsystem: Unknown device 3030:5032
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e400 [size=256]
        Memory at ea001000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e8000000 [disabled] [size=256K]
        Capabilities: [50] Power Management version 2

00:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
        Subsystem: Unknown device 3030:5032
        Flags: bus master, medium devsel, latency 64, IRQ 3
        I/O ports at e800 [size=256]
        Memory at ea000000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e9000000 [disabled] [size=256K]
        Capabilities: [50] Power Management version 1

```

---

### Post by ashrack on 2006-12-29
I did
'ifconfig eth0 up'
and it came up!
and can also ping other machine with it.
BUt how do I make it permanent?

---

### Post by lloyd_b on 2006-12-29
> I did
'ifconfig eth0 up'
and it came up!
and can also ping other machine with it.
BUt how do I make it permanent?

Look in the file "/etc/network/interfaces", and ensure that it's set to "auto". 

```
auto eth0
iface eth0 inet dhcp
```

Lloyd B.

---

