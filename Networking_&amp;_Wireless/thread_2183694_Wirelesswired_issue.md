---
title: "Wireless/wired issue"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by cranecreek on 2013-10-25
A new install of 12.04. I had a wired connection at first then did the updates then all networking stoped working. Upon rebooting no networking was available, but when I changed the kernel at boot time wired works, it all broke when when I installed additional drivers. On reboot  when the grub option for other linux kernels was presented I chose an older version which works with a wired connection but no wireless.```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        00:14:22:A9:3C:55

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.159.193.40
    DNS:             8.8.8.8


  sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a9:3c:55
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.109 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

[CODE]
[CODE]sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a9:3c:55
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.109 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff


``` this is a start, there was an older version of ubuntu  on this laptop that worked fine and it seems to me in the set up there was issues but i dont remember what they were. The main thing to keep in mind here is that this is not the kernel that is default that allows me a wired connection. Grub menu to change kernel at start up which  gives me the option which is strange unless i never paid attention before. Any ideas are appreciated.
Thanks,
Cranecreek

---

### Post by Hadaka on 2013-10-25
Hi,please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot
working now?

---

### Post by cranecreek on 2013-10-25
Thanks for that, closer now. The original kernel boot does allow me to use wired but not wireless. I just want a system that boots up and acts normal. I will try the other boot options and let you you know thanks for the help

---

### Post by cranecreek on 2013-10-25
That did corect the the boot issue thanks for that, but didnt fix the networking problems as far as wirelesss, wired works great. any suggestions?

---

### Post by Hadaka on 2013-10-25
Hi, please post the output of..
```
lsmod
rfkill list all
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by cranecreek on 2013-10-26
```
Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
arc4                   12509  2 
snd_hda_codec_idt      64649  1 
b43                   364596  0 
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_idt,snd_hda_intel
i915                  550464  3 
snd_hwdep              13276  1 snd_hda_codec
joydev                 17329  0 
mac80211              541819  1 b43
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
coretemp               13324  0 
snd_seq_midi           13132  0 
r852                   17873  0 
snd_rawmidi            25157  1 snd_seq_midi
sm_common              16772  1 r852
snd_seq_midi_event     14475  1 snd_seq_midi
nand                   54027  2 r852,sm_common
drm_kms_helper         47749  1 i915
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
mtd                    38990  2 sm_common,nand
drm                   233935  4 i915,drm_kms_helper
cfg80211              453919  2 b43,mac80211
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_ids                8547  1 nand
nand_bch               13003  1 nand
gpio_ich               13278  0 
psmouse                82769  0 
bch                    21767  1 nand_bch
r592                   17808  0 
snd                    57014  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13316  1 i915
dell_wmi               12601  0 
memstick               15885  1 r592
serio_raw              13031  0 
soundcore              12600  1 snd
microcode              18433  0 
nand_ecc               13105  1 nand
ssb_hcd                12781  0 
bcma                   39810  1 b43
dell_laptop            17209  0 
lpc_ich                17048  0 
sparse_keymap          13658  1 dell_wmi
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
dcdbas                 14065  1 dell_laptop
mac_hid                13077  0 
wmi                    18744  1 dell_wmi
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12484  0 
usbhid                 46125  0 
hid                    83062  2 hid_generic,usbhid
b44                    31223  0 
sdhci_pci              18265  0 
firewire_ohci          35914  0 
sdhci                  32339  1 sdhci_pci
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    51554  3 b43,ssb_hcd,b44


```lsmod

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```
rfkill list all
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron E1405 [1028:01d8]
    Kernel driver in use: b44
    Kernel modules: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb


```

---

### Post by Hadaka on 2013-10-26
Hi, your rfkill list is showing a hard block.
press the fn/f2 key ONE time and then do..
```
rfkill unblock all
rfkill list all
```
thanks.

---

### Post by cranecreek on 2013-10-26
Thanks so much for the help. Operator error, wireless not turned on.

---

### Post by Hadaka on 2013-10-26
Hi, glad to see you got it working !
please mark your thread solved
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

