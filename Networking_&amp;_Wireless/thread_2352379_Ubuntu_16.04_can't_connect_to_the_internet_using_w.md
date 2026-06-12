---
title: "Ubuntu 16.04 can't connect to the internet using wireless or ethernet"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by jonathan90 on 2017-02-11
I just installed Ubuntu 16.04 on an old laptop and erased the Windows XP files, but now Ubuntu can't connect to the internet using wireless or ethernet. When I open the network icon, it shows "Enable Networking" but not "Enable Wireless." I'm suspecting that installing Ubuntu might have erased some drivers or software I needed. Any help is appreciated. Thanks!!!


Output for rfkill list:
```

```


(rfkill list didn't output anything)


Output for lspci:


```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
	Kernel modules: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl
```


Output for iwconfig:


```
lo        no wireless extensions.
```


Output for lsmod:


```
Module                  Size  Used by
nls_iso8859_1          16384  1
uas                    20480  0
usb_storage            57344  2 uas
hid_generic            16384  0
usbhid                 49152  0
hid                    98304  2 hid_generic,usbhid
ssb                    57344  1
mii                    16384  0
wl                   6152192  1
gpio_ich               16384  0
dell_laptop            24576  0
coretemp               16384  0
dcdbas                 16384  1 dell_laptop
kvm                   471040  0
dell_smm_hwmon         16384  0
snd_hda_codec_hdmi     49152  1
snd_hda_codec_idt      53248  1
snd_hda_codec_generic    69632  1 snd_hda_codec_idt
snd_hda_intel          36864  3
irqbypass              16384  1 kvm
snd_hda_codec         118784  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
cfg80211              499712  1 wl
snd_hda_core           61440  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
joydev                 20480  0
input_leds             16384  0
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0
r852                   20480  0
sm_common              20480  1 r852
nand                   69632  2 r852,sm_common
nand_ecc               16384  1 nand
nand_bch               16384  1 nand
bch                    20480  1 nand_bch
nand_ids               12288  1 nand
snd_pcm                94208  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
mtd                    57344  2 nand,sm_common
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
lpc_ich                20480  0
snd_rawmidi            28672  1 snd_seq_midi
r592                   20480  0
memstick               16384  1 r592
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    69632  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 32768  0
soundcore              16384  1 snd
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2
psmouse               118784  0
sdhci_pci              24576  0
firewire_ohci          36864  0
sdhci                  45056  1 sdhci_pci
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
pata_acpi              16384  0
i915                 1130496  4
i2c_algo_bit           16384  1 i915
drm_kms_helper        131072  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
video                  36864  2 i915,dell_laptop
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   311296  6 i915,drm_kms_helper
```


Output for sudo lshw -C network:


```
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:dfdfc000-dfdfffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64


       resources: memory:df9fe000-df9fffff
```


Output for iwlist scan:


```
lo        Interface doesn't support scanning
```


Output for cat /etc/lsb-release; uname -a:


```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
Linux inspiron-6400 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux

```


Output for lspci -nnk | grep -iA2 net:


```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
	Kernel modules: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl
```


Ouptut for lsusb:


```
Bus 001 Device 003: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by wildmanne39 on 2017-02-11
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and now wired connection should work.
Do:
```
sudo apt-get install firmware-b43-installer
```
You will need the wired connection to run the above command, watch for errors, when it is done reboot and wifi should work.

---

### Post by jonathan90 on 2017-02-12
It worked! Thank you so much!

---

### Post by wildmanne39 on 2017-02-12
Your welcome!
Enjoy!

---

