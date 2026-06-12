---
title: "This network issue is bugging me a lot"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by SwaroopKunduru on 2008-10-10
Hi All,

I have read all the forum to make my wirless work but failed.

Please see my commands and results in the list and please help me.


 ndiswrapper -l

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
01:05.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)
01:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020]
01:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
01:0b.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7897] (rev 02)

uname -m

i686

 lshw -C Network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 03
       serial: 00:30:bd:fd:89:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,07/11/2007, 4.150. latency=66 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

sudo rmmod ssb


ERROR: Module ssb does not exist in /proc/modules


lsmod | grep -e bcm -e b4 -e ssb

bcm43xx               127720  0 
ieee80211softmac       30976  1 bcm43xx
ieee80211              35528  2 bcm43xx,ieee80211softmac

sudo iwconfig wlan0 essid SwaroopKunduru
sudo iwconfig wlan0 key 23056710077409019723090400
sudo dhclient wlan0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:30:bd:fd:89:56
Sending on   LPF/wlan0/00:30:bd:fd:89:56
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


lsmod | grep ndis

ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,usbhid,uhci_hcd

sudo -s
root@swaroop-desktop:~# echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper


dmesg | grep -e ndis -e wlan
[   69.740395] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   69.821096] usbcore: registered new interface driver ndiswrapper
[   78.109693] Modules linked in: ppdev speedstep_lib cpufreq_stats cpufreq_conservative cpufreq_ondemand cpufreq_powersave freq_table cpufreq_userspace video output container sbs dock sbshc battery iptable_filter ip_tables x_tables af_packet ac ndiswrapper sbp2 lp rfkill_input joydev snd_maestro3 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc arc4 ecb blkcipher snd_seq_dummy evdev rfkill snd_seq_oss analog gameport snd_mpu401 snd_mpu401_uart snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq parport_pc parport snd_timer snd_seq_device serio_raw snd soundcore button psmouse i2c_i810 intel_rng intel_agp i2c_algo_bit shpchp pcspkr agpgart pci_hotplug iTCO_wdt iTCO_vendor_support i2c_core ext3 jbd mbcache usbhid hid sg sr_mod cdrom sd_mod pata_acpi floppy ohci1394 ieee1394 uhci_hcd ata_piix ata_generic usbcore libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   78.448324] usbcore: deregistering interface driver ndiswrapper
[   78.542388] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   78.678811] ndiswrapper: driver bcmwl5 (Broadcom,07/11/2007, 4.150.29.0) loaded
[   78.684906] ndiswrapper: using IRQ 5
[   79.198679] wlan0: ethernet device 00:30:bd:fd:89:56 using NDIS driver: bcmwl5, version: 0x4961d00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   79.198800] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   79.198983] usbcore: registered new interface driver ndiswrapper
[  113.469646] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  300.809318] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  319.416971] ADDRCONF(NETDEV_UP): wlan0: link is not ready

lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
01:0b.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)





Regards,

Swaroop Kunduru

---

### Post by jheaton5 on 2008-10-11
You have a lot more experience than me, so don't think that I am being presumptuous.  You have done all the things I know to do and more.  Sometimes the most obvious things are the hardest to see.  Is this problem on a laptop or a desktop?  If a laptop, is the wireless hardware switch turned on?

---

### Post by kevdog on 2008-10-11
remove the bcm43xx driver

---

### Post by jheaton5 on 2008-10-11
I missed that.  Still got a lot to learn.

---

