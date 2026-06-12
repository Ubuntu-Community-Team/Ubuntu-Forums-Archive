---
title: "how i can use wireless again?"
date: 2015-06-19
forum: Networking &amp; Wireless
---

### Post by sungkyun on 2015-06-19
in terminal, response to rfkill list all is
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

and response to lsmod is
```
Module                  Size  Used by
vmw_vsock_vmci_transport    26278  0 
vsock                  34903  1 vmw_vsock_vmci_transport
vmw_vmci               62976  1 vmw_vsock_vmci_transport
bnep                   19624  2 
rfcomm                 69509  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_conexant    23109  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_conexant
arc4                   12608  2 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
rtsx_usb_ms            18697  0 
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
memstick               16966  1 rtsx_usb_ms
media                  21903  2 uvcvideo,videodev
rtl8723be              85054  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                64255  2 rtl_pci,rtl8723be
intel_rapl             18783  0 
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm                   452047  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
snd_hda_intel          30469  3 
snd_hda_controller     30228  1 snd_hda_intel
cfg80211              494362  2 mac80211,rtlwifi
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
snd_hda_codec         139682  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
joydev                 17393  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
serio_raw              13483  0 
snd_compress           19200  1 snd_soc_core
snd_pcm_dmaengine      15172  1 snd_soc_core
lpc_ich                21093  0 
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
i915                  906106  3 
snd_seq_midi           13564  0 
btusb                  32497  0 
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             446409  22 bnep,btusb,rfcomm
shpchp                 37047  0 
6lowpan_iphc           18702  1 bluetooth
snd_rawmidi            30876  1 snd_seq_midi
mei_txe                19704  0 
drm_kms_helper         61574  1 i915
mei                    87875  1 mei_txe
drm                   311018  5 i915,drm_kms_helper
iosf_mbi               13541  0 
i2c_algo_bit           13413  1 i915
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ideapad_laptop         18278  0 
snd_timer              29562  2 snd_pcm,snd_seq
sparse_keymap          13948  1 ideapad_laptop
video                  20128  1 i915
i2c_hid                18726  0 
snd                    79468  19 snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
hid                   110426  1 i2c_hid
dw_dmac                12835  0 
dw_dmac_core           28390  1 dw_dmac
snd_soc_sst_acpi       13007  0 
intel_smartconnect     12637  0 
soundcore              15047  2 snd,snd_hda_codec
i2c_designware_platform    12979  0 
i2c_designware_core    14768  1 i2c_designware_platform
spi_pxa2xx_platform    23079  0 
8250_dw                13551  0 
pwm_lpss               13214  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_usb_sdmmc         27787  0 
rtsx_usb               20987  2 rtsx_usb_sdmmc,rtsx_usb_ms
psmouse               106722  0 
r8169                  71694  0 
mii                    13934  1 r8169
ahci                   34062  3 
libahci                32424  1 ahci
sdhci_acpi             13351  0 
sdhci                  43685  1 sdhci_acpi
```

please help me!

---

### Post by jeremy31 on 2015-06-19
What model Lenovo is it?

---

### Post by Bucky Ball on 2015-06-19
Welcome. Please run:

```
sudo lshw -C network
```

... and post the output here between code tags (see last link in my signature). Thanks.

Although you've given some output, there is very little else. Which Ubuntu release and flavour are you using to start, please? ;)

---

### Post by sungkyun on 2015-06-19
model name is lenovo G50-30 80G0

and result of sudo lshw -C network is
```
 *-network DISABLED      
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:29:af:92:12:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.16.0-41-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:2000(size=256) memory:90500000-90503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 68:f7:28:3d:ca:82
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=222.100.101.244 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:105 ioport:1000(size=256) memory:90404000-90404fff memory:90400000-90403fff

```

thanks!

---

### Post by NoWayWin8 on 2015-06-19
This is the problem: ideapad_laptop module  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1324095](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1324095)  If you blacklist that module in /etc/modprobe.d/blacklist.conf, it should work after reboot. ```
sudo sed -i '$ a blacklist ideapad_laptop' /etc/modprobe.d/blacklist.conf
```

---

### Post by jeremy31 on 2015-06-19
> **NoWayWin8 said:**
> This is the problem: ideapad_laptop module  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1324095](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1324095)  If you blacklist that module in /etc/modprobe.d/blacklist.conf, it should work after reboot. ```
sudo sed -i '$ a blacklist ideapad_laptop' /etc/modprobe.d/blacklist.conf
```

I wouldn't blacklist ideapad-laptop as Pilot6 has a ppa with a modified module that fixes the issue, you can get some details from [https://launchpad.net/~hanipouspilot/+archive/ubuntu/ideapad-laptop](https://launchpad.net/~hanipouspilot/+archive/ubuntu/ideapad-laptop)

---

