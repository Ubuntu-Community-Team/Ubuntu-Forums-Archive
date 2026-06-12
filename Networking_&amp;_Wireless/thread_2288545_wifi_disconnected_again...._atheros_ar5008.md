---
title: "wifi disconnected again.... atheros ar5008"
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by 300432280 on 2015-07-28
Two days ago I started computer and found the wifi disconnected. I couldn't even figure out a reason since I didn't do anything, I didn't update anything, I didn't change any settings, and it just all of sudden stopped working! I have tried almost all the method I can find, it just wont work! I tried changed additional driver, I tried remove and load ath9k again and again, and I tried removed wifi adapter and use another pci slot, It just wont work! I noticed the firmware is showing N/A, but I could figure out how to fix that, I cant download and install drivers, because I dont have Ethernet access, below is the termial output

```
tnt@TNT:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Qualcomm Atheros
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 01
       serial: 54:e6:fc:d1:bf:a0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.16.0-44-generic firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fb9e0000-fb9effff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:c5:59:da
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:ee00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
tnt@TNT:~$ lsmod 
Module                  Size  Used by
nls_iso8859_1          12713  1 
uas                    27255  0 
usb_storage            66545  2 uas
snd_hda_codec_hdmi     47548  4 
rfcomm                 69509  0 
bnep                   19624  2 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
arc4                   12608  2 
binfmt_misc            17468  1 
gpio_ich               13586  0 
snd_hda_codec_realtek    77514  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
snd_usb_audio         161790  2 
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_usbmidi_lib        29828  1 snd_usb_audio
snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_pcm               104112  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_rawmidi            30876  2 snd_usbmidi_lib,snd_seq_midi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143630  0 
kvm                   452047  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13483  0 
joydev                 17393  0 
ath9k                 141379  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
nouveau              [1206535]("tel:1206535")  3 
ath9k_common           25638  1 ath9k
snd_timer              29562  2 snd_pcm,snd_seq
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
mxm_wmi                13021  1 nouveau
snd                    79468  27 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
video                  20128  1 nouveau
tpm_infineon           17131  0 
ttm                    93588  1 nouveau
drm_kms_helper         61574  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
cfg80211              498458  4 ath,ath9k_common,ath9k,mac80211
drm                   311018  6 ttm,drm_kms_helper,nouveau
parport_pc             32741  0 
i2c_algo_bit           13413  1 nouveau
lpc_ich                21093  0 
soundcore              15047  2 snd,snd_hda_codec
mac_hid                13227  0 
ppdev                  17671  0 
mei_me                 19696  0 
mei                    87875  1 mei_me
lp                     17759  0 
shpchp                 37047  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
firewire_ohci          40551  0 
pata_acpi              13053  0 
r8169                  71694  0 
firewire_core          68769  1 firewire_ohci
ahci                   34142  4 
mii                    13934  1 r8169
crc_itu_t              12707  1 firewire_core
libahci                32424  1 ahci

```
can anybody help me please 
thanks!

---

### Post by 300432280 on 2015-07-29
I can't stand this naughty wifi anymore!!! :mad:I tried to ignore ipv6 and restart, It worked!! Then when I restart it again, it stopped working again!!!! I can't understand what's the cause of this peculiar behaver. can't find any effective solution on google, having a project due by August, can some please help!!

---

