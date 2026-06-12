---
title: "wireless connected but with no internet [Ubuntu 14.04]"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by Faysal_MISSI on 2015-05-08
hello guys i'm new
i have the problem that everybody has it, it's the problem of connection (sorry for my eng)
to be honest i've tried every solution in this forum
i have installed this :
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
and i have alpha (LINE FOX) with driver rtl8187L 
but the same problem 
but i have shared phone connection with cable and it's work plz guys help me
> 
lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:0585]
    Kernel driver in use: r8169


> 
lsusb

Bus 002 Device 004: ID 125f:cb20 A-DATA Technology Co., Ltd. 
Bus 002 Device 006: ID 0fce:7171 Sony Ericsson Mobile Communications AB 
Bus 002 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 15d9:0a41 Trust International B.V. MI-2540D [Optical mouse]
Bus 001 Device 003: ID 1a2c:0c23 China Resource Semico Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> 
lsmod

Module                  Size  Used by
rndis_host             14513  0 
cdc_ether              14361  1 rndis_host
usbnet                 43913  2 rndis_host,cdc_ether
nls_iso8859_1          12713  1 
ctr                    13049  1 
ccm                    17773  1 
rfcomm                 69509  0 
bnep                   19624  2 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
arc4                   12608  2 
rtl8187                64924  0 
mac80211              652718  1 rtl8187
joydev                 17393  0 
cfg80211              494330  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_conexant    23064  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_conexant
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
intel_rapl             18783  0 
snd_hda_codec         139682  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
snd_hwdep              17698  1 snd_hda_codec
coretemp               13441  0 
kvm_intel             143590  0 
dcdbas                 14928  0 
kvm                   452043  1 kvm_intel
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
cryptd                 20359  1 ghash_clmulni_intel
serio_raw              13483  0 
lpc_ich                21093  0 
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
i915                  905798  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
video                  20128  1 i915
snd_timer              29562  2 snd_pcm,snd_seq
drm_kms_helper         61574  1 i915
shpchp                 37047  0 
snd                    79468  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   311018  5 i915,drm_kms_helper
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
mei                    87875  1 mei_me
i2c_algo_bit           13413  1 i915
parport_pc             32741  0 
mac_hid                13227  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
uas                    23159  0 
usb_storage            66545  2 uas
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
psmouse               106561  0 
r8169                  71694  0 
ahci                   34062  4 
libahci                32424  1 ahci
mii                    13934  2 r8169,usbnet


> 
iwconfig

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TNCAP2C7258"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 18:17:25:2C:72:58   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:16  Invalid misc:12   Missed beacon:0

usb0      no wireless extensions.

lo        no wireless extensions.


> 
rfkill list

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


---

