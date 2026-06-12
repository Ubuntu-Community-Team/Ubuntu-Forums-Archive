---
title: "Install wifi modem buffalo airstation g54"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by Soonick on 2014-07-19
I borrowed a [wifi modem from a friend - buffalo airstation g54]("http://en.wikipedia.org/wiki/Buffalo_AirStation")
[IMG]http://upload.wikimedia.org/wikipedia/commons/d/de/Buffalo_AirStation_WBR-G54.jpg[/IMG]
I don't know anything about the installation, I just would like to use the wifi. I don't have an installation cd. I have found some guides on the web, but all of them are for windows machines. I am on Linux - Ubuntu. Could you please guide me on this? What kind of information do you/I need?

---

### Post by praseodym on 2014-07-19
Hi,

check if there is a sticker/label with the "ESSID" and the password of the network on the modem. Open the network-manager applet and setup the wifi accordingly. Open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
route -n
iwlist chan
sudo iwlist scan
rfkill list
cat /etc/resolv.conf
```Can you connect via cable?

---

### Post by Soonick on 2014-07-20
Hi! Many thanks for your reply.

One problem I forgot to mention in the first post, is that... there are some labels on the modem but they are in Japanese (since I am in Japan right now).
I think I understood which one is the password (in western alphabet, btw), but I don't know about the "ESSID".
I tried to connect via cable but I can't neither.

here is the result from the terminal:
```
nedu@nedu:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
    Kernel driver in use: wl
--
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0212]
    Kernel driver in use: atl1c
nedu@nedu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
nedu@nedu:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
snd_hda_codec_realtek   224215  1 
lib80211_crypt_tkip    17390  0 
joydev                 17693  0 
snd_hda_intel          33719  5 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
wl                   3074895  0 
snd_pcm                97275  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 47604  4 
uvcvideo               72627  0 
soundcore              15091  1 snd
videodev               98259  1 uvcvideo
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
parport_pc             32866  0 
psmouse                98051  0 
binfmt_misc            17540  1 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17128  1 videodev
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
cfg80211              205774  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
ppdev                  17113  0 
mac_hid                13253  0 
dm_multipath           23275  0 
serio_raw              13211  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
mxm_wmi                13021  0 
atl1c                  41718  0 
i915                  478689  3 
usbhid                 47238  0 
hid                    99883  1 usbhid
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
wmi                    19256  2 acer_wmi,mxm_wmi
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
nedu@nedu:~$ ifconfig -a
eth0      Link encap:Ethernet  IndirizzoHW 70:5a:b6:3d:3f:bf  
          indirizzo inet:192.168.1.19  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::725a:b6ff:fe3d:3fbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21298 errors:0 dropped:0 overruns:0 carrier:2
          collisioni:0 txqueuelen:1000 
          Byte RX:42073159 (42.0 MB)  Byte TX:1916554 (1.9 MB)
          Interrupt:46 

eth1      Link encap:Ethernet  IndirizzoHW f0:7b:cb:10:42:e2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:480 (480.0 B)  Byte TX:480 (480.0 B)

nedu@nedu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

nedu@nedu:~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
nedu@nedu:~$ iwlist chan
lo        no frequency information.

eth1      26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
eth0      no frequency information.

nedu@nedu:~$ sudo iwlist scan
[sudo] password for nedu: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

nedu@nedu:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
nedu@nedu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 210.150.255.66
nameserver 203.138.71.154
nedu@nedu:~$ 


