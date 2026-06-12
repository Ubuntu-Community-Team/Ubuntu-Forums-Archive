---
title: "Wifi doesn't accept the correct password after the installation of Ubuntu 12.04"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by mukund-pant on 2015-11-23
Hi,

I'm having Belkin router to route the internet at my home.

My PC can detect the wifi properly, but not accepting the correct password any more.
Below are the details:

```
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ uname -a
Linux mukund-HP-Pavilion-dv6-Notebook-PC 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1448]
    Kernel driver in use: r8169
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 003: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 002 Device 004: ID 0bda:5801 Realtek Semiconductor Corp. 
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
#########################################################
hp@HP-Pavilion-dv6-Notebook-PC:~$ lsmod
Module                  Size  Used by
rfcomm                 47864  12 
bnep                   18258  2 
parport_pc             28284  0 
ppdev                  17113  0 
uvcvideo               82214  0 
snd_hda_codec_hdmi     37434  1 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
arc4                   12573  2 
iwldvm                249093  0 
mac80211              630977  1 iwldvm
snd_hda_codec_idt      71153  1 
snd_hda_intel          44339  5 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlwifi               183603  1 iwldvm
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
radeon                960918  3 
snd_timer              29989  2 snd_pcm,snd_seq
coretemp               13596  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              525244  3 iwldvm,mac80211,iwlwifi
kvm_intel             137899  0 
joydev                 17613  0 
kvm                   455932  1 kvm_intel
btusb                  22431  0 
snd                    69533  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             247024  24 rfcomm,bnep,btusb
soundcore              12680  1 snd
hp_accel               26012  0 
hp_wmi                 18092  0 
psmouse                97873  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  1 hp_wmi
ttm                    84051  1 radeon
wmi                    19256  1 hp_wmi
drm_kms_helper         49597  1 radeon
drm                   287564  5 radeon,ttm,drm_kms_helper
serio_raw              13215  0 
lis3lv02d              20200  1 hp_accel
input_polldev          13896  1 lis3lv02d
i7core_edac            24565  0 
i2c_algo_bit           13564  1 radeon
microcode              23017  0 
mei                    41820  0 
lpc_ich                17144  0 
video                  19652  0 
edac_core              62724  1 i7core_edac
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   25879  2 
libahci                31606  1 ahci
r8169                  68716  0 
#########################################################
```

---

