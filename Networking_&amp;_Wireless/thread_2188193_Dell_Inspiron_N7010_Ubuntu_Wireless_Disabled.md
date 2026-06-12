---
title: "Dell Inspiron N7010 Ubuntu Wireless Disabled"
date: 2013-11-15
forum: Networking &amp; Wireless
---

### Post by knc2 on 2013-11-15
So, as the Title, "Dell Inspiron N7010 Ubuntu Wireless Disabled" says, my computer's wireless is disabled. I am able to work with it through Ethanet but I want to go to my room! :P I guess the Ethanet cord would reach but... Yeah. Anyway. Please help?

I read up on some other posts but none seemed to help. If there is one you, the reader/poster knows of, please tell me.

Hmm... Does an Administrator have to approve a post from a new user or something? My first post of this doesn't show.
Edit: Nevermind! I just use too many characters in my tag.

---

### Post by praseodym on 2013-11-16
Please open a terminal with CTRL+ALT+T and show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by knc2 on 2013-11-16
kenton@kenton-Inspiron-N7010:~$ uname -a
Linux kenton-Inspiron-N7010 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
kenton@kenton-Inspiron-N7010:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0457]
    Kernel driver in use: atl1c
kenton@kenton-Inspiron-N7010:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. Card reader
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
kenton@kenton-Inspiron-N7010:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
joydev                 17613  0 
dm_crypt               23051  1 
pci_stub               12622  1 
vboxpci                23236  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               283008  3 vboxpci,vboxnetadp,vboxnetflt
coretemp               13596  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
uvcvideo               82214  0 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
dell_laptop            17425  0 
dcdbas                 14449  1 dell_laptop
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_realtek    79916  1 
lib80211_crypt_tkip    17390  0 
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
microcode              23017  0 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
wl                   3074618  0 
snd_seq_midi           13324  0 
psmouse                97873  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
intel_ips              18066  0 
serio_raw              13215  0 
lpc_ich                17144  0 
cfg80211              525326  1 wl
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
lib80211               14352  2 lib80211_crypt_tkip,wl
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
rfcomm                 47864  0 
bnep                   18258  2 
mei                    41820  0 
bluetooth             247165  10 rfcomm,bnep
parport_pc             28284  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech_dj        18767  0 
usbhid                 47346  1 hid_logitech_dj
hid                   105826  2 hid_logitech_dj,usbhid
ums_realtek            18256  0 
usb_storage            61749  2 ums_realtek
wmi                    19256  1 dell_wmi
ahci                   25879  2 
atl1c                  41977  0 
libahci                31606  1 ahci
i915                  620571  8 
drm_kms_helper         49597  1 i915
drm                   287564  4 i915,drm_kms_helper
i2c_algo_bit           13564  1 i915
video                  19652  1 i915
kenton@kenton-Inspiron-N7010:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

kenton@kenton-Inspiron-N7010:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
kenton@kenton-Inspiron-N7010:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search home
kenton@kenton-Inspiron-N7010:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
kenton@kenton-Inspiron-N7010:~$ cat /var/lib/NetworkManager/NetworkManager.state 

Sorry I didn't do this last night. :( I was so tired.

Edit: Let me clarify, it says I have wirless acess but nothing shows up.

---

### Post by praseodym on 2013-11-17
Install the missing firmware and uninstall the STA driver. After that, clean up the config:
```

sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot. Now the native driver should work

---

