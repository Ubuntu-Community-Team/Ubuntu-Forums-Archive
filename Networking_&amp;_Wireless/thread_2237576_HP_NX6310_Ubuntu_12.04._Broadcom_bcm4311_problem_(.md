---
title: "HP NX6310 Ubuntu 12.04. Broadcom bcm4311 problem (hard blocked)"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by IPHUN on 2014-08-02
Hi all!

I know this is a common problem and I used to solve it in the past, but now I am stuck. 
So I have an HP NX6310 laptop, with Ubuntu 12.04 (fresh install, but updates already installed)
I have done the followings so far:
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter
sudo apt-get install linux-firmware-nonfree
Results: I have wired connection but no wireless. Rf kill shows that it is hard blocked, 
I have a switch button for turning on/off WIFI which used to work in the past, but now it doesn't react.
```
rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
iphun@iphun-HP-Compaq-nx6310-EY588ES-AKC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.
eth1      no wireless extensions.
     lsmod
Module                  Size  Used by
arc4                   12509  2 
b44                    31407  0 
mii                    13693  1 b44
b43                   369680  0 
mac80211              564484  1 b43
cfg80211              423921  2 b43,mac80211
ssb_hcd                12781  0 
bcma                   46408  1 b43
ssb                    56668  3 b44,b43,ssb_hcd
rfcomm                 59026  0 
bnep                   19107  2 
bluetooth             356681  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  17423  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_analog    14537  1 
snd_hda_intel          43398  3 
snd_hda_codec         169779  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                90501  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25198  1 snd_seq_midi
i915                  733074  3 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17299  0 
pcmcia                 56297  0 
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28971  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 17834  0 
yenta_socket           44622  0 
lpc_ich                16987  0 
sparse_keymap          13658  1 hp_wmi
pcmcia_rsrc            18495  1 yenta_socket
drm_kms_helper         47561  1 i915
psmouse                97578  0 
pcmcia_core            22396  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   249595  4 i915,drm_kms_helper
serio_raw              13230  0 
snd                    61351  17 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13316  1 i915
wmi                    18827  1 hp_wmi
soundcore              12600  1 snd
mac_hid                13077  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19330  1 i915
lp                     13359  0 
parport                40945  3 parport_pc,ppdev,lp
firewire_ohci          36130  0 
ahci                   25703  3 
firewire_core          62418  1 firewire_ohci
libahci                31263  1 ahci
crc_itu_t              12627  1 firewire_core
    sudo lshw -C network
[sudo] password for iphun: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:e8000000-e8003fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth1
       version: 02
       serial: 00:17:08:44:b3:ce
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.114 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:e8108000-e8109fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:d9:33:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-32-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
        
   iwlist scan
wlan0     Failed to read scan data : Network is down
lo        Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
       
```
In the BIOS the following options are:
1. Embedded WLAN Device Radio: Enabled
2. LAN/WLAN Switching: Disabled
3. Wake on LAN: Enabled


Thanks in advance!

---

### Post by praseodym on 2014-08-02
Please try
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot and check the buttons and
```

rfkill list
```

---

### Post by IPHUN on 2014-08-03
Thanks for your help!

```
iphun@iphun-HP-Compaq-nx6310-EY588ES-AKC:~$ echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf  

 [sudo] password for iphun:  

 options hp_wmi wireless=1
```

After reboot:

```
rfkill list all 

 0: phy0: Wireless LAN 

     Soft blocked: no 

     Hard blocked: yes
```

WIFI ON/OFF button still doesn't react.

---

### Post by praseodym on 2014-08-03
Check:
```

sudo modprobe -rfv b43
sudo rfkill unblock all
sudo modprobe -v b43
```

---

### Post by IPHUN on 2014-08-03
```
sudo modprobe -rfv b43

 [sudo] password for iphun:  

 rmmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko

 rmmod /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko

 rmmod /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
 rmmod /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
 iphun@iphun-HP-Compaq-nx6310-EY588ES-AKC:~$ sudo rfkill unblock all
 iphun@iphun-HP-Compaq-nx6310-EY588ES-AKC:~$ sudo modprobe -v b43
 insmod /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko  
 insmod /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko  
 insmod /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko  
 insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko 

 iphun@iphun-HP-Compaq-nx6310-EY588ES-AKC:~$ rfkill list all

 1: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: yes

```

The button still doesn't react.

---

### Post by praseodym on 2014-08-03
Tried to reset the BIOS?

---

### Post by IPHUN on 2014-08-03
I have just done it, and it worked. Now the wifi button is reacting :)
But I don't get it. Every option is the same as I left
1. Embedded WLAN Device Radio: Enabled
2. LAN/WLAN Switching: Disabled
3. Wake on LAN: Enabled

But now it works. 

Anyway, thank you very much for your help!

---

