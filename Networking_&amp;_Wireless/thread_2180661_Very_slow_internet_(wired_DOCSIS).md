---
title: "Very slow internet (wired DOCSIS)"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by tygre2 on 2013-10-14
Hello! I have 5 Mbps internet, it is so on Windows. But when i connect from Linux (Mint) it begins with about 56 kbps and in some minutes comes to 0. How can i fix it?

---

### Post by tygre2 on 2013-10-14
lspci -nnk | grep -iA2 net
```

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
    Kernel driver in use: ath5k
--
08:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: ASUSTeK Computer Inc. L8400B or L3C/S notebook [1043:1045]
    Kernel driver in use: 8139too

```

uname -mr
```

3.8.0-19-generic i686

```

nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
HW Address:        00:50:FC:FC:48:7D

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.110.13.32

    Prefix:          24 (255.255.255.0)
    Gateway:         10.110.13.1

    DNS:             81.9.17.1
    DNS:             81.9.18.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        00:15:AF:6F:4E:70

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

iwconfig
```

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.

```

lsmod
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            47684  1 
arc4                   12543  2 
joydev                 17097  0 
coretemp               13131  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63791  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
pcmcia                 39544  0 
microcode              18286  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
parport_pc             27504  0 
ppdev                  12817  0 
dm_multipath           22402  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
bnep                   17669  2 
scsi_dh                14427  1 dm_multipath
rfcomm                 37420  0 
r592                   17707  0 
snd_timer              24411  2 snd_pcm,snd_seq
bluetooth             202069  10 bnep,rfcomm
psmouse                81038  0 
yenta_socket           27095  0 
sp5100_tco             13447  0 
serio_raw              13031  0 
memstick               15842  1 r592
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
snd                    56485  16 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_piix4              13066  0 
soundcore              12600  1 snd
ath5k                 134997  0 
ath                    19187  1 ath5k
binfmt_misc            17260  1 
asus_laptop            23874  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
mac80211              526519  1 ath5k
mac_hid                13037  0 
cfg80211              436177  3 ath,ath5k,mac80211
shpchp                 32129  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
btrfs                 774622  0 
zlib_deflate           26445  1 btrfs
libcrc32c              12543  1 btrfs
dm_raid45              75357  0 
xor                    26062  1 dm_raid45
dm_mirror              21621  0 
dm_region_hash         16012  1 dm_mirror
dm_log                 18137  3 dm_region_hash,dm_mirror,dm_raid45
pata_acpi              12886  0 
hid_generic            12484  0 
usbhid                 41805  0 
radeon                870822  3 
hid                    82666  2 hid_generic,usbhid
i2c_algo_bit           13197  1 radeon
ttm                    71289  1 radeon
drm_kms_helper         47545  1 radeon
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
pata_atiixp            13058  0 
8139too                23071  0 
8139cp                 26557  0 
drm                   228750  5 ttm,drm_kms_helper,radeon
ahci                   25507  2 
libahci                26108  1 ahci
video                  18894  0 
ati_agp                13177  0 

```

---

