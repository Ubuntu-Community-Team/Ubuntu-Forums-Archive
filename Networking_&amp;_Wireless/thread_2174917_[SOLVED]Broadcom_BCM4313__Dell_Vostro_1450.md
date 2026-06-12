---
title: "[SOLVED]Broadcom BCM4313 / Dell Vostro 1450"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by M_Zainal_Abidin on 2013-09-16
Hi,

I installing ubuntu 12.04 LTS. Suddenly when i reboot it said your wifi is offline. How to fix it? A few times i install it and got same error. Any work around for this laptop?

Thanks.

---

### Post by Hadaka on 2013-09-16
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list
```
thanks.

---

### Post by M_Zainal_Abidin on 2013-09-17
Will check after office.

---

### Post by M_Zainal_Abidin on 2013-09-17
```
root@Banie-Vostro:~# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
09:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
root@Banie-Vostro:~# 

```
```
root@Banie-Vostro:~# lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  12 
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_idt      71153  1 
joydev                 17613  0 
coretemp               13596  0 
snd_hda_intel          44339  3 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
kvm_intel             137899  0 
uvcvideo               82214  0 
i915                  620421  3 
kvm                   455932  1 kvm_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
btusb                  22431  0 
snd_timer              29989  2 snd_pcm,snd_seq
bluetooth             247024  24 bnep,rfcomm,btusb
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         49597  1 i915
videobuf2_memops       13202  1 videobuf2_vmalloc
ghash_clmulni_intel    13259  0 
cryptd                 20501  1 ghash_clmulni_intel
drm                   287564  4 i915,drm_kms_helper
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
psmouse                97873  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
i2c_algo_bit           13564  1 i915
dell_laptop            17425  0 
dcdbas                 14449  1 dell_laptop
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
microcode              23017  0 
wmi                    19256  1 dell_wmi
serio_raw              13215  0 
mei                    41820  0 
lpc_ich                17144  0 
video                  19652  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18256  0 
usb_storage            61749  1 ums_realtek
ahci                   25879  6 
libahci                31606  1 ahci
r8169                  68716  0 
root@Banie-Vostro:~# 

```
```
root@Banie-Vostro:~# lspci -nnk | grep -iA3 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:0506]
    Kernel driver in use: r8169
    Kernel modules: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel modules: bcma
root@Banie-Vostro:~# 

```
```
root@Banie-Vostro:~# rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@Banie-Vostro:~# 

```

---

### Post by Hadaka on 2013-09-17
Hi, give this a try..
```
sudo modprobe -r bcma
```
then do..
```
sudo modprobe -v brcmsmac
rfkill unblock all

```
thanks.

---

### Post by M_Zainal_Abidin on 2013-09-17
I issue command given by Hadaka. Can connect to wifi. But after i reboot laptop i can't connect wifi. So i need to issue command again. Is it i need to do each time i running my ubuntu. I'm using 64bit version 12.04 LTS.

---

### Post by Hadaka on 2013-09-17
Hi, please do.
```
sudo su
echo brcmsmac >> /etc/modules
exit 0

```
boot
It should now be permanent and load on boot
thanks.

---

### Post by M_Zainal_Abidin on 2013-09-18
Thanks dude. Working fine now.

---

### Post by Hadaka on 2013-09-18
awesome...please mark your thread solved..
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

