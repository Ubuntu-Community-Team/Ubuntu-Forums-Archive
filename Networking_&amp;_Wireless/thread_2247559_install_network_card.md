---
title: "install network card"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by soufiane.android on 2014-10-08
how to install network cart on ubuntu

---

### Post by soufiane.android on 2014-10-08
when i want to use airmon i have this problem
```

Interface	Chipset		Driver


mon0		Unknown 	brcmsmac - [phy0]
mon1		Unknown 	brcmsmac - [phy0]
mon2		Unknown 	brcmsmac - [phy0]
wlan0		Unknown 	brcmsmac - [phy0]

```

---

### Post by QIII on 2014-10-08
We do not allow discussions regarding airmon-ng, aircrack-ng or similar tools on the forums.

Closed.

---

### Post by soufiane.android on 2014-10-08
i have problem in my wireless card  

```

Interface	Chipset		Driver


wlan0		Unknown 	brcmsmac - [phy0]

```

---

### Post by soufiane.android on 2014-10-08
[COLOR=#000000]i have problem in my wireless card => unknown 

```

[/COLOR]Interface	Chipset		Driver


wlan0		Unknown 	brcmsmac - [phy0]
[COLOR=#000000]
```
[/COLOR]

---

### Post by sammiev on 2014-10-08
Have you tried 

```
sudo lshw
```

or

```
lshw
```

should give you your full specs for your computer.

---

### Post by oldfred on 2014-10-09
Merged several threads.

Please do not create duplicate threads on the same issue. We all are volunteers and do not want to duplicate effort that others have already provided.

---

### Post by varunendra on 2014-10-09
To get and show us the details of your wireless setup, please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

By the way, we can only assist with getting your wireless working. Nothing further about your 'airmon' thing, not allowed here as QIII had mentioned.

---

### Post by soufiane.android on 2014-10-09
please can u help me
 [COLOR=#000000]i have problem in my wireless card => unknown 

```

[/COLOR]Interface	Chipset		Driver


wlan0		Unknown 	brcmsmac - [phy0]
[COLOR=#000000]
```

[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by kc1di on 2014-10-09
can you tells what card it is.
```
lspci
```
also post 
```
lsmod
```

---

### Post by soufiane.android on 2014-10-09
lspci =>
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```

lsmod =>

```

Module                  Size  Used by
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46368  1 
uvcvideo               80885  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  7 
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
kvm                   451511  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
radeon               1522474  4 
snd_timer              29482  2 snd_pcm,snd_seq
joydev                 17381  0 
serio_raw              13462  0 
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
edac_core              62291  0 
sp5100_tco             13979  0 
k10temp                13126  0 
edac_mce_amd           22617  0 
snd                    69322  24 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_piix4              22155  0 
drm                   303102  6 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
wmi                    19177  1 hp_wmi
parport_pc             32701  0 
video                  19476  0 
ppdev                  17671  0 
arc4                   12608  2 
brcmsmac              563041  0 
mac_hid                13205  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
shpchp                 37032  0 
bcma                   52096  2 brcmsmac
mac80211              630653  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
ahci                   25819  2 
libahci                32716  1 ahci
r8169                  67581  0 
mii                    13934  1 r8169

```

---

### Post by slickymaster on 2014-10-09
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by oldfred on 2014-10-09
Merged another thread.

---

### Post by kc1di on 2014-10-09
Hi again,
You have a broadcom 4313 wireless card and you have a brcmsmac,mac80211 driver loaded which will not work with that card.
I'm assuming your using Unity as your desktop.  so Go to software center then click on Edit, then Software Sources then Additional Driver tab. 
it takes a minute to find the card and should offer you the correct driver to install, Install that driver.  then reboot.  Wireless should then be working. 
(Note: you will have to be connected online via Lan to download the driver. 
good Luck !

---

### Post by soufiane.android on 2014-10-09
same problem 

```

Interface	Chipset		Driver


wlan0		Unknown 	brcmsmac - [phy0]

```

---

### Post by Vladlenin5000 on 2014-10-09
Same problem after doing what exactly?

---

### Post by soufiane.android on 2014-10-09
[IMG]https://lh6.googleusercontent.com/-w5tOKpKkcXE/VDcSn-ZeZdI/AAAAAAAAGHI/2A-8OZpUNeI/w978-h550-no/Screenshot%2Bfrom%2B2014-10-09%2B23%3A52%3A15.png[/IMG]

i install this driver

---

### Post by Vladlenin5000 on 2014-10-09
So apparently it's connected to a WiFi network. Doesn't it work?

Obs.: If not supported by a certain app perhaps you should contact their forum and/or other specialized forums. It happens that specific app (and what it meant to) isn't supported here as someone already told you.

---

### Post by kc1di on 2014-10-10
if you have not already done so run the wireless script found [here]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222") and post the results.

---

