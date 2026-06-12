---
title: "Ubuntu 13.10 Wifi spotty RTL8188EE adapter dual boot win8.1"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by claven123 on 2014-01-20
I have a Toshipa laptop and I dual boot with win 8.1 on unbuntu 13.10.  I have very spotty wift that comes and goes on the laptop on the ubuntu side, while in Win 8.1 it is quite good in the exact same location.  I can boot back and forth and see a dramatic difference.  I've attempted some fixes and diagnostic work on various websites, but none seem to help with me.  I have similar experiences on my work network vs my home network.  (worse at work, but that's the network I believe)

Here is the output on the sticky instructions.

```
Toshiba satellite c55a5302 laptop  
 

 $ lsusb
 Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller  
 

 $ lspci 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)  
 

 

 

 ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:8c:fa:6e:06:d3   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:16  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:65536  Metric:1  
           RX packets:787 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:787 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:77962 (77.9 KB)  TX bytes:77962 (77.9 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 48:d2:24:b2:29:9f   
           inet addr:10.254.243.33  Bcast:10.254.255.255  Mask:255.255.0.0  
           inet6 addr: fe80::4ad2:24ff:feb2:299f/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:74121 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:15484 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:24781753 (24.7 MB)  TX bytes:3459491 (3.4 MB)  
 

 

 

 lwconfig
 

 wlan0     IEEE 802.11bgn  ESSID:"eeeegtddhome"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 2C:36:F8:0C:D3:14    
           Bit Rate=72.2 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off  
           Power Management:off  
           Link Quality=68/70  Signal level=-42 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:1   Missed beacon:0  
 

 

 

 lsmod
 

 Module                  Size  Used by  
 

 rfcomm                 69130  0  
 

 bluetooth             372041  10 bnep,rfcomm  
 

 

 

 snd_hda_codec_realtek    55704  1  
 snd_hda_intel          48171  3  
 snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel  
 snd_hwdep              13602  1 snd_hda_codec  
 snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel  
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel  
 snd_seq_midi           13324  0  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 snd_rawmidi            30095  1 snd_seq_midi  
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi  
 lp                     17759  0  
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi  
 snd_timer              29433  2 snd_pcm,snd_seq  
 uvcvideo               80885  0  
 snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi 
 parport                42299  3 lp,ppdev,parport_pc  
 arc4                   12608  2  
 videobuf2_vmalloc      13216  1 uvcvideo  
 videobuf2_memops       13362  1 videobuf2_vmalloc  
 videobuf2_core         40499  1 uvcvideo  
 videodev              133509  2 uvcvideo,videobuf2_core  
 rts5139               331166  0  
 rtl8188ee              89614  0  
 i915                  661261  3  
 mei_me                 18421  0  
 rtl_pci                26641  1 rtl8188ee  
 mei                    77782  1 mei_me  
 rtlwifi                63229  2 rtl_pci,rtl8188ee  
 drm_kms_helper         52710  1 i915  
 drm                   297056  4 i915,drm_kms_helper  
 mac80211              597268  3 rtl_pci,rtlwifi,rtl8188ee  
 psmouse                97655  0  
 cfg80211              480503  2 mac80211,rtlwifi  
 soundcore              12680  1 snd  
 microcode              23576  0  
 i2c_algo_bit           13413  1 i915  
 mac_hid                13205  0  
 serio_raw              13413  0  
 lpc_ich                21080  0  
 video                  19318  1 i915  
 hid_logitech_dj        18581  0  
 usbhid                 53014  0  
 hid                   105858  3 usbhid,hid_logitech_dj  
 alx                    32452  0  
 mdio                   13807  1 alx  
 ahci                   25819  4  
 libahci                31928  1 ahci  
 

 

 ubuntu 13.10
 3.11.0-15-generic x86_64  



```

---

### Post by claven123 on 2014-01-30
Any suggestions?

Thanks

---

### Post by claven123 on 2014-02-10
I've noticed at times it will not connect to the wifi and keeps searching.

d

---

