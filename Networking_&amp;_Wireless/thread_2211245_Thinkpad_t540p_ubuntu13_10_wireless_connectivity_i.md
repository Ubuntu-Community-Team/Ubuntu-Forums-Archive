---
title: "Thinkpad t540p ubuntu13_10 wireless connectivity issue"
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by benjamin16 on 2014-03-15
Hello, guys,

I just bought a new laptop t540p after my old t61 finally gave up. Have both Windows 7 and Ubuntu 13.10 installed on the new machine but the wireless adapter is not working properly in Linux on my machine. Initially the wireless connection did not even show up and thanks to some very helpful posts here I managed to get the laptop connected. However, sadly there is no access to the Internet even though the status shows it is connected already. No response from pinging any other machines in the network including the router. Did try to remove the firewall and set the DNS manually but neither worked. The wireless connection works fine in Windows 7 after the driver has been updated. All other machines don't have any problem in connecting the wifi. 

The wireless adapter is Thinkpad b/g/n wireless card. Please any suggestion that could help me out will be very appreciated!!!

Here are some information:

**$uname -a**
```

Linux bxu-ThinkPad-T540p 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

**$lspci -nn | grep 0280**
```

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:818b]

```

**$cat /etc/lsb-release**
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"

```

**$rfkill list all**
```

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

**$ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 54:ee:75:01:99:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2600000-f2620000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76034 (76.0 KB)  TX bytes:76034 (76.0 KB)


wlan0     Link encap:Ethernet  HWaddr 48:5a:b6:93:72:b5  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5a:b6ff:fe93:72b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:556768 (556.7 KB)  TX bytes:193140 (193.1 KB)

```


**$iwconfig**
```

wlan0     IEEE 802.11bgn  ESSID:"2WIRE105"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: B0:E7:54:58:C7:79   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

```


[B]$lspci -nnk | grep -iA2 net
[/B]```

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
    Subsystem: Lenovo Device [17aa:2210]
    Kernel driver in use: e1000e
--
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]
    Kernel driver in use: rtl8192ee

```

**$lsmod**
```

Module                  Size  Used by
nls_iso8859_1          12713  1 
parport_pc             32701  0 
bnep                   19704  2 
ppdev                  17671  0 
rfcomm                 69130  0 
snd_hda_codec_hdmi     41154  1 
snd_hda_codec_realtek    56475  1 
x86_pkg_temp_thermal    14162  0 
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
joydev                 17377  0 
snd_hda_intel          52267  5 
nouveau               943749  0 
thinkpad_acpi          81113  1 
arc4                   12608  2 
uvcvideo               80885  0 
nvram                  14362  1 thinkpad_acpi
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
i915                  661339  6 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_core         40499  1 uvcvideo
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rtl8192ee             139274  0 
mxm_wmi                13021  1 nouveau
videodev              133509  2 uvcvideo,videobuf2_core
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
btcoexist             105039  1 rtl8192ee
rtlwifi               129442  1 rtl8192ee
ttm                    84169  1 nouveau
snd_timer              29433  2 snd_pcm,snd_seq
drm_kms_helper         52710  2 i915,nouveau
drm                   297056  7 ttm,i915,drm_kms_helper,nouveau
mac80211              597268  2 rtlwifi,rtl8192ee
snd                    69141  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
psmouse                97655  0 
cfg80211              480503  2 mac80211,rtlwifi
microcode              23656  0 
serio_raw              13413  0 
mei_me                 18421  0 
wmi                    19070  2 mxm_wmi,nouveau
mei                    77782  1 mei_me
btusb                  28267  0 
bluetooth             372041  11 bnep,btusb,rfcomm
tpm_tis                19123  0 
i2c_algo_bit           13413  2 i915,nouveau
soundcore              12680  1 snd
video                  19318  2 i915,nouveau
lpc_ich                21080  0 
intel_smartconnect     12690  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
usb_storage            62062  1 
ahci                   25819  4 
e1000e                254604  0 
rtsx_pci               45546  0 
libahci                32009  1 ahci
ptp                    18580  1 e1000e
pps_core               19057  1 ptp

```

**$lshw -C network**
```

  *-network
       description: Ethernet interface
       product: Ethernet Connection I217-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 54:ee:75:01:99:12
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:f2600000-f261ffff memory:f263f000-f263ffff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 48:5a:b6:93:72:b5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ee driverversion=3.11.0-18-generic firmware=N/A ip=192.168.1.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 ioport:4000(size=256) memory:f2400000-f2403fff

```

Thanks in advance!!

---

