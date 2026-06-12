---
title: "Ubuntu 14.04 LTS WIFI Connection Issue with ASUS DSL-N10s Wireless N-150 Modem Router"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by deepak18 on 2014-09-07
I have installed Ubuntu 14.04 on my dell laptop Insprion 14R.
I am using ASUS DSL-N10s Wireless N-150 Modem Router.

I am able to connect to internet through wire but i am not able to connect to internet using WIFI.

Network Manager is able to find WIFI SSID but it is not able to connect through it.

I try few solutions already mentioned on forums e.g. installing firmware but i am not able to solve this issue.

Please Help!! Seriously!!!!!!!!!!!!

---

### Post by praseodym on 2014-09-07
Please show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
rfkill list
sudo iwlist scan
```

---

### Post by deepak18 on 2014-09-07
uname -a
```

Linux Programmer 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux
```


lspci -nnk | grep -iA2 net

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0456]
    Kernel driver in use: atl1c


```



lsusb
```

Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6461 Microdia 
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod
```


Module                  Size  Used by
rfcomm                 53664  8 
bnep                   18895  2 
binfmt_misc            13140  1 
snd_hda_codec_hdmi     45440  1 
snd_hda_codec_realtek    55163  1 
btusb                  27580  0 
bluetooth             342208  22 bnep,btusb,rfcomm
snd_hda_intel          42730  3 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17808  0 
snd_rawmidi            25135  1 snd_seq_midi
dcdbas                 14448  1 dell_laptop
lib80211_crypt_tkip    17456  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             132549  0 
kvm                   388084  1 kvm_intel
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
wl                   3999690  0 
joydev                 17101  0 
i915                  705659  8 
serio_raw              13230  0 
intel_ips              18217  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lib80211               14040  2 wl,lib80211_crypt_tkip
lpc_ich                16864  0 
snd_timer              28584  2 snd_pcm,snd_seq
cfg80211              409394  1 wl
snd                    60939  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         47182  1 i915
mei_me                 18195  0 
drm                   244037  4 i915,drm_kms_helper
soundcore              12600  1 snd
wmi                    18673  1 dell_wmi
mei                    66737  1 mei_me
i2c_algo_bit           13197  1 i915
video                  18903  1 i915
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  3 hid_generic,usbhid
ums_realtek            17733  0 
usb_storage            48417  1 ums_realtek
ahci                   25579  4 
psmouse                91329  0 
libahci                27214  1 ahci
atl1c                  40949  0 

```


iwconfig
```


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.
```



ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr b8:ac:6f:67:8d:08  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe67:8d08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3136 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2084897 (2.0 MB)  TX bytes:668503 (668.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130176 (130.1 KB)  TX bytes:130176 (130.1 KB)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:ae:cf:fd  
          inet6 addr: fe80::7ae4:ff:feae:cffd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

```


rfkill list 
```



0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```


sudo iwlist scan
```



wlan0     Scan completed :
          Cell 01 - Address: 60:A4:4C:85:C5:D3
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"ASUS-BSNL_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 0011415355532D42534E4C5F4E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DDAE0050F204104A0001101044000102103B000103104700106304125310192006122860A44C85C5D31021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000B4144534C20526F757465721024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F2040001101100154144534C20526F757465722F4D6F64656D204947441008000206861049000600372A000120
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408001300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

---

### Post by praseodym on 2014-09-07
Use the native driver instead:
```

sudo apt-get install linux-firmware-nonfree 
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Reboot. You better c/p these lines ;)

---

### Post by deepak18 on 2014-09-08
I have try your solution but its not working :(

Only starting 2 commands are working 

sudo apt-get install linux-firmware-nonfree 
sudo apt-get remove --purge bcmwl-kernel-source


all other commands get error for** NO input FILE**
Please help me to solve this issue.
Now its even not searching SSID or Network ID of Modem

```
sudo rm /etc/modprobe.d/blacklist-bcm43.confrm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory

sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*)
sed: no input files
```

---

### Post by praseodym on 2014-09-08
Its Ok, if the files are not there. Reboot

---

### Post by deepak18 on 2014-09-09
yes, i have reboot it but its not working, [COLOR=#000000]Now its even not showing SSID or Network ID of Modem in Network manager. [/COLOR]

---

### Post by deepak18 on 2014-09-09
> **praseodym said:**
> Its Ok, if the files are not there. Reboot

Is there any other solution ?

---

