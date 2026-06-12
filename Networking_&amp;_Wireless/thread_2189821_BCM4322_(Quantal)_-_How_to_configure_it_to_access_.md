---
title: "BCM4322 (Quantal) - How to configure it to access wifi?"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by caro8pare on 2013-11-24
lspci -vvnn | grep 14e4
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


How to configure 'ath' device or wich driver do I have to install?

I search since 3 days. Help will be really appreciate.

---

### Post by westie457 on 2013-11-24
Hi
The 'ath' driver is no good for a Broadcom chip.

There is enough info in this link to help you get your wireless working. [https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

---

### Post by caro8pare on 2013-11-24
Thank you.

What driver should I download, I'm a beginner.


Is it this one?
[https://launchpad.net/ubuntu/+source/broadcom-sta/5.100.82.112-8~ubuntu12.10.1](https://launchpad.net/ubuntu/+source/broadcom-sta/5.100.82.112-8~ubuntu12.10.1)

do I have to download the 3 files or only one?

---

### Post by westie457 on 2013-11-25
Hopefully you have a cable connected.

The bcmwl driver is available in the repositories.
Open a terminal and run these commands ```
sudo apt-get install bcmwl-kernel-source

sudo modprobe wl
```
Unplug the cable and click on the 'Network' icon, any available networks? If yes choose yours and enter the password for the router.

If none show leave the cable unplugged and reboot the system, it should be working now.

If not working after the reboot post the terminal output of```
lsmod

lshw -C network
```


Thank you

---

### Post by caro8pare on 2013-11-27
Hello,

Here is the output, it seems that the driver is not available in the repositories:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'bcmwl-kernel-source' has no installation candidate


OTHER:
lsmod
Module                  Size  Used by
joydev                 17161  0 
snd_hda_codec_idt      59761  1 
coretemp               13168  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
kvm                   357806  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            17161  0 
psmouse                84843  0 
dcdbas                 14054  1 dell_laptop
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              18209  0 
b43                   347284  0 
mac80211              461161  1 b43
snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16925  0 
serio_raw              13031  0 
cfg80211              175375  2 b43,mac80211
bcma                   34483  1 b43
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i915                  457161  3 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
parport_pc             31968  0 
i2c_algo_bit           13197  1 i915
ppdev                  12817  0 
rfcomm                 37276  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
mac_hid                13037  0 
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ssb                    50087  1 b43
r8169                  55976  0 
karo@KARO:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:d1:ff:dd
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=216.113.111.69 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff
karo@KARO:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
1a:00.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. 1394 OHCI Compliant Host Controller [1217:10f7] (rev 01)
1a:00.1 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:8120] (rev 01)
1a:00.2 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/MSPRO/xD Controller [1217:8130] (rev 01)
karo@KARO:~$ 



Any idea?

---

