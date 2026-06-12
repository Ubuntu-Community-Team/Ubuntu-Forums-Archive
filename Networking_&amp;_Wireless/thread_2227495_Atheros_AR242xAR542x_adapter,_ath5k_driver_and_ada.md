---
title: "Atheros AR242x/AR542x adapter, ath5k driver and adapter soft block"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by iivo.kerminen on 2014-06-02
Hi

I have FujitsuSiemens Amilo Li 1720 Model MS2199 laptop with Qualcomm Atheros AR242x/AR542x adapter. Driver is ath5k. My Ubuntu build is 14.04LTS.

My problem is that I can not enable my wireless because of soft block on my wireless adapter. I have tried many things but none have helped. The adapter stays in soft block.

I am thinking that maybe some other module that is loaded is blocking my adapter so that I would need to blacklist this other module but I have no idea what that conflicting driver could be. Below are some outputs from terminal. "rfkill unblock" dont work.

I am not sure that the problem is conflicting module but I dont have any other idea why the soft block wil not go off.

Any help appreciated...



mutsi@mutsi-AMILO-Li-1720:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
mutsi@mutsi-AMILO-Li-1720:~$ clear

mutsi@mutsi-AMILO-Li-1720:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Kiinteä yhteys 1] --------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:0A:E4:BA:93:DD

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.10.100.9
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.100.1

    DNS:             10.10.100.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:C0:A8:C3:76:FA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


mutsi@mutsi-AMILO-Li-1720:~$ sudo lshw -C network
[sudo] password for mutsi: 
  *-network DISABLED      
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:c3:76:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.13.0-27-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:c0100000-c010ffff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:ba:93:dd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.10.100.9 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:a000(size=256) memory:c0201800-c02018ff
mutsi@mutsi-AMILO-Li-1720:~$ 
mutsi@mutsi-AMILO-Li-1720:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    51029  1 
snd_hda_intel          42730  6 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
acer_wmi               31735  0 
snd_hwdep              13272  1 snd_hda_codec
sparse_keymap          13708  1 acer_wmi
snd_pcm                85501  5 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
radeon               1416373  3 
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
ttm                    72698  1 radeon
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
coretemp               13195  0 
ath5k                 134977  0 
snd_timer              28584  2 snd_pcm,snd_seq
r852                   17722  0 
sm_common              16772  1 r852
drm_kms_helper         46907  1 radeon
ath                    23922  1 ath5k
nand                   58760  2 r852,sm_common
nand_ecc               13136  1 nand
joydev                 17101  0 
nand_bch               13067  1 nand
snd                    60871  21 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
bch                    17197  1 nand_bch
mac80211              546013  1 ath5k
drm                   243792  5 ttm,drm_kms_helper,radeon
r592                   17711  0 
nand_ids                8547  1 nand
serio_raw              13230  0 
memstick               16174  1 r592
mtd                    52813  2 nand,sm_common
soundcore              12600  1 snd
i2c_piix4              17723  0 
i2c_algo_bit           13197  1 radeon
cfg80211              409394  3 ath,ath5k,mac80211
ati_agp                13177  0 
shpchp                 32128  0 
wmi                    18673  1 acer_wmi
video                  18903  1 acer_wmi
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
mac_hid                13037  0 
pata_acpi              12886  0 
firewire_ohci          35529  0 
8139too                32571  0 
firewire_core          61867  1 firewire_ohci
8139cp                 27171  0 
sdhci_pci              18535  0 
psmouse                91033  0 
sdhci                  37779  1 sdhci_pci
mii                    13654  2 8139cp,8139too
pata_atiixp            13058  2 
crc_itu_t              12627  1 firewire_core
mutsi@mutsi-AMILO-Li-1720:~$ 
mutsi@mutsi-AMILO-Li-1720:~$ rfkill list 0
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
mutsi@mutsi-AMILO-Li-1720:~$ rfkill unblock 0
mutsi@mutsi-AMILO-Li-1720:~$ rfkill list 0
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
mutsi@mutsi-AMILO-Li-1720:~$

---

### Post by iivo.kerminen on 2014-06-10
Found a solution to this problem. Key was to blacklist acer_wmi and after this, wlan works like a charm.

---

