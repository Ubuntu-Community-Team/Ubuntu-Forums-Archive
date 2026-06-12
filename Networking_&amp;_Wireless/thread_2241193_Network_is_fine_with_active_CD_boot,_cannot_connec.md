---
title: "Network is fine with active CD boot, cannot connect when booting from HD"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by Carl_Baily on 2014-08-24
I'm trying to install the latest build of Ubuntu on an older Dell laptop (Broadcom wireless and wired network cards).  Everything works fine if I boot from the CD (Live CD), but neither the wired or wireless network cards work if I boot from the HD.  It doesn't identify the wireless adapter, and I get a "no network cable connected" error for the Ethernet port.

Any suggestions?

---

### Post by weatherman2 on 2014-08-24
Go to the "Sticky: Before Posting in Networking & Wireless" at the top of this forum and find the link to the wireless script.  Download it to a thumbdrive on some other computer (or use the live CD that works and save to your hard drive or something), then run the script from the HD boot and post the results here.

---

### Post by Carl_Baily on 2014-08-29
OK, here's the output. 

```

########## wireless info START ##########
Report from: 29 Aug 2014 10:27 MDT -0600
Script from: 17 Aug 2014 02:46 UTC +0000
##### release #####
Distributor ID: Ubuntu
Description: Ubuntu 14.04.1 LTS
Release: 14.04
Codename: trusty
##### kernel #####
Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7
##### desktop #####
Ubuntu
##### lspci #####
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
 Subsystem: Dell Inspiron 6400 [1028:01af]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
 Kernel driver in use: wl
##### lsusb #####
Bus 001 Device 004: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
##### PCMCIA card info #####
##### rfkill #####
##### lsmod #####
ssb                    51854  1 
wl                   3999690  1 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
lib80211               14040  1 wl
cfg80211              409394  1 wl
wmi                    18673  1 dell_wmi
##### interfaces #####
auto lo
iface lo inet loopback
##### ifconfig #####
##### iwconfig #####
lo        no wireless extensions.
##### route #####
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
##### resolv.conf #####
##### nm-tool #####
NetworkManager Tool
State: disconnected
##### NetworkManager.state #####
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
##### NetworkManager.conf #####
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false
##### iw reg get #####
country 00:
 (2402 - 2472 @ 40), (3, 20)
 (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
 (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
##### iwlist channels #####
lo        no frequency information.
##### iwlist scan #####
lo        Interface doesn't support scanning.
##### module infos #####
[ssb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A7:FC:65:90:FC:4A:8D:85:9A:AE:BD:A2:CA:5D:D0:47:16:24:4F:A0
sig_hashalgo:   sha512
[wl]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string
##### module parameters #####
##### /etc/modules #####
lp
##### blacklists #####
[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci
[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
blacklist b44
[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
##### udev rules #####
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
##### dmesg #####
[    8.952827] wl: module license 'MIXED/Proprietary' taints kernel.
[    8.976063] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    9.035016] wl driver 6.30.223.141 (r415941) failed with code 21
[    9.035067] Modules linked in: wl(POF+) dell_wmi sparse_keymap r852 sm_common dell_laptop dcdbas nand coretemp kvm lib80211 snd_hda_intel(+) snd_hda_codec joydev nand_ecc snd_hwdep snd_pcm nand_bch lpc_ich(+) serio_raw snd_page_alloc bch cfg80211 r592 snd_seq_midi snd_seq_midi_event memstick nand_ids snd_rawmidi snd_seq mtd snd_seq_device snd_timer snd soundcore mac_hid i915(+) wmi drm_kms_helper drm parport_pc video i2c_algo_bit ppdev lp parport sdhci_pci psmouse sdhci firewire_ohci firewire_core crc_itu_t
[    9.035215] EIP is at wdev_priv.part.9+0x3/0x5 [wl]
[    9.035338]  [<f95339d7>] wl_cfg80211_detach+0xf7/0x100 [wl]
[    9.035390]  [<f952c3c3>] wl_free_if.isra.12+0x23/0xa0 [wl]
[    9.035442]  [<f952ca68>] wl_free+0x78/0x260 [wl]
[    9.035513]  [<f952cf5e>] wl_pci_probe+0x30e/0x630 [wl]
[    9.035662]  [<f8646017>] wl_module_init+0x17/0x1000 [wl]
[    9.035808] EIP: [<f9533fb6>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f2465bb8
########## wireless info END ############

```

---

### Post by jeremy31 on 2014-08-30
This should work fine with Ubuntu first ```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
```
sudo apt-get purge bcmwl-kernel-source
```
```
sudo apt-get install linux-firmware-nonfree
``` 
And you should be good after a reboot

---

### Post by Carl_Baily on 2014-08-30
Thanks, that fixed both the Ethernet and wireless.  One slight modification...  The third command required an internet connection, so I had to reboot after the purge command. That did get the network going, so the third command was successful after the first reboot.  The wireless didn't work after the first reboot, but was fine after the second..

---

