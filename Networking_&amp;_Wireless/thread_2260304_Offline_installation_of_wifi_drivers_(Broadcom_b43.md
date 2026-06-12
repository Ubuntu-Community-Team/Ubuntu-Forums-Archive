---
title: "Offline installation of wifi drivers (Broadcom b43b1) in Ubuntu 14.04.1 ?"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by hsk2 on 2015-01-10
I have a PC with an ASUS Z97i-PLUS motherboard and I managed to figure out that the wireless chipset is a Broadcom b43b1. Unfortunately however, there seems to be no official driver support for it under Ubuntu according to [http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom](http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom) and I'm therefore researching alternative ways of getting it to work. I don't have a PCE-AC66 though, I use the 2T2R antenna which came with the motherboard if it makes any difference.

My router is far away from my PC and disconnecting and moving everything isn't possible right now which is why I need to figure out how I can install the drivers without any form of internet access. I've been searching for quite a while and ended up finding a guide here: [http://forum.osxlatitude.com/index.php?/topic/6339-ubuntudebian-14e443b1-broadcom-corporation-device-43b1-rev-03/](http://forum.osxlatitude.com/index.php?/topic/6339-ubuntudebian-14e443b1-broadcom-corporation-device-43b1-rev-03/)

How would one go about to install the driver from a USB drive for instance? I'm a casual user so I'm not very experienced with Linux/Ubuntu and I would really appreciate it if you could help me with a simple step-by-step guide on how to get my wifi up and running. If you need any additional information just ask and I'll try to supply it ASAP.

---

### Post by praseodym on 2015-01-11
Please show the teminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by jramshu2 on 2015-01-11
I had to use the ndiswrapper to get mine going. I didn't have lan to connect to so I put it on a usb along with a generic driver and installed it that way.

But yeah, need to run what praseodym posted.

---

### Post by TACD on 2015-07-30
I'm having the same problem as the OP, using the same motherboard.

> **praseodym said:**
> Please show the teminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

uname -a:
```
Linux Onyx 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

lspci -nnk | grep -iA2 net:
```

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:855c]
```

lsmod:```

Module                  Size  Used by
ipheth                 13462  0 
xt_multiport           12798  2 
iptable_filter         12810  1 
ip_tables              27240  1 iptable_filter
x_tables               34059  3 ip_tables,xt_multiport,iptable_filter
joydev                 17393  0 
hid_logitech_dj        18469  0 
btusb                  32497  0 
usbhid                 52616  0 
hid                   110426  4 usbhid,hid_logitech_dj
rfcomm                 69509  8 
bnep                   19624  2 
bluetooth             446409  22 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
nvidia              11070238  40 
eeepc_wmi              13151  0 
asus_wmi               24094  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm                   452047  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
nouveau              1206535  0 
aesni_intel           152552  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13483  0 
mxm_wmi                13021  1 nouveau
ttm                    93588  1 nouveau
snd_hda_codec_realtek    77514  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
tpm_infineon           17131  0 
drm_kms_helper         61574  1 nouveau
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
drm                   311018  6 ttm,drm_kms_helper,nvidia,nouveau
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
video                  20128  2 nouveau,asus_wmi
snd_hwdep              17698  1 snd_hda_codec
acpi_pad               17942  0 
mac_hid                13227  0 
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
i2c_algo_bit           13413  1 nouveau
snd_seq_midi           13564  0 
wmi                    19193  3 mxm_wmi,nouveau,asus_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
mei_me                 19696  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    87875  1 mei_me
soundcore              15047  2 snd,snd_hda_codec
shpchp                 37047  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
e1000e                226396  0 
psmouse               106722  0 
ahci                   34142  3 
ptp                    19395  1 e1000e
libahci                32424  1 ahci
pps_core               19382  1 ptp
```

iwconfig:
```
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.
```

rfkill list:
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Any help would be much appreciated!

---

### Post by chili555 on 2015-07-30
Please see my answer here: [http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r](http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r)> Just wanted to confirm that I have a Lenovo y50-70 using Broadcom BCM4352, 14e4:43b1 (rev 03) and this driver worked. Thanks!

---

### Post by TACD on 2015-08-18
> **chili555 said:**
> Please see my answer here: [http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r](http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r)
This worked perfectly! Thank you very much.

---

