---
title: "Wireless issue after upgrade to 12.04"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by neogarfield on 2014-09-12
Hello,

I just upgraded from 10.04 to 12.04, and now my wireless isn't working. I keep getting an error "Wireless network disconnected". I can see the connections, but not connect to them. I tried reinstalling Broadcom drivers, did not help.

I saw the following information asked across threads where people had similar issues, so I'm posting them here. Help would be much appreciated. Thank you!

**iwconfig**
```
lo        no wireless extensions.

eth2      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```
[B]
lspci[/B]
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
```

**lsmod**
```
Module                  Size  Used by
snd_hrtimer            12648  1 
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             25616  0 
vboxnetflt             27270  0 
vboxdrv               299685  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  0 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
nfsd                  230069  13 
nfs                   372372  0 
lockd                  78865  2 nfsd,nfs
fscache                50642  1 nfs
auth_rpcgss            39597  2 nfsd,nfs
nfs_acl                12771  2 nfsd,nfs
binfmt_misc            17292  1 
sunrpc                215112  14 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
snd_hda_codec_conexant    52521  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
lib80211_crypt_tkip    17240  0 
r852                   17901  0 
sm_common              16772  1 r852
r592                   17808  0 
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21784  1 nand_bch
wl                   2906597  0 
memstick               15857  1 r592
nand_ecc               13105  1 nand
psmouse                97218  0 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
snd_seq                51592  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl
snd                    62250  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
e100                   36289  0 
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
i915                  428368  2 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  19115  1 i915

```

**rfkill list all**
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```
[B]
lspci -nnk | grep -iA2 net[/B]
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1375]
	Kernel driver in use: wl
--
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30bb]
	Kernel driver in use: e100
```
[B]
sudo lshw -C network[/B]
```

  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 02
       serial: 00:1a:73:87:b1:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:7e:19:e5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=10.8.16.116 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
```

---

### Post by chili555 on 2014-09-12
I suggest you consult the sticky. The driver wl is incorrect for your device.

---

### Post by Hadaka on 2014-09-12
Hi, please try this from a working wired connection
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

---

### Post by neogarfield on 2014-09-13
Hi,
I just upgraded to 14.04, and it seems to be working now. Thanks for the help! I'll keep posted here if things go awry.

---

