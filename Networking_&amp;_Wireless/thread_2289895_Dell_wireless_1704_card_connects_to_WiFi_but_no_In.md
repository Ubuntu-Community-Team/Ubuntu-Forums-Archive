---
title: "Dell wireless 1704 card connects to WiFi but no Internet"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by bublz2 on 2015-08-07
Hello everyone :) 

I have an issue with my dell wireless 1704 card, it  connects to my WiFi but there is no Internet when I try to go into Firefox etc.  I tried installing the drivers but that didn't work. Can anyone help me please I really need help

---

### Post by praseodym on 2015-08-08
Please open a terminal with CTRL+ALT+T and show the outputs of these commands
```

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
ifconfig -a
```

---

### Post by bublz2 on 2015-08-15
> **praseodym said:**
> Please open a terminal with CTRL+ALT+T and show the outputs of these commands
```

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
ifconfig -a
```

Sorry i haven't been on in  a while i was away on a vacation.
Also i figured something out and its really weird, in the morning when i switch my router on and connect to it, it works perfectly no problems or anything but in the evening when i turn my laptop back on again and try to connect to it, it connect but no internet. The router hasn't been switched on/off during the day but it doesn't work and the only way to resolve this is to reboot the router. I know you can say that you can reboot it every night but i don't want to be getting up every single night rebooting the router. If you could fix this I would gladly appreciate it, thanks :)
Also I switched to Ubuntu MATE and I still have the same problem

Here's what you asked for 
[INDENT]```

destiny@destiny:~$ uname -a
Linux destiny 3.19.0-25-generic #26-Ubuntu SMP Fri Jul 24 21:17:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```

destiny@destiny:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
    Subsystem: Dell Device [1028:0654]
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 [8086:9c90] (rev e3)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 [8086:9c94] (rev e3)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 [8086:9c96] (rev e3)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 [8086:9c98] (rev e3)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB EHCI Controller [8086:9ca6] (rev 03)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc3] (rev 03)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83] (rev 03)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
    Subsystem: Dell Device [1028:0654]
06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: wl
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:0654]
    Kernel driver in use: r8169

```

```

destiny@destiny:~$ lsusb
Bus 003 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 003 Device 004: ID 0c45:670b Microdia 
Bus 003 Device 003: ID 046d:c534 Logitech, Inc. 
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

destiny@destiny:~$ lsmod
Module                  Size  Used by
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               458752  3 vboxnetadp,vboxnetflt,vboxpci
binfmt_misc            20480  1 
rfcomm                 69632  12 
bnep                   20480  2 
nls_iso8859_1          16384  1 
rtsx_usb_ms            20480  0 
memstick               20480  1 rtsx_usb_ms
dell_led               16384  1 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_soc_rt5640         94208  0 
btusb                  40960  0 
v4l2_common            16384  1 videobuf2_core
snd_hda_codec_hdmi     53248  1 
dell_wmi               16384  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_hda_intel          36864  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_soc_core          196608  1 snd_soc_rt5640
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
bluetooth             491520  22 bnep,btusb,rfcomm
i915                 1056768  3 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
sparse_keymap          16384  1 dell_wmi
intel_rapl             20480  0 
media                  24576  2 uvcvideo,videodev
iosf_mbi               16384  1 intel_rapl
hid_rmi                20480  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
snd_compress           20480  1 snd_soc_core
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wl                   6369280  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
cfg80211              540672  1 wl
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           172032  1 
aes_x86_64             20480  1 aesni_intel
dell_laptop            16384  0 
lrw                    16384  1 aesni_intel
dcdbas                 16384  1 dell_laptop
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
i8k                    16384  0 
joydev                 20480  0 
serio_raw              16384  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
video                  20480  1 i915
dw_dmac                16384  0 
dw_dmac_core           24576  1 dw_dmac
wmi                    20480  2 dell_led,dell_wmi
snd_soc_sst_acpi       16384  0 
mei_me                 20480  0 
drm_kms_helper        126976  1 i915
mei                    90112  1 mei_me
drm                   344064  4 i915,drm_kms_helper
snd                    90112  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
i2c_hid                20480  0 
8250_dw                16384  0 
soundcore              16384  2 snd,snd_hda_codec
spi_pxa2xx_platform    24576  0 
shpchp                 40960  0 
i2c_designware_platform    16384  0 
acpi_pad               20480  0 
i2c_algo_bit           16384  1 i915
i2c_designware_core    16384  1 i2c_designware_platform
lpc_ich                24576  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  4 i2c_hid,hid_generic,hid_rmi,usbhid
psmouse               118784  0 
r8169                  81920  0 
ahci                   36864  3 
libahci                32768  1 ahci
mii                    16384  1 r8169
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi

```

```

destiny@destiny:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"D-Link873640"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 48:EE:0C:2A:65:ED   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

```

```

destiny@destiny:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```

destiny@destiny:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 20:47:47:12:f0:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103677 (103.6 KB)  TX bytes:103677 (103.6 KB)

wlan0     Link encap:Ethernet  HWaddr ac:d1:b8:d0:04:f1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aed1:b8ff:fed0:4f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3680 errors:0 dropped:0 overruns:0 frame:4259
          TX packets:3064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2898481 (2.8 MB)  TX bytes:646514 (646.5 KB)
          Interrupt:18 

```
[/INDENT]

---

### Post by praseodym on 2015-08-16
Check if this works:
```

sudo iwconfig wlan0 power off
```
If you are on 14.04 install this package via double-click, it updates the driver

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

Reboot

---

### Post by bublz2 on 2015-08-17
> **praseodym said:**
> Check if this works:
```

sudo iwconfig wlan0 power off
```
If you are on 14.04 install this package via double-click, it updates the driver

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

Reboot

I'm on 15.04, should I install this package or not ?

---

### Post by praseodym on 2015-08-18
No, it is already the same driver. Tried that command? Also check if it works if you deactivate IPv6 in the network-manager profile

---

### Post by bublz2 on 2015-08-18
> **praseodym said:**
> No, it is already the same driver. Tried that command? Also check if it works if you deactivate IPv6 in the network-manager profile

I'll try the command on Saturday, I'm away from home until Saturday. I'll try it asap when I come home on Saturday

---

### Post by bublz2 on 2015-08-26
> **praseodym said:**
> No, it is already the same driver. Tried that command? Also check if it works if you deactivate IPv6 in the network-manager profile

Sorry, didn't get a chance to do it until now. The command didn't work :( I still have problems, I even tried the commands again instead of "off"  I replaced it with "on" still didn't work

---

