---
title: "Cant connect to the internet via ethernet or wifi"
date: 2017-07-09
forum: Networking &amp; Wireless
---

### Post by wander799 on 2017-07-09
Hi there I recently installed Ubuntu Desktop 16.04.2 LTS on an old hp pavilion laptop, I'm a total noob on Ubuntu so please describe everything clearly for me.

The problem that I have is that I cant connect to the internet via both ethernet and wifi, wifi doesn't show up on the bar and when I connect an ethernet cable from my router to the laptop it is stuck on the connecting status and occasionally comes up with a you have been disconnected message. I have looked at many posts online but haven't been able to figure out what's going on. another weird thing is that the wifi switch on my laptop turns off and on the Bluetooth on the menu bar for some reason.

I think that it might be a driver issue or something like that but since I have no internet on the laptop I can't update the drivers, I do have another laptop that I can use but I've not figured out how to install stuff on Ubuntu yet like drivers, please respond and thanks in advance.

---

### Post by praseodym on 2017-07-09
Hi,

please open a terminal and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
rfkill list
lsmod
```

---

### Post by wander799 on 2017-07-09
Hi thanks for the quick reply here are all the results for the codes that you gave me.

**_lspci -nnk | grep -iA9 net_**


```
00:06.0 Ethernet controller [0200]: NVIDIA Corporation MCP65 Ethernet [10de:0450] (rev a3)
	Subsystem: Hewlett-Packard Company Pavilion dv9668eg Laptop [103c:30cf]
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
00:07.0 Audio device [0403]: NVIDIA Corporation MCP65 High Definition Audio [10de:044a] (rev a1)
	Subsystem: Hewlett-Packard Company Pavilion dv9668eg Laptop [103c:30cf]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:08.0 PCI bridge [0604]: NVIDIA Corporation MCP65 PCI bridge [10de:0449] (rev a1)
00:09.0 IDE interface [0101]: NVIDIA Corporation MCP65 IDE [10de:0448] (rev a1)
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Hewlett-Packard Company BCM4321 802.11a/b/g/n Wireless LAN Controller [103c:1367]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
05:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86M [GeForce 8400M GS] [10de:0427] (rev a1)
	Subsystem: Hewlett-Packard Company Pavilion dv9668eg Laptop [103c:30cf]
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
	Subsystem: Hewlett-Packard Company Pavilion dv9668eg Laptop [103c:30cf]
```

_**lsusb**_


```
Bus 001 Device 003: ID 064e:a110 Suyin Corp. HP Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**_rfkill_****_ list_**


```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

**_lsmod_**


```
Module                  Size  Used by
rfcomm                 77824  0
bnep                   20480  2
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    73728  1 snd_hda_codec_conexant
uvcvideo               90112  0
b43                   413696  0
videobuf2_vmalloc      16384  1 uvcvideo
snd_hda_intel          36864  3
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_hda_codec         135168  3 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec_generic
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_core           86016  4 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec,snd_hda_codec_generic
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
bcma                   61440  1 b43
snd_hwdep              16384  1 snd_hda_codec
mac80211              761856  1 b43
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
kvm                   598016  0
snd_pcm               110592  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
media                  40960  2 uvcvideo,videodev
btusb                  45056  0
snd_seq_midi_event     16384  1 snd_seq_midi
btrtl                  16384  1 btusb
irqbypass              16384  1 kvm
snd_rawmidi            32768  1 snd_seq_midi
btbcm                  16384  1 btusb
cfg80211              581632  2 b43,mac80211
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
btintel                16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
bluetooth             557056  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ssb_hcd                16384  0
joydev                 20480  0
snd_timer              32768  2 snd_seq,snd_pcm
r852                   20480  0
sm_common              16384  1 r852
input_leds             16384  0
snd                    86016  16 snd_hda_intel,snd_hwdep,snd_hda_codec_conexant,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_pcm
nand                   61440  2 r852,sm_common
soundcore              16384  1 snd
serio_raw              16384  0
nand_ecc               16384  1 nand
nand_bch               16384  1 nand
bch                    20480  1 nand_bch
r592                   20480  0
k8temp                 16384  0
nand_ids               16384  1 nand
mtd                    65536  3 nand_bch,sm_common,nand
memstick               20480  1 r592
shpchp                 36864  0
i2c_nforce2            16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
pata_acpi              16384  0
nouveau              1572864  3
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                   102400  1 nouveau
drm_kms_helper        167936  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               139264  0
drm                   368640  6 nouveau,ttm,drm_kms_helper
ssb                    65536  2 b43,ssb_hcd
ahci                   36864  2
firewire_ohci          40960  0
libahci                32768  1 ahci
pata_amd               20480  0
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
sdhci_pci              28672  0
sdhci                  45056  1 sdhci_pci
forcedeth              69632  0
wmi                    16384  3 mxm_wmi,nouveau,hp_wmi
fjes                   28672  0
video                  40960  1 nouveau
```

---

### Post by praseodym on 2017-07-09
For LAN:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
Remove all connection profiles for "cable" and "DSL" (if any) and reboot.
Does LAN work now?

---

### Post by wander799 on 2017-07-09
nope still doesn't work, just to make sure, do you mean delete old connections like wired connection 1 when you say the profiles?

---

### Post by praseodym on 2017-07-09
Yes, delete them. For wireless download this file and save it in your /home directory:

[https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Install it via
```

sudo tar ~/xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
and reboot

---

### Post by BenginM on 2017-07-09
Salutations!

lsmod shows the open source driver for the wireless card is b43 and it's loaded, i wounder what is the output of:

dmesg | grep b43

---

### Post by wander799 on 2017-07-09
> **praseodym said:**
> Yes, delete them. For wireless download this file and save it in your /home directory:

[https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Install it via
```

sudo tar ~/xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
and reboot

When I tyred to install the driver it came up with an error in the terminal]

```

tar: invalid option -- '/'
try 'tar --help' or 'tar --usage' for more information

```

---

### Post by wander799 on 2017-07-09
> **Sary.sa said:**
> Salutations!

lsmod shows the open source driver for the wireless card is b43 and it's loaded, i wounder what is the output of:

dmesg | grep b43

Hey I put that code in the terminal and here are the results

```

[   14.544201] b43-phy0: Broadcom 4321 WLAN found (core revision 12)
[   14.588040] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 2
[   14.588064] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2055, Revision 4, Version 0
[   14.725527] b43 ssb0:0: Direct firmware load for b43/ucode11.fw failed with error -2
[   14.725572] b43 ssb0:0: Direct firmware load for b43/ucode11.fw failed with error -2
[   14.725601] b43 ssb0:0: Direct firmware load for b43-open/ucode11.fw failed with error -2
[   14.725614] b43 ssb0:0: Direct firmware load for b43-open/ucode11.fw failed with error -2
[   14.725619] b43-phy0 ERROR: Firmware file "b43/ucode11.fw" not found
[   14.725625] b43-phy0 ERROR: Firmware file "b43-open/ucode11.fw" not found
[   14.725628] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

---

### Post by jeremy31 on 2017-07-09
Praseodym had a typo in the command
```
sudo tar -xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

Reboot

---

### Post by wander799 on 2017-07-09
thats me connected to the internet now via wifi thanks for the help guys, any tips on how i can fix ethernet too im guessing i can update through the internet some way

---

### Post by praseodym on 2017-07-09
True, sorry

---

