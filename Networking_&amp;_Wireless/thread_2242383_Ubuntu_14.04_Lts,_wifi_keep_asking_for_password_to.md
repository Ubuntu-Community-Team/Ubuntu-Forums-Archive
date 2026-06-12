---
title: "Ubuntu 14.04 Lts, wifi keep asking for password to network"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by Isak_Falk on 2014-09-01
Hello, I just upgraded to 14.04 lts.

When I try to connect to my network, the network manager asks for my password, which I insert. After this it loads like it is waiting to connect, but after a while it asks for my password again. It seems like this have been up before, but I couldn't find a clear answer to the solution.

My computer is a Lenovo Z580. Is there some kind of log that I can post to help others, more knowledgeable, to solve my problem?

Thanks!

---

### Post by praseodym on 2014-09-01
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
```
Does LAN work?

---

### Post by Isak_Falk on 2014-09-01
Yeah, I can connect through an ethernet cable.

Terminal Output:
```

isak@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0587]
    Kernel driver in use: wl
isak@ubuntu:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0489:e032 Foxconn / Hon Hai 
Bus 003 Device 002: ID 5986:0295 Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
isak@ubuntu:~$ lsmod
Module                  Size  Used by
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
lib80211_crypt_tkip    17619  0 
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
arc4                   12608  0 
cordic                 12574  0 
brcmutil               15618  0 
mac80211              630653  0 
cfg80211              484040  2 wl,mac80211
uvcvideo               80885  0 
snd_hda_codec_hdmi     46368  1 
videobuf2_vmalloc      13216  1 uvcvideo
snd_hda_codec_realtek    65580  1 
intel_rapl             18773  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
nouveau              1097199  1 
videobuf2_core         40664  1 uvcvideo
x86_pkg_temp_thermal    14205  0 
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_intel          56451  6 
rts5139               335409  0 
intel_powerclamp       14705  0 
btusb                  32412  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
i915                  783805  4 
coretemp               13435  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
mxm_wmi                13021  1 nouveau
kvm                   451511  0 
ttm                    85115  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         53081  2 i915,nouveau
snd_rawmidi            30144  1 snd_seq_midi
drm                   303102  8 ttm,i915,drm_kms_helper,nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
crct10dif_pclmul       14289  0 
snd_timer              29482  2 snd_pcm,snd_seq
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
i2c_algo_bit           13413  2 i915,nouveau
snd                    69322  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
soundcore              12680  1 snd
lpc_ich                21080  0 
mei                    82276  1 mei_me
cryptd                 20359  1 ghash_clmulni_intel
ideapad_laptop         18216  0 
wmi                    19177  2 mxm_wmi,nouveau
joydev                 17381  0 
sparse_keymap          13948  1 ideapad_laptop
video                  19476  2 i915,nouveau
bnep                   19624  2 
mac_hid                13205  0 
serio_raw              13462  0 
rfcomm                 69160  8 
bluetooth             391136  22 bnep,btusb,rfcomm
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
r8169                  67581  0 
ahci                   25819  2 
libahci                32716  1 ahci
psmouse               106678  0 
mii                    13934  1 r8169
isak@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:9e:01:78:f6:a2  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a9e:1ff:fe78:f6a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:555411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:496178506 (496.1 MB)  TX bytes:43344087 (43.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:39147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4328191 (4.3 MB)  TX bytes:4328191 (4.3 MB)

wlan0     Link encap:Ethernet  HWaddr 68:94:23:fa:6c:d3  
          inet6 addr: fe80::6a94:23ff:fefa:6cd3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:362204
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18080 (18.0 KB)  TX bytes:18816 (18.8 KB)
          Interrupt:18 

isak@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
isak@ubuntu:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search lan
isak@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
isak@ubuntu:~$ iwlist chan
eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
isak@ubuntu:~$ sudo iwlist scan
[sudo] password for isak: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:3B:6D:4C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"TeliaGateway00-26-44-3B-6D-4C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 001D54656C69614761746577617930302D32362D34342D33422D36442D3443
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700103C2ED33BE1775E2BBFD67CFF5E9179561021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420009313031354E54454D321054000800060050F20400011011000D54686F6D736F6E20544737383410080002008410570001001041000100
                    IE: Unknown: DD090010180205F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 02 - Address: AC:16:2D:E8:F1:B0
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Levi_Wlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 00094C6576695F576C616E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 23021300
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 470104
                    IE: Unknown: 2D1AAC0103FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
          Cell 03 - Address: AC:16:2D:E8:F1:B1
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Levi_Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000A4C6576695F4775657374
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030107
                    IE: Unknown: 23021300
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 470104
                    IE: Unknown: 2D1AAC0103FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00


```

---

### Post by praseodym on 2014-09-01
Which of that cells is yours? Anyway, change the encryption to pure WPA2-AES (CCMP), check the router manual.

If it doesnt work use the native driver:
```

sudo apt-get install linux-firmware-nonfree 
sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Reboot.

---

### Post by Isak_Falk on 2014-09-02
Thank you, will try it out when I get home.

Ps. The broadcom one is mine.

---

