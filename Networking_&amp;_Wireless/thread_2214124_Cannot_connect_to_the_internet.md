---
title: "Cannot connect to the internet"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by CrackedP0t on 2014-03-30
A few days ago, I installed Ubuntu GNOME 13.10 on my laptop. My internet worked fine for a few days, then it suddenly stopped. I can't connect to the internet via Wi-Fi or through an Ethernet cable. Here's the result of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr a0:b3:cc:4a:f5:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10272 (10.2 KB)  TX bytes:10272 (10.2 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:3e:84:48:99:73  
          inet6 addr: fe80::1e3e:84ff:fe48:9973/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1852 (1.8 KB)  TX bytes:7547 (7.5 KB)
```

---

### Post by praseodym on 2014-03-30
Hi,

please show these outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```

---

### Post by CrackedP0t on 2014-03-30
uname:
```
 Linux Laptop-of-Power 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
lspci:
```
0a:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci
--
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: r8169
```
lsusb:
```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 05c8:033a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13fe:3800 Kingston Technology Company Inc. Rage XT Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
lsmod:
```
Module                  Size  Used by
usb_storage            62062  1 
snd_hda_codec_hdmi     41154  1 
snd_hda_codec_idt      50341  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431754  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52267  3 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
arc4                   12608  2 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 17377  0 
snd_timer              29433  2 snd_pcm,snd_seq
rt2800pci              18719  0 
microcode              23656  0 
rt2800lib              79992  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
uvcvideo               80885  0 
nouveau               943749  1 
rt2x00lib              55362  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
i915                  661339  3 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
mac80211              597268  3 rt2x00lib,rt2x00pci,rt2800lib
videobuf2_core         40499  1 uvcvideo
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
videodev              133509  2 uvcvideo,videobuf2_core
psmouse                97655  0 
ttm                    84169  1 nouveau
serio_raw              13413  0 
cfg80211              480503  2 mac80211,rt2x00lib
drm_kms_helper         52710  2 i915,nouveau
rtsx_pci_ms            18151  0 
drm                   297056  7 ttm,i915,drm_kms_helper,nouveau
eeprom_93cx6           13344  1 rt2800pci
memstick               16760  1 rtsx_pci_ms
lpc_ich                21080  0 
crc_ccitt              12707  1 rt2800lib
mei_me                 18421  0 
soundcore              12680  1 snd
mei                    77782  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
nls_iso8859_1          12713  2 
ext2                   72949  1 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
mxm_wmi                13021  1 nouveau
hp_accel               26012  0 
video                  19318  2 i915,nouveau
wmi                    19070  3 hp_wmi,mxm_wmi,nouveau
lis3lv02d              20156  1 hp_accel
mac_hid                13205  0 
input_polldev          13896  1 lis3lv02d
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23527  0 
hid_generic            12548  0 
ahci                   25819  3 
r8169                  67581  0 
libahci                32009  1 ahci
usbhid                 53014  0 
mii                    13934  1 r8169
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
hid                   101762  2 hid_generic,usbhid
```
iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
cat:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
```
rfkill:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
Thanks for responding!

---

### Post by praseodym on 2014-03-31
You need nameservers:
```

echo -e "nameserver 8.8.4.4\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
sudo service network-manager restart
```

---

