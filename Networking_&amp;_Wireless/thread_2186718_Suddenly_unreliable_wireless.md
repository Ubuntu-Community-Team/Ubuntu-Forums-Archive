---
title: "Suddenly unreliable wireless"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by IanKoro on 2013-11-08
I have three computers in the house, two desktops, and one laptop. They all connect through the wifi, one of the desktops used to have a direct cable connection, but due to wiring issues, this is no longer an option. 

For a few months after switching that desktop to wifi, everything was fine, but in the last few weeks, the connection has been unreliable. Sometimes everything is fine for a few hours, others it disconnects every few minutes, or will work for a while and disconnect, etc... Occasionally a reboot will solve the problem for a while, but not always. This computer dual boots Windows 7 and Ubuntu, and the problem is pretty much the same in both.

The laptop and other PC don't seem to have any issues whatsoever.

I've been searching around for similar issues online, but I can't find any helpful replies anywhere. I figured that the Ubuntu crowd might be a bit more knowledgeable than elsewhere.

The router is in my roommate's room, and he's not home, so I can't get in to take a look at the moment, but I've obviously rebooted it a bunch. I just tried to connect to the router's http interface (at 192.168.0.1) to check the model, and I'm unable to connect, which is a new issue, though I'm able to ping the router just fine.

Thanks for anyone's time.

---

### Post by praseodym on 2013-11-09
Please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```

---

### Post by tgalati4 on 2013-11-09
Install *wifi-radar *and count the number of wireless networks that show up.  It could be wireless interference.

---

### Post by IanKoro on 2013-11-14
Sorry about the delay, I hope this is still seen.

Wifi-radar only shows my network. I'm in a relatively uncrowded suburban area with elderly people living around me, so there's a little less wifi than you'd see in many places.


Here's the various outputs:


**uname -a**

```

ian@ScratchBox:~$ uname -a
Linux ScratchBox 3.8.0-33-generic #48-Ubuntu SMP Wed Oct 23 09:16:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

**lspci -nnk | grep -iA2 net**

```

ian@ScratchBox:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	Subsystem: Lenovo Device [17aa:3616]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176]
	Kernel driver in use: rtl8192ce


```

**lsusb**

```


ian@ScratchBox:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 04f2:0833 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer



```

**lsmod**

```


ian@ScratchBox:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39815  1 
snd_hrtimer            12744  1 
bnep                   18036  2 
rfcomm                 42641  4 
bluetooth             228808  10 bnep,rfcomm
parport_pc             28152  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
snd_hda_codec_hdmi     36906  4 
coretemp               13355  0 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  5 
kvm_intel             132891  0 
snd_hda_codec         136498  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   443165  1 kvm_intel
arc4                   12615  2 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
nouveau               943184  4 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  1 
aes_x86_64             17255  1 aesni_intel
rtl8192ce              53594  0 
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
snd_seq_midi           13324  0 
gf128mul               14951  2 lrw,xts
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rtlwifi                79673  1 rtl8192ce
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  3 snd_hrtimer,snd_pcm,snd_seq
mxm_wmi                13021  1 nouveau
rtl8192c_common        48779  1 rtl8192ce
wmi                    19070  2 mxm_wmi,nouveau
snd                    68876  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192ce
video                  19390  1 nouveau
lp                     17759  0 
soundcore              12680  1 snd
ttm                    83187  1 nouveau
drm_kms_helper         49394  1 nouveau
drm                   286028  6 ttm,drm_kms_helper,nouveau
psmouse                95905  0 
parport                46345  3 lp,ppdev,parport_pc
cfg80211              511019  2 mac80211,rtlwifi
usb_storage            57204  0 
mei                    41158  0 
microcode              22881  0 
mac_hid                13205  0 
gpio_ich               13476  0 
i2c_algo_bit           13413  1 nouveau
serio_raw              13215  0 
lpc_ich                17061  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101289  2 hid_generic,usbhid
ahci                   25731  4 
libahci                31364  1 ahci
e1000e                198832  0 



```

**ifconfig -a**

```



ian@ScratchBox:~$ ifconfig -a
em1       Link encap:Ethernet  HWaddr c8:9c:dc:68:f8:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fa300000-fa320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:331721 (331.7 KB)  TX bytes:331721 (331.7 KB)

wlan0     Link encap:Ethernet  HWaddr ac:81:12:b9:03:3b  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ae81:12ff:feb9:33b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39268955 (39.2 MB)  TX bytes:3413051 (3.4 MB)




```

**iwconfig**

```



ian@ScratchBox:~$ iwconfig
lo        no wireless extensions.

em1       no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MARCO"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E8:40:F2:6E:56:ED   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0



```

**cat /etc/resolv.conf**

```


ian@ScratchBox:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```

**iwlist chan**

```

ian@ScratchBox:~$ iwlist chan
lo        no frequency information.

em1       no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

```

**sudo iwlist scan**

```

ian@ScratchBox:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

em1       Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E8:40:F2:6E:56:ED
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"MARCO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000682ef6e582
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00054D4152434F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

ian@ScratchBox:~$ 


```

Hope this helps somehow. Thanks to anyone who takes the time to look this over.

---

### Post by praseodym on 2013-11-14
Try pure WPA2-AES (CCMP) encryption, check the router manual.

Additionally/alternatively, try the following module parameters:

```
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

---

