---
title: "Network suddenly stopped working,"
date: 2014-07-13
forum: Networking &amp; Wireless
---

### Post by elymic on 2014-07-13
Dear all,

I'm a newbie and I write to ask for your help about an issue I have with the network connectivity on my dell desktop.
It all worked perfectly for the past 6 months using wired connection, until yesterday when it failed to connect as usual.. this is frustrating as no change was made that might have caused this (no updates, upgrades etc.)
I searched for a possible solution in the forums, but i couldn't find a full answer to this problem. This is why I post my request here, with some info that might be relevant:

sudo lshw -C network
* *-network************** 
****** description: Ethernet interface
****** product: RTL8111/8168 PCI Express Gigabit Ethernet controller
****** vendor: Realtek Semiconductor Co., Ltd.
****** physical id: 0
****** bus info: pci@0000:02:00.0
****** logical name: eth0
****** version: 06
****** serial: d0:67:e5:07:15:9a
****** size: 100Mbit/s
****** capacity: 1Gbit/s
****** width: 64 bits
****** clock: 33MHz
****** capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
****** configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
****** resources: irq:42 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff

(Before that, I typed "ifconfig eth0 up" but it didn't help..)

By the way, my other devices (like the smartphone I'm using to type this) connect without problem wirelessly to the router.

I would be so grateful for any help you can offer, to bring back lost connection! Many thanks in advance!

---

### Post by praseodym on 2014-07-13
Hi,

please show
```

ifconfig -a
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by grahammechanical on 2014-07-13
> [COLOR=#000000]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s[/COLOR]

That shows that Ubuntu has recognised the ethernet adapter and that a driver for it is installed. By the way, for some strange reason "ifconfig eth0 up" is more likely to work if we first do

```
ifconfig eth0 down
```

We can also run

```
nm-tool
```

See if it lists eth0 "unavailable" or "connected." If "unavailable" check to see if Networking is enabled in the Network Manager icon menu.

Regards.

---

### Post by elymic on 2014-07-14
Hi, thank you for answering!
I paste this from the terminal:

cm@cm-Inspiron-620:~$ ifconfig -a

eth0***** Link encap:Ethernet* HWaddr d0:67:e5:07:15:9a*

********* inet6 addr: fe80::d267:e5ff:fe07:159a/64 Scope:Link

********* UP BROADCAST RUNNING MULTICAST* MTU:1500* Metric:1

********* RX packets:11244 errors:0 dropped:5291 overruns:0 frame:0

********* TX packets:15327 errors:0 dropped:0 overruns:0 carrier:0

********* collisions:0 txqueuelen:1000

********* RX bytes:2322920 (2.3 MB)* TX bytes:3491106 (3.4 MB)


lo******* Link encap:Local Loopback*

********* inet addr:127.0.0.1* Mask:255.0.0.0

********* inet6 addr: ::1/128 Scope:Host

********* UP LOOPBACK RUNNING* MTU:65536* Metric:1

********* RX packets:18600 errors:0 dropped:0 overruns:0 frame:0

********* TX packets:18600 errors:0 dropped:0 overruns:0 carrier:0

********* collisions:0 txqueuelen:0

********* RX bytes:1477288 (1.4 MB)* TX bytes:1477288 (1.4 MB)


cm@cm-Inspiron-620:~$ lsmod

Module***************** Size* Used by

uvcvideo************** 80847* 0

videobuf2_vmalloc***** 13056* 1 uvcvideo

snd_usb_audio******** 140732* 1

videobuf2_memops****** 13202* 1 videobuf2_vmalloc

videobuf2_core******** 40542* 1 uvcvideo

snd_usbmidi_lib******* 24938* 1 snd_usb_audio

videodev************* 129379* 2 uvcvideo,videobuf2_core

nls_iso8859_1********* 12713* 0

parport_pc************ 28152* 0

ppdev***************** 17073* 0

rfcomm**************** 42699* 0

bnep****************** 18177* 2

bluetooth************ 228967* 10 bnep,rfcomm

binfmt_misc*********** 17500* 1

snd_hda_codec_hdmi**** 36855* 1

snd_hda_codec_conexant*** 62000* 1

ext2****************** 72954* 1

joydev**************** 17377* 0

ip6t_REJECT*********** 12574* 1

xt_hl***************** 12521* 6

ip6t_rt*************** 12558* 3

nf_conntrack_ipv6***** 18335* 7

nf_defrag_ipv6******** 13230* 1 nf_conntrack_ipv6

ipt_REJECT************ 12541* 1

xt_LOG**************** 17400* 10

xt_limit************** 12711* 13

xt_tcpudp************* 12603* 18

xt_addrtype*********** 12635* 4

nf_conntrack_ipv4***** 14487* 7

nf_defrag_ipv4******** 12729* 1 nf_conntrack_ipv4

xt_state************** 12578* 14

ip6table_filter******* 12815* 1

ip6_tables************ 27025* 1 ip6table_filter

nf_conntrack_netbios_ns*** 12665* 0

nf_conntrack_broadcast*** 12589* 1 nf_conntrack_netbios_ns

nf_nat_ftp************ 12649* 0

nf_nat**************** 25925* 1 nf_nat_ftp

nf_conntrack_ftp****** 13371* 1 nf_nat_ftp

nf_conntrack********** 83478* 8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6

iptable_filter******** 12810* 1

ip_tables************* 26995* 1 iptable_filter

x_tables************** 29803* 13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT

coretemp************** 13355* 0

kvm_intel************ 132920* 0

kvm****************** 443533* 1 kvm_intel

ghash_clmulni_intel*** 13259* 0

cryptd**************** 20403* 1 ghash_clmulni_intel

snd_hda_intel********* 39619* 3

snd_hda_codec******** 136498* 3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel

snd_hwdep************* 13602* 2 snd_usb_audio,snd_hda_codec

snd_pcm*************** 97451* 4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel

snd_page_alloc******** 18710* 2 snd_pcm,snd_hda_intel

snd_seq_midi********** 13324* 0

snd_seq_midi_event**** 14899* 1 snd_seq_midi

snd_rawmidi*********** 30180* 2 snd_usbmidi_lib,snd_seq_midi

snd_seq*************** 61554* 2 snd_seq_midi_event,snd_seq_midi

snd_seq_device******** 14497* 3 snd_seq,snd_rawmidi,snd_seq_midi

snd_timer************* 29425* 2 snd_pcm,snd_seq

snd******************* 68876* 20 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device

i915***************** 605700* 3

mac_hid*************** 13205* 0

gpio_ich************** 13476* 0

video***************** 19390* 1 i915

drm_kms_helper******** 49394* 1 i915

drm****************** 286260* 4 i915,drm_kms_helper

lp******************** 17759* 0

psmouse*************** 95934* 0

dcdbas**************** 14397* 0

i2c_algo_bit********** 13413* 1 i915

mei******************* 41216* 0

soundcore************* 12680* 1 snd

lpc_ich*************** 17061* 0

parport*************** 46345* 3 lp,ppdev,parport_pc

microcode************* 22939* 0

serio_raw************* 13215* 0

hid_generic*********** 12540* 0

ums_realtek*********** 17949* 0

usb_storage*********** 61300* 1 ums_realtek

r8169***************** 67706* 0

usbhid**************** 47074* 0

hid****************** 101289* 2 hid_generic,usbhid

cm@cm-Inspiron-620:~$ cat etc/network/interfaces

cat: etc/network/interfaces: No such file or directory

cm@cm-Inspiron-620:~$ cat /etc/resolv.conf

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)

#**** DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

cm@cm-Inspiron-620:~$ route -n

Kernel IP routing table

Destination**** Gateway******** Genmask******** Flags Metric Ref*** Use Iface

The "interfaces" file contains:
# interface(s) file used by if up(8) and if down(8)
auto lo
iface lo inet loopback

nm-tool shows the state as "disconnected", because whenever I try to switch it on it trees to connect for a minute, then fails.

---

### Post by praseodym on 2014-07-14
You need nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by elymic on 2014-07-14
Hi praseodym, thanks for your reply. I don't understand what should be the output/should happen after typing the code, could you please explain me?
Thank you

---

### Post by praseodym on 2014-07-15
It adds nameservers to the /etc/resolv.conf file. Without them there will be no connection to resolv (sic!) IP addresses/websites

---

### Post by Daniel_Pinel on 2014-07-16
Is the network interface you are trying to use is working from a Live CD? If is it not, then go take a look in the BIOS.

---

