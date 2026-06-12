---
title: "No wireless access on Ubuntu 16.04 [Laptop: HP Pavilion G6]"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by kaushikangara on 2016-09-16
Hello users and admins,

I am unable to access Wifi on my Ubuntu. I am able to connect via ethernet. I have tried a no of solutions suggested but in vain. Please help me out. 

Following is the output of lshw -class network

kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ ```
lshw -class network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: rename3
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:52510000-5251ffff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 05
       serial: 38:ea:a7:d9:f5:b1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:26 ioport:3000(size=256) memory:52404000-52404fff memory:52400000-52403fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ 
```


My wireless support is via Railink 3290.

Any help would be appreciated.

---

### Post by wildmanne39 on 2016-09-16
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```

---

### Post by wildmanne39 on 2016-09-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by kaushikangara on 2016-09-16
kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ cat /etc/lsb-release; uname -a

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux kaushik-HP-Pavilion-g6-Notebook-PC 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ lspci -nnk | grep -iA2 net

```

01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink RT3290LE  802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Ad
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:183f]
    Kernel driver in use: r8169
    Kernel modules: r8169


```
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ lsusb

```

Bus 002 Device 003: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ iwconfig

```

lo        no wireless extensions.

eno1      no wireless extensions.

rename3   Ralink STA  

```
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ rfkill list all


NO OUTPUT FOR THIS COMMAND

--------------------------------------------------------------------------------------------------------------------------------------------------------
kaushik@kaushik-HP-Pavilion-g6-Notebook-PC:~$ lsmod

```

Module                  Size  Used by
cpuid                  16384  0
wl                   6365184  0
bnep                   20480  2
cfg80211              565248  1 wl
bluetooth             520192  7 bnep
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec_hdmi     53248  1
kvm_intel             172032  0
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
snd_hda_intel          36864  3
kvm                   540672  1 kvm_intel
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
irqbypass              16384  1 kvm
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
uvcvideo               90112  0
snd_timer              32768  2 snd_pcm,snd_seq
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
mei_me                 36864  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
mei                    98304  1 mei_me
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
aesni_intel           167936  0
snd                    81920  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
media                  24576  2 uvcvideo,videodev
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
input_leds             16384  0
glue_helper            16384  1 aesni_intel
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
joydev                 20480  0
serio_raw              16384  0
shpchp                 36864  0
lpc_ich                24576  0
hp_accel               28672  0
hp_wireless            16384  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
mac_hid                16384  0
rt3290sta            1155072  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0
i915                 1208320  5
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
psmouse               126976  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
r8169                  81920  0
drm                   364544  7 i915,drm_kms_helper
libahci                32768  1 ahci
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
fjes                   28672  0
video                  40960  1 i915


```

---

### Post by wildmanne39 on 2016-09-16
Please do:
```
sudo modprobe -rfv wl
```
That command unloads the wrong driver.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
This command removes it off your system permanently.
```
sudo modprobe -v rt2800pci
```
This command loads the correct driver.
Wifi should come on.

---

### Post by Contsa on 2016-10-17
I had a very similar issue with a Pavilion G6 and noticed. The wifi on xenial would not come up after a reboot, but it would work fine after a full manual power-off and power-on cycle. Hope this helps.

---

