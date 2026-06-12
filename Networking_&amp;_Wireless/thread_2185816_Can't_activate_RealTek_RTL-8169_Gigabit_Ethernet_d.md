---
title: "Can't activate RealTek RTL-8169 Gigabit Ethernet driver"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by kroeze on 2013-11-04
When I go through systems settings into additional drivers, my Ethernet driver is not activated. When I click on it to activate it I get the following error message:
```
"Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log"
```


This is what is read in /var/log/jockey.log

```
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'platform:chromeos_acpi')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'pci:v00008086d00001C26sv00008086sd00001C26bc0Csc03i20')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,009A,009B,00C0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2013-11-04 12:14:30,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x32e2ab8> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-11-04 12:17:01,092 DEBUG: unbind/rebind on driver /sys/module/r8169/drivers/pci:r8169: device 0000:02:00.0
2013-11-04 12:17:02,048 DEBUG: writing back check cache /var/cache/jockey/check
``` 

Any help would be greatly appreciated! 

Thanks :)

---

### Post by praseodym on 2013-11-04
Do you need it?! Check
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
dmesg | grep r8
cat /etc/resolv.conf
cat /etc/network/interfaces
```
Does wireless work?

---

### Post by kroeze on 2013-11-04
Thanks for the help! Unfortunately I do need the Ethernet since my wifi is very poor at my office on campus. 

The result of lspci -nnk | grep -iA2 net is:
```
01:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)    Subsystem: Samsung Electronics Co Ltd Device [144d:4107]
    Kernel driver in use: ath9k
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

The result of lsmod is:
```
Module                  Size  Used byr8169                  45120  0 
fuse                   59846  2 
uvcvideo               59368  0 
videobuf2_core         25315  1 uvcvideo
videodev               85508  1 uvcvideo
videobuf2_vmalloc      12313  1 uvcvideo
videobuf2_memops       12396  1 videobuf2_vmalloc
rfcomm                 25259  0 
bluetooth             161077  9 rfcomm
memconsole             12352  0 
joydev                 16448  0 
isl29018               12352  0 
industrialio           17379  1 isl29018
snd_hda_codec_hdmi     29021  1 
snd_hda_codec_cirrus    20544  1 
ath9k                 118081  0 
snd_hda_intel          24640  3 
mac80211              318094  1 ath9k
snd_hda_codec          71488  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
ath9k_common           12643  1 ath9k
snd_hwdep              12390  1 snd_hda_codec
ath9k_hw              355782  2 ath9k,ath9k_common
ath                    21066  3 ath9k,ath9k_common,ath9k_hw
cfg80211              141215  3 ath9k,mac80211,ath
snd_pcm                61370  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nm10_gpio              12352  0 
snd_timer              21094  1 snd_pcm
snd_page_alloc         12806  2 snd_hda_intel,snd_pcm
```

The result of ifconfig -a is:
```
eth0      Link encap:Ethernet  HWaddr e8:03:9a:e0:8a:5e            inet6 addr: fe80::ea03:9aff:fee0:8a5e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162195 (162.1 KB)  TX bytes:4624 (4.6 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:687668 (687.6 KB)  TX bytes:687668 (687.6 KB)


wlan0     Link encap:Ethernet  HWaddr 74:e5:43:a5:f3:f5  
          inet addr:192.168.2.39  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::76e5:43ff:fea5:f3f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54483471 (54.4 MB)  TX bytes:10027760 (10.0 MB)
```

I didn't get any result for dmesg | grep r8

The result of cat /etc/resolv.conf is:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search home
nameserver 192.168.2.1
search home.
options single-request timeout-ms:300 attempts:15
```

and finally the result of cat /etc/network/interfaces is:
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback
```

---

### Post by praseodym on 2013-11-04
The driver is already installed, but r8169 is poor. Install r8168 instead:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/14/31/3005217-r8168-dkms-8.036.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.036.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.036.00
sudo dkms build -m r8168-dkms -v 8.036.00
sudo dkms install -m r8168-dkms -v 8.036.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by kroeze on 2013-11-04
Thanks for all of your help! Unfortunately I am running a Chromebook with Ubuntu 12.04 LTS and there are problems installing linux-headers-3.4.0. This is a completely separate problem, but thanks a bunch for all of your help! :)

---

