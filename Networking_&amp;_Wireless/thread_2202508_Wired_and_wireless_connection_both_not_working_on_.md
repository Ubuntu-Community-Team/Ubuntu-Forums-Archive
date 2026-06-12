---
title: "Wired and wireless connection both not working on elementaryOS"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by ashlee2 on 2014-01-29
Just switched to eOS from 13.04 just because I wanted to try it out. Wireless doesn't work, which is a common problem with eOS but I can't get a wired connection to work either. It works on my other computers but when I plug the Ethernet cable into my laptop it will say "Connecting" for a while and then say it's disconnected. I probably just need to install some drivers and update to ge my wireless to work but I can't do that without a wired connection.

---

### Post by praseodym on 2014-01-29
Hi,

please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by ashlee2 on 2014-01-29
```
ashlee@ashlee-Inspiron-1545:~$ lspci -nnk | grep -iA2 net09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
	Subsystem: Dell Device [1028:02aa]
	Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge
ashlee@ashlee-Inspiron-1545:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 014: ID 05ac:12a8 Apple, Inc. 
ashlee@ashlee-Inspiron-1545:~$ lsmod
Module                  Size  Used by
ipheth                 13526  0 
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
b43                   365983  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                97485  0 
mac80211              506862  1 b43
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205774  2 b43,mac80211
dell_wmi               12681  0 
dell_laptop            18119  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sparse_keymap          13890  1 dell_wmi
mac_hid                13253  0 
dcdbas                 14490  1 dell_laptop
bcma                   26696  1 b43
sky2                   59043  0 
i915                  478239  3 
wmi                    19256  1 dell_wmi
ssb                    52752  1 b43
ums_realtek            18248  0 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
usb_storage            49198  1 ums_realtek
ashlee@ashlee-Inspiron-1545:~$ iwconfig
lo        no wireless extensions.


eth1      no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


ashlee@ashlee-Inspiron-1545:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:40:bc:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:314932 (314.9 KB)  TX bytes:114659 (114.6 KB)
          Interrupt:18 


eth1      Link encap:Ethernet  HWaddr 22:7d:74:23:eb:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:236912 (236.9 KB)  TX bytes:236912 (236.9 KB)


wlan0     Link encap:Ethernet  HWaddr 00:22:5f:b2:32:3f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ashlee@ashlee-Inspiron-1545:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
ashlee@ashlee-Inspiron-1545:~$ 
```

---

### Post by ashlee2 on 2014-01-29
Installed the Linux driver by Marvell to try and fix wired connection, didn't help.

---

### Post by praseodym on 2014-01-29
Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation:
```

cd ~/Downloads/
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo service network-manager stop
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Maybe you need nameservers for both LAN and WLAN:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart 
```

---

### Post by spitter on 2014-04-05
This works for me, Inspiron 1545, LinuxMint16, I had no wired and no wireless connection. I downloaded the file on my mac mini, copied and paste it on my Dell inspiron. Many thanks.
Location: Oosterhout, the Netherlands

---

