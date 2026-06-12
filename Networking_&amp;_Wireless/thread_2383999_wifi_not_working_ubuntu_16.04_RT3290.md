---
title: "wifi not working ubuntu 16.04 RT3290"
date: 2018-02-01
forum: Networking &amp; Wireless
---

### Post by coercion on 2018-02-01
I'm new to Ubuntu. I did try couple of solutions to install my wifi driver none of them worked out. please if you can help me step by step :D Thank you very much!

lspci
```
02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
             02:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
```

sudo lshw -C network

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eno1
       version: 07
       serial: d8:9d:67:cb:b3:96
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:25 ioport:3000(size=256) memory:c2404000-c2404fff memory:c2400000-c2403fff
  *-network
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 00
       serial: b8:76:3f:42:bc:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.4.0-112-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:c2510000-c251ffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:1.2
       logical name: enp0s26u1u2c4i2
       serial: be:9f:ef:dd:46:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.10 link=yes multicast=yes

```


lsmod

```
Module                  Size  Used by
cpuid                  16384  0
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
ipheth                 16384  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
intel_powerclamp       16384  0
coretemp               16384  0
uvcvideo               90112  0
snd_hda_intel          40960  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
videobuf2_vmalloc      16384  1 uvcvideo
kvm                   544768  0
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
snd_hwdep              16384  1 snd_hda_codec
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
snd_rawmidi            32768  1 snd_seq_midi
mei_me                 36864  0
crct10dif_pclmul       16384  0
mei                    98304  1 mei_me
crc32_pclmul           16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
ghash_clmulni_intel    16384  0
rtsx_pci_ms            20480  0
cryptd                 20480  1 ghash_clmulni_intel
joydev                 20480  0
memstick               20480  1 rtsx_pci_ms
input_leds             16384  0
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
mac_hid                16384  0
shpchp                 36864  0
lpc_ich                24576  0
hp_wireless            16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
i915                 1208320  3
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
psmouse               131072  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   364544  5 i915,drm_kms_helper
libahci                32768  1 ahci
r8169                  81920  0
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
fjes                   28672  0
video                  40960  1 i915


```

dmesg

```
[  354.993468] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[  355.001874] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[  355.027311] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  355.029621] rt2800pci 0000:02:00.0 wlo1: renamed from wlan0
[  355.059871] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  355.059946] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[  355.111593] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[  355.231828] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[  355.317398] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1071.159509] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1071.173001] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 1071.415672] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1074.834558] ipheth 1-1.2:4.2: ipheth_rcvbulk_callback: urb status: -71
[ 1074.847367] usb 1-1.2: USB disconnect, device number 3
[ 1074.879456] ipheth 1-1.2:4.2: Apple iPhone USB Ethernet now disconnected
[ 1195.279112] wlo1: authenticate with be:9f:ef:dd:46:c9
[ 1195.295017] wlo1: send auth to be:9f:ef:dd:46:c9 (try 1/3)
[ 1195.340345] wlo1: send auth to be:9f:ef:dd:46:c9 (try 2/3)
[ 1195.374619] wlo1: send auth to be:9f:ef:dd:46:c9 (try 3/3)
[ 1195.412888] wlo1: authentication with be:9f:ef:dd:46:c9 timed out
[ 1219.199703] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1257.105609] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready


```

---

### Post by jeremy31 on 2018-02-01
Please see the wireless script link in my signature and post results as you have a driver loaded for your wifi, rt2800pci

---

### Post by coercion on 2018-02-01
Thanks for response in such a short notice. I followed steps as I could. Results:

[https://pastebin.ca/3966586](https://pastebin.ca/3966586)

---

### Post by jeremy31 on 2018-02-01
That was the script itself, not the results, you could do
```
cat wireless-info.txt | nc termbin.com 9999
```
And post the URL

---

### Post by coercion on 2018-02-01
[http://termbin.com/58ze](http://termbin.com/58ze)
i hope this one is correct

---

### Post by praseodym on 2018-02-01
Try this driver

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp /firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot

---

### Post by coercion on 2018-02-01
When I open the laptop to try install driver wi-fi was working I thought we made it but couple of minutes later connection got lost. Then I start trying last solution at the last steps i had following error.
Thanks in advance!

```

selman@selman-PC:~/RT3290_u16$ sudo cp /firmware/rt3290.bin /lib/firmware 
cp: cannot stat '/firmware/rt3290.bin': No such file or directory



```

---

### Post by praseodym on 2018-02-01
Try
```

sudo cp firmware/rt3290.bin /lib/firmware/
```
without the first slash

---

### Post by coercion on 2018-02-01
unfortunately it is not working.

```

~$ ifconfig
eno1      Link encap:Ethernet  HWaddr d8:9d:67:cb:b3:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp0s26u1u2c4i2 Link encap:Ethernet  HWaddr be:9f:ef:dd:46:c9  
          inet addr:172.20.10.10  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::649:e18f:8180:24b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92957 (92.9 KB)  TX bytes:36046 (36.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:85465 (85.4 KB)  TX bytes:85465 (85.4 KB)



```

---

