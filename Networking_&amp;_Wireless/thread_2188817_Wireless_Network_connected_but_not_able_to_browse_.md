---
title: "Wireless Network connected but not able to browse Internet in Ubuntu 12.04"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by bte_rajan on 2013-11-19
I have problem browsing internet, 


my wireless detects networks and I am able to  connect to one of the network. but still I am unable to browse internet.
what should I do please help??

---

### Post by praseodym on 2013-11-19
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

What kind of computer is it?

---

### Post by bte_rajan on 2013-11-20
uname -a
Linux rajan-Inspiron-3521 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 09:20:45 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]
    Kernel driver in use: ath9k

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:64ad Microdia 
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90


lsmod
Module                  Size  Used by
usbhid                 47238  0 
hid                    99636  1 usbhid
btusb                  18332  2 
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32193  1 
snd_hda_codec_realtek    73693  1 
arc4                   12529  2 
joydev                 17693  0 
ath9k                 150027  0 
mac80211              605725  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              413382  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              528435  3 ath9k,mac80211,ath
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33327  3 
snd_hda_codec         134156  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
compat                 25790  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rts5139               351188  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
i915                  478326  3 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
drm_kms_helper         46978  1 i915
v4l2_compat_ioctl32    17128  1 videodev
ath3k                  12910  0 
bluetooth             180113  24 btusb,rfcomm,bnep,ath3k
drm                   241971  4 i915,drm_kms_helper
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 dell_wmi
snd_timer              29990  2 snd_pcm,snd_seq
mac_hid                13253  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97519  0 
serio_raw              13211  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62190  0


iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:E7:0E:DA:4D   
          Bit Rate=12 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:51  Invalid misc:46   Missed beacon:0

eth0      no wireless extensions.


rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by bte_rajan on 2013-11-20
Wired Network connection works perfectly in my system.

---

### Post by praseodym on 2013-11-20
Deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Check:
```

cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
```

---

### Post by bte_rajan on 2013-11-21
Here is the terminal output


echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1

sudo modprobe -v ath9k

sudo modprobe -rfv ath9krmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/ath9k.ko
rmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/mac80211.ko
rmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/ath9k_common.ko
rmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/ath9k_hw.ko
rmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/ath.ko
rmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/cfg80211.ko
rmmod /lib/modules/3.2.0-56-generic/updates/cw-3.8/compat.ko

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

iwlist chan
lo        no frequency information.

eth0      no frequency information.

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2013-11-21
You need nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by bte_rajan on 2013-11-22
I tried doing that but still unable to browse internet

---

### Post by praseodym on 2013-11-22
Check the router settings:
[LIST]
[*]
[*]WPA2-AES encryption
[*]no MAC address filter enabled
[*]bandwidth 20MHz instead of 20/40MHz
[*]fixed channel, e.g. "1"
[/LIST]

---

