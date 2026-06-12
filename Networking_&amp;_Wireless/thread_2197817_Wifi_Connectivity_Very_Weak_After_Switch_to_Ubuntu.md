---
title: "Wifi Connectivity Very Weak After Switch to Ubuntu (13.10)"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by faultlessimperfect on 2014-01-05
I recently switched my HP Pavilion dm1 laptop from Windows to Ubuntu (13.10). Since making this switch, I have found that my wifi connectivity is much weaker than it was with Windows such that I can only connect to the internet if my laptop is right next to the wireless router. I have tried connecting while on both battery and plugged-in power and have the same problem either way (I've also checked and wifi power management is off which would indicate that is not the issue). I have also tried connecting via three different wifi networks (all of which worked fine when I ran the same laptop with Windows) and have had the same problem of needing to be right next to the wifi router to connect in all cases. Interestingly, once I do get a connection, it is generally strong, fast, and doesn't drop me at all so long as I stay next to the router.

I had previously run Ubuntu (7.04-11.04) for several years on another laptop and had found that I got better wifi connectivity with those releases than I did with the out-of-the-box Windows on that laptop. I'm really hoping that I can get that same great wifi connectivity with this laptop and newer Ubuntu release!

I would very much appreciate any tips on how to increase my wifi  sensitivity. It's going to be a real pain if the only place I can  connect to the internet is sitting the middle of the hallway in my  shared rental house! Thanks!!

---

### Post by praseodym on 2014-01-05
Hi,

please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
sudo iwlist scan
```
Router firmware is up-to-date?

---

### Post by faultlessimperfect on 2014-01-05
> **praseodym said:**
> please show the terminal outputs of these commands:

```

me@compname:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: bcma-pci-bridge
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
    Kernel driver in use: r8169

```
```

me@compname:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 004: ID 0a5c:21e3 Broadcom Corp. HP Portable Valentine
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:032b Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```

me@compname:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  12 
snd_hda_codec_idt      44605  1 
snd_hda_codec_hdmi     40373  1 
brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356429  0 
mac80211              517444  2 b43,brcmsmac
cfg80211              401762  3 b43,brcmsmac,mac80211
joydev                 17097  0 
ssb                    51596  1 b43
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
kvm                   368949  0 
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
radeon               1307313  4 
btusb                  23443  0 
uvcvideo               71309  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videobuf2_vmalloc      13048  1 uvcvideo
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
videobuf2_memops       13170  1 videobuf2_vmalloc
snd_seq_midi           13132  0 
psmouse                90642  0 
microcode              18830  0 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             323656  22 bnep,btusb,rfcomm
snd_rawmidi            25094  1 snd_seq_midi
ttm                    75982  1 radeon
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
drm_kms_helper         46867  1 radeon
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13189  0 
k10temp                12958  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   242400  6 ttm,drm_kms_helper,radeon
snd_timer              24447  2 snd_pcm,snd_seq
hp_accel               25756  0 
wmi                    18590  1 hp_wmi
bcma                   40966  3 b43,brcmsmac
lis3lv02d              19500  1 hp_accel
snd                    60790  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 radeon
sp5100_tco             13643  0 
lp                     13299  0 
mac_hid                13037  0 
parport                40795  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
i2c_piix4              17682  0 
input_polldev          13648  1 lis3lv02d
video                  18777  0 
ums_realtek            17733  0 
usb_storage            48294  1 ums_realtek
r8169                  61562  0 
mii                    13654  1 r8169
ahci                   25579  2 
libahci                26554  1 ahci

```
```

me@compname:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"PartyHouse"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:28:BF:5E   
          Bit Rate=26 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:1460   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


```
```

me@compname:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:1f:74:b8:1c:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:34030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3130559 (3.1 MB)  TX bytes:3130559 (3.1 MB)

wlan0     Link encap:Ethernet  HWaddr 60:d8:19:96:7d:7a  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62d8:19ff:fe96:7d7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2152065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1934473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1691994363 (1.6 GB)  TX bytes:362969472 (362.9 MB)


```
```

me@compname:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hsd1.wa.comcast.net

```
```

me@compname:~$ sudo iwlist scan
[sudo] password for me: 
wlan0     Scan completed :
          Cell 01 - Address: 58:6D:8F:28:BF:5E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"PartyHouse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e8f0ede524
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000A5061727479486F757365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B0001031047001090AE2BF5DBA167D33C671E86B97D165810210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 58:6D:8F:28:BF:5F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"PartyHouse-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e8f0edf1af
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00105061727479486F7573652D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

I hope this gives you the information you need. Thank you so much for your help! As to the router firmware being up to date, I believe so. The router is maintained by my landlord so I'm not in a position to make any changes to it. However, like I said before, this does not seem to be a router specific issue as I have tried to connect to wifi in three seperate locations via completely different wifi networks and have had the same issue of needing to be right next to the router in all cases.

Thanks again for your help!

---

### Post by praseodym on 2014-01-06
Install the firmware for Broadcom cards and blacklist the wrongly loaded driver:
```

sudo apt-get install linux-firmware-nonfree
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by faultlessimperfect on 2014-01-07
> **praseodym said:**
> Install the firmware for Broadcom cards and blacklist the wrongly loaded driver:


Hmm. That seems to have helped a little. I can now go several paces from the router and still have connection (though once I'm more than 4 or 5 paces from the router the speed of the connection becomes very slow - makes me feel a little like I'm back in the 90s where I could go get a coffee while the page loaded...). Unfortunately, it still drops me if I'm any further away than that or there's a wall between me and the router...

Thank you so much for your help thus far. Any other thoughts? I'm beginning to consider trying a USB wifi receiver off of the list of Ubuntu compatible wifi cards as an alternative to getting my internal card to work. Am I likely to have the same problem with a USB receiver or should that fix the problem??

Thanks!

---

### Post by praseodym on 2014-01-07
Change the encryption mode to pure WPA2-AES (CCMP) instead of mixed mode

---

### Post by faultlessimperfect on 2014-01-08
> **praseodym said:**
> Change the encryption mode to pure WPA2-AES (CCMP) instead of mixed mode

I'm afraid I'm not entirely clear on how to do that... I went into "Edit Connections" and found that the encryption is set as "WPA & WPA2 Personal" but could find no option that's any closer to what you wrote above or any drop downs in sub-menus that matched "AES" or "CCMP"... I've had Ubuntu long enough that I can generally follow basic instructions in Terminal, but beyond that I'm afraid I'm rather a noob... Thank you so much for helping me along with this.

---

### Post by praseodym on 2014-01-08
You need to enter the router interface for that. Check the manual for it.

---

### Post by faultlessimperfect on 2014-01-13
> **praseodym said:**
> You need to enter the router interface for that. Check the manual for it.

Since I can't muck around with the router (rental house and the landlord has the password) I did some extra searching based on the info from the commands you had me run (specifically that it's a BCM4313 wifi card). I found the thread below and replaced my bcma driver with the bcmwl one that had worked for the original poster there and it worked like a charm!
[http://ubuntuforums.org/showthread.php?t=2104178](http://ubuntuforums.org/showthread.php?t=2104178)

For the info of anyone reading this who has the same problem, the code I ran which fixed the problem was:
```

sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source

```

And that was it. Started working fine right after that and continued working fine after a reboot.

Thanks so much praseodym for all your help on this!

---

