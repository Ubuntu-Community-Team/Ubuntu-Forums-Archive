---
title: "Acer Aspire E5-575G No LAN Connection"
date: 2017-04-28
forum: Networking &amp; Wireless
---

### Post by Julind on 2017-04-28
Wireless works and all but LAN does not. 

Searched around and some said it was a driver problem so i reinstalled the Realtek LAN driver (r8168) and still get no connection from the LAN. Pinging anything does not return a response or anything. Tried setting a static ip from ifconfig and no succes. Tried all DNS problems, nothing. I have to mention, that the ethernet connection shows up as enp4s0f1 instead of eth0 and on the ethernet connection in network manager it says "auto ethernet".
[B]
In windows however, resetting the winsock and tcp/ip stack fixed it for good, so it works in windows. Its just ubuntu thats giving me problems.

Any help is appreciated.
[/B]
ifonfig
```

enp4s0f1  Link encap:Ethernet  HWaddr 54:ab:3a:98:22:64  
          inet addr:192.168.4.10  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::db64:1556:e85f:7eb4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:488 (488.0 B)  TX bytes:12453 (12.4 KB)
          Interrupt:128 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:68688 (68.6 KB)  TX bytes:68688 (68.6 KB)

wlp3s0    Link encap:Ethernet  HWaddr 74:df:bf:80:1b:f1  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b414:3416:3a9:af77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9855199 (9.8 MB)  TX bytes:715967 (715.9 KB)

```

And on the routing table there appears to be no default gateway.

route
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 enp4s0f1
192.168.4.0     *               255.255.255.0   U     100    0        0 enp4s0f1

```

---

### Post by kc1di on 2017-04-29
could you go to a terminal and install inxi ```
sudo apt-get install inxi
```
when it's finished run this command:
```
inxi -Nn
```
Then post the output so we will know what we are dealing with.

---

### Post by Julind on 2017-05-01
inxi -Nn
```

Network:   Card-1: Qualcomm Atheros Device 0042 driver: ath10k_pci
           IF: wlp3s0 state: down mac: 74:df:bf:80:1b:f1
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8168
           IF: enp4s0f1 state: up speed: 1000 Mbps duplex: full
           mac: 54:ab:3a:98:22:64

```

---

### Post by praseodym on 2017-05-07
Please show
```

sudo apt-get install ethtool
sudo ethtool enp4s0f1
lsmod
```

---

### Post by Julind on 2017-05-10
Out out of  sudo ethtool enp4s0f1
```

Settings for enp4s0f1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```

Output of lsmod
```

sudo lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  0
ccm                    20480  0
msr                    16384  0
rfcomm                 69632  0
arc4                   16384  2
snd_hda_codec_hdmi     53248  1
bnep                   20480  2
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
bbswitch               16384  0
hid_multitouch         20480  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
joydev                 20480  0
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
snd_soc_skl            49152  0
snd_soc_skl_ipc        32768  1 snd_soc_skl
snd_hda_ext_core       28672  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        53248  1 snd_soc_skl_ipc
snd_soc_core          212992  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
dw_dmac_core           24576  1 snd_soc_sst_dsp
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_core            73728  7  snd_hda_codec_realtek,snd_hda_ext_core,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_soc_skl
coretemp               16384  0
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                106496  8  snd_hda_ext_core,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_skl,snd_pcm_dmaengine,snd_hda_core
kvm_intel             172032  0
kvm                   544768  1 kvm_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ghash_clmulni_intel    16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
ath                    32768  1 ath10k_core
aesni_intel           167936  0
mac80211              737280  1 ath10k_core
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_timer              32768  2 snd_pcm,snd_seq
snd                     81920  19  snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
cfg80211              565248  3 ath,mac80211,ath10k_core
rtsx_pci_ms            20480  0
input_leds             16384  0
serio_raw              16384  0
soundcore              16384  1 snd
memstick               20480  1 rtsx_pci_ms
idma64                 20480  0
virt_dma               16384  1 idma64
mei_me                 36864  0
intel_lpss_pci         16384  0
mei                    98304  1 mei_me
shpchp                 36864  0
dell_smo8800           16384  0
wmi                    20480  1 acer_wmi
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
tpm_crb                16384  0
mac_hid                16384  0
acpi_pad               24576  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
rtsx_pci_sdmmc         24576  0
i915_bpo             1302528  4
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  1 i915_bpo
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8168                 487424  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   36864  2
drm                   364544  5 i915_bpo,drm_kms_helper
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  4 i2c_hid,hid_multitouch,hid_generic,usbhid
pinctrl_sunrisepoint    28672  0
video                  40960  2 i915_bpo,acer_wmi
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0

```

---

### Post by Julind on 2017-05-16
Bump again.
Damn this seems to be a hard problem no one is picking on it :grin:

---

### Post by gordintoronto on 2017-05-17
What version of Linux are you running? With a computer that new, it should be 17.04, or maybe 17.10, the development version.

---

### Post by Julind on 2017-05-21
As it says on my Profile info, it is Ubuntu 16.04 Xenial Xerus

---

### Post by Julind on 2017-05-29
Anyone, pls? &#128531;

---

### Post by Julind on 2017-05-30
I fixed it

The routing table was messed up and using the wrong gateway

Editet the interfaces file by setting up a static ip with the correct gateway and its all good now.
Really weird why dhcp was picking up the wrong gateway adress

---