```

of which, of course, I don't understand anything :lolflag:

---

### Post by praseodym on 2014-07-20
Uninstall the "wrong" Broadcom driver:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Download this file and save it in "Downloads":
[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)
Installation via:
```
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by Soonick on 2014-07-20
You are super helpful!
Just before I proceed (since I don't really know what I am doing): is it not that with those coomands I won't be able to connect internet anymore? (before to install the new one, or so...)

---

### Post by praseodym on 2014-07-20
No, for this device the native driver works better, but it lacks the proprietary firmware.

---

### Post by Soonick on 2014-07-20
Ok, I am trying right now.
Is it normal that, after removing the DKMS Modules, the next commands result in:
```
nedu@nedu:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: impossibile rimuovere "/etc/modprobe.d/blacklist-bcm43.conf": File o directory non esistente
nedu@nedu:~$ sudo rm /etc/modprobe.d/broadcom-sta-common.conf
rm: impossibile rimuovere "/etc/modprobe.d/broadcom-sta-common.conf": File o directory non esistente
nedu@nedu:~$ sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
rm: impossibile rimuovere "/etc/modprobe.d/broadcom-sta-dkms.conf": File o directory non esistente
nedu@nedu:~$ sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sed: nessun file in ingresso
nedu@nedu:~$ sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sed: nessun file in ingresso
nedu@nedu:~$ sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sed: nessun file in ingresso
nedu@nedu:~$ sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*)
sed: nessun file in ingresso
```

?

EDI: sorry, it is italian XD 
"impossibile rimuovere" = impossible to remove
"File o directory non esistente" = file or directory not existing
"nessun file in ingresso" = no files in input

Update:
I have followed the procedure, but still can't connect either via wifi or via cable.
When I try the wifi, it doesn't ask the password anymore (it just asked the first time, so maybe now it is saved).
Btw, to connect via cable should not I "configure" the connection as well? Like give it a name, and other parameters...

---

### Post by praseodym on 2014-07-20
Remove all networks (cable, wireless, DSL, if any) and reboot. Try again to connect and show:
```

sudo iwlist scan
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
lsmod
ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.11 
dmesg | egrep 'wlan|error|brcm'
```

---

### Post by Soonick on 2014-07-20
Thanks again. What do you mean: "remove all networks"? what should I do?

If I disable the networs, and reboot, this is what the terminal returns:
```
nedu@nedu:~$ sudo iwlist scan
[sudo] password for nedu: 
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

nedu@nedu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

nedu@nedu:~$ ifconfig -a
eth0      Link encap:Ethernet  IndirizzoHW 70:5a:b6:3d:3f:bf  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:1792 (1.7 KB)  Byte TX:1792 (1.7 KB)

wlan0     Link encap:Ethernet  IndirizzoHW f0:7b:cb:10:42:e2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

nedu@nedu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nedu@nedu:~$ route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
nedu@nedu:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
snd_hda_codec_realtek   224215  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29990  2 snd_pcm,snd_seq
rfcomm                 47604  4 
b43                   365983  0 
bnep                   18281  2 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506862  1 b43
parport_pc             32866  0 
snd                    79041  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acer_wmi               28418  0 
binfmt_misc            17540  1 
sparse_keymap          13890  1 acer_wmi
bluetooth             180113  10 rfcomm,bnep
uvcvideo               72627  0 
cfg80211              205774  2 b43,mac80211
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
bcma                   26696  1 b43
psmouse                98051  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
dm_multipath           23275  0 
ppdev                  17113  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
mxm_wmi                13021  0 
i915                  478689  3 
usbhid                 47238  0 
hid                    99883  1 usbhid
wmi                    19256  2 acer_wmi,mxm_wmi
drm_kms_helper         46978  1 i915
atl1c                  41718  0 
ssb                    52752  1 b43
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
nedu@nedu:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
Usage: ping [-LRUbdfnqrvVaAD] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface]
            [-M pmtudisc-hint] [-m mark] [-S sndbuf]
            [-T tstamp-options] [-Q tos] [hop1 ...] destination
nedu@nedu:~$ ping -c 2 www.ubuntuusers.de
ping: unknown host www.ubuntuusers.de
nedu@nedu:~$ ping -c 2 213.95.41.11 
connect: Network is unreachable
nedu@nedu:~$ dmesg | egrep 'wlan|error|brcm'
```

---

### Post by praseodym on 2014-07-21
You need nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Soonick on 2014-07-22
Hi! It seems to work properly!
But it does not ask for a password, so the network is free...
Ho can I set a password, please?

---

### Post by praseodym on 2014-07-22
Add the IP address **192.168.1.1** into your browser and enter the router interface (manual?). Change the encryption from "none" to WPA2-AES (CCMP), if possible.

---

### Post by Soonick on 2014-07-26
Hi! the address is not found, the page is not load.
If I understood properly, I just have to use that IP as address in the browser, right?

---

### Post by praseodym on 2014-07-27
Right, please check

```
route -n
arp -v
```

---

### Post by Soonick on 2014-07-27
Ok, here is the output:
```
nedu@nedu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
nedu@nedu:~$ arp -v
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:60:b9:e3:04:e4   C                     wlan0
Entries: 1    Skipped: 0    Found: 1
nedu@nedu:~$
```

---

### Post by praseodym on 2014-07-27
Can you connect via cable? Any manual for that modem, how to enter the interface?

---

### Post by Soonick on 2014-09-17
Yes I can connect via cable, but I dont have any manual: it is a device borrowed by a friend here in Japan.

---

### Post by praseodym on 2014-09-17
[http://www.danets.com/download/WHR-HP-G54-Manual.pdf](http://www.danets.com/download/WHR-HP-G54-Manual.pdf)

This one?

---

### Post by Soonick on 2014-09-20
Hi! Thanks again. Yes, I think this manual could be fine, but I just don't know how to proceed. On pag. 9 it says to enter the proper IP address (192.168.11.1) on the browser, but the page is not loaded. I tried with many different addresses googling a bit, but none of them works. Is there not a proper and unambiguous way to know this IP? What about if it has been changed?

---

### Post by praseodym on 2014-09-21
Sure, its "11" instead of "1"?

---

### Post by Soonick on 2014-09-21
I tried both of course.

---

### Post by praseodym on 2014-09-21
Can you connect via cable and try it again?

---

### Post by Soonick on 2014-09-22
Yes, sorry, I meant that I tried connected by cable.

---

