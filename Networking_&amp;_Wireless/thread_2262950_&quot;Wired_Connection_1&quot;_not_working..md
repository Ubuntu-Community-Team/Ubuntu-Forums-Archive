---
title: "&quot;Wired Connection 1&quot; not working."
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by pmasson on 2015-01-28
I am trying to refurbish discarded computers from a school district. All of the machines are Dell Optiplex GX620's with the exact same hardware. I am installing Edubuntu 14.01 on each using the same installation disc on all of them. The machines have been wiped by the district so the Edubuntu installation is the only OS (previously they all ran Windows XP). In addition, all of the machines are using the same Ethernet wire / port (I am literally swapping it in and out of each machine).

The problem is that some of these machines can connect via the Network Manager to "Wired connection 1" (the default Ethernet configuration) and others cannot. Looking at the network / driver information they also appear to be the same. Here is some information that might be helpful (happy to pull more if needed):

- lshw -C network
- lsmod
- cat /etc/network/interfaces
- lspci
- cat /etc/resolv.conf
- cat /etc/udev/rules.d/70-persistent-net.rules
- ifconfig -a

Thanks for your help,
Patrick


```

*************************************************
lshw -C network
*************************************************

WORKING MACHINE: sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:de:40:ac
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5751-v3.44a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fe8f0000-fe8fffff

NOTWORKING MACHINE: sudo lshw -C network
[sudo] password for alex: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:95:f1:7d
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5751-v3.44a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fe8f0000-fe8fffff

*************************************************
lsmod
*************************************************

WORKING MACHINE: lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48417  1 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
binfmt_misc            13140  1 
dcdbas                 14448  0 
i915                  710093  3 
video                  18903  1 i915
drm_kms_helper         48868  1 i915
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
drm                   244037  4 i915,drm_kms_helper
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
serio_raw              13230  0 
snd                    60939  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
tg3                   152160  0 
ptp                    18445  1 tg3
usbhid                 47070  0 
pps_core               18799  1 ptp
psmouse                91357  0 
hid                    87604  2 hid_generic,usbhid
floppy                 55416  0 

NOT WORKING MACHINE: lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48417  1 
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342206  10 bnep,rfcomm
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
i915                  705659  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
video                  18903  1 i915
drm_kms_helper         47182  1 i915
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
drm                   244037  4 i915,drm_kms_helper
binfmt_misc            13140  1 
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
dcdbas                 14448  0 
lpc_ich                16864  0 
serio_raw              13230  0 
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
psmouse                91329  0 
hid                    87604  2 hid_generic,usbhid
floppy                 55416  0 
tg3                   152132  0 
ptp                    18445  1 tg3
pps_core               18799  1 ptp

*************************************************
cat /etc/network/interfaces
*************************************************

WORKING MACHINE cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

NOT WORKING MACHINE cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


*************************************************
lspci
*************************************************

WORKING MACHINE: lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

NOT WORKING MACHINE: lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

*************************************************
cat /etc/resolv.conf 
*************************************************

WORKING MACHINE: cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

NOT WORKING MACHINE: cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

*************************************************
cat /etc/udev/rules.d/70-persistent-net.rules 
*************************************************

WORKING MACHINE: cat /etc/udev/rules.d/70-persistent-net.rules 
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:72:de:40:ac", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

NOT WORKING MACHINE: /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:72:95:f1:7d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

*************************************************
ifconfig -a
*************************************************

WORKING MACHINE: ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:72:de:40:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:415672 (415.6 KB)  TX bytes:11801 (11.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22234 (22.2 KB)  TX bytes:22234 (22.2 KB)

NOT WORKING MACHINE: ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:13:72:95:f1:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149240 (149.2 KB)  TX bytes:23195 (23.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18175 (18.1 KB)  TX bytes:18175 (18.1 KB)

```

---

### Post by Hadaka on 2015-01-28
Hi,please show the output of..
```
cat /etc/resolv.conf
```
on a working and NOT working card
thanks.

---

### Post by pmasson on 2015-01-28
Thanks Hadaka,

I included that in my initial outputs, here it is again (sorry, it was buried) :

```

*************************************************
cat /etc/resolv.conf 
*************************************************

WORKING MACHINE: cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

NOT WORKING MACHINE: cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

```

Thanks - Patrick

---

### Post by pmasson on 2015-02-06
[ 						 							]("http://ubuntuforums.org/member.php?u=1599436")[[COLOR=#000000]Hadaka[/COLOR]]("http://ubuntuforums.org/member.php?u=1599436"),

I was wondering if the information provided you with any ideas / suggestions?

Thanks

---

### Post by chili555 on 2015-02-07
I love a mystery. And by 'love,' I mean hate.

Are there any clues here?```
dmesg | grep -e tg3 -e eth0
cat /var/log/syslog | grep etwork | tail -n25
```As before, for both WORKING and NOTWORKING. As the results are lengthy, please post them here and let us have the link in your reply:  [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by pmasson on 2015-03-03
chili555

please see: [http://paste.ubuntu.com/10517921/](http://paste.ubuntu.com/10517921/)

Also, I apologize for the delays but I only work on these machines once a week. They are machines that a school district has tossed and a few students and I are trying to get them back up to donate to folks in the community.

---

