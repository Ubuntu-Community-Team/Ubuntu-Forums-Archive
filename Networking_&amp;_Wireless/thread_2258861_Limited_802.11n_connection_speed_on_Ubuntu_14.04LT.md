---
title: "Limited 802.11n connection speed on Ubuntu 14.04LTS with ASUS RT-N66U router"
date: 2014-12-31
forum: Networking &amp; Wireless
---

### Post by Derek_Carpenter on 2014-12-31
My router is running Shibby Tomato and is configured to where all other wireless devices on my network are having no connection issues with 802.11n. The only issue is with Ubuntu machines.

I have tried the stock RTL8188EE with my Toshiba C55-A5100 in addition to a AR5BHB92 AR9280 adapter and an Edimax USB EW-7811Un; all of these adapters will merely acheive a max download speed 3mbps on 802.11n, however the upload speed is seemingly unaffected. Once I switch the broadcast mode on my router to 802.11g the download speed is significantly higher (12-25mbps).

I attempted to run a liveCD version of Ubuntu 12.04LTS to see if this could be an issue with the newer version, however the same problem persists. The same limitation occurs on my roommate's HP 14-b109wm, which is also running Ubuntu 14.04LTS.

Is this a known issue with Ubuntu, or could it happen to be somewhat of a compatibility issue with the standard driver set and my router/router's firmware?

---

### Post by praseodym on 2014-12-31
Please run the following commands and show the outputs with all devices
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
route -n
cat /etc/resolv.conf
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
iwlist chan
sudo iwlist scan
```

---

### Post by Derek_Carpenter on 2014-12-31
X:~$ uname -a
Linux X-X  3.16.0-031600-lowlatency #201408031935 SMP PREEMPT Sun Aug 3 23:44:11  UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

X:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0191]
    Kernel driver in use: rtl8188ee

X:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

X:~$ lsmod
Module                  Size  Used by
ctr                    13193  2 
ccm                    17856  2 
bnep                   19884  2 
rfcomm                 75114  0 
bluetooth             471033  10 bnep,rfcomm
6lowpan_iphc           18968  1 bluetooth
uvcvideo               86628  0 
dm_crypt               23456  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59635  1 uvcvideo
snd_hda_codec_hdmi     48243  1 
snd_hda_codec_realtek    73695  1 
v4l2_common            15715  1 videobuf2_core
snd_hda_codec_generic    70087  1 snd_hda_codec_realtek
videodev              154834  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_intel          30634  3 
media                  22008  2 uvcvideo,videodev
snd_hda_controller     31373  1 snd_hda_intel
snd_hda_codec         144889  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17709  1 snd_hda_codec
snd_pcm               105002  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            31148  1 snd_seq_midi
snd_seq                63540  2 snd_seq_midi_event,snd_seq_midi
parport_pc             32906  0 
arc4                   12573  2 
intel_rapl             19196  0 
ppdev                  17711  0 
8192cu                628527  0 
lp                     17799  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
x86_pkg_temp_thermal    14312  0 
intel_powerclamp       19099  0 
snd_timer              30069  2 snd_pcm,snd_seq
rtl8188ee              95951  0 
coretemp               13638  0 
rtl_pci                27306  1 rtl8188ee
mei_me                 19565  0 
toshiba_acpi           28375  0 
kvm_intel             149130  0 
rtlwifi                69157  2 rtl_pci,rtl8188ee
joydev                 17538  0 
snd                     83976  17  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
kvm                   468402  1 kvm_intel
mac80211              699524  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              533464  2 mac80211,rtlwifi
serio_raw              13434  0 
sparse_keymap          13890  1 toshiba_acpi
parport                42432  3 lp,ppdev,parport_pc
mei                    88632  1 mei_me
lpc_ich                21176  0 
crct10dif_pclmul       14268  0 
crc32_pclmul           13180  0 
ghash_clmulni_intel    13230  0 
toshiba_bluetooth      12867  0 
nls_iso8859_1          12713  1 
soundcore              15091  2 snd,snd_hda_codec
cryptd                 20531  1 ghash_clmulni_intel
mac_hid                13275  0 
i915                  945754  3 
i2c_algo_bit           13564  1 i915
psmouse               113048  0 
drm_kms_helper         62042  1 i915
drm                   316819  5 i915,drm_kms_helper
ahci                   30167  2 
libahci                32533  1 ahci
alx                    41397  0 
mdio                   13561  1 alx
wmi                    19379  1 toshiba_acpi
video                  20521  1 i915

X:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AlphaMeow"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr
          Power Management
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:616   Missed beacon:0

X:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.25.1    0.0.0.0         UG    0      0        0 wlan0
192.168.25.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

X:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search XXXX

X:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr XXXXX 
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
          RX packets:824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76268 (76.2 KB)  TX bytes:76268 (76.2 KB)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXX 
          inet addr:192.168.25.57  Bcast:192.168.25.255  Mask:255.255.255.0
          inet6 addr: XXXXXXX/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8945767 (8.9 MB)  TX bytes:9976408 (9.9 MB)

X:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="XXXXXX",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="XXXXXX",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="XXXXXX",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="XXXXXX",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

---

### Post by Derek_Carpenter on 2014-12-31
Someone please help, I really would like to give Linux a chance!

---

### Post by praseodym on 2014-12-31
Check these module parameters for the internal card:

```
echo "options rtl8188ee ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf
```
Reboot.

---

### Post by Derek_Carpenter on 2014-12-31
Thank you, but that did not make any difference.

---

### Post by Derek_Carpenter on 2014-12-31
The interesting part is that both laptops of different model are experiencing the exact same issue, but only with Ubuntu Linux.

---

### Post by praseodym on 2014-12-31
Ok, lets try some nameservers:
```

echo -e "nameserver 192.168.25.1\nnameserver 8.8.8.8" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Derek_Carpenter on 2014-12-31
Still won't get past 3mbps. Nameserver looks right, it's pointing to my router. The second one is just 8.8.8.8.

---

### Post by praseodym on 2015-01-01
Check the following router settings:
[LIST=1]
[*]fixed channel
[*]network not hidden
[*]bandwidth to 20MHz instead of 20/40MHz
[*]mode to b/g/n
[/LIST]

---

### Post by Derek_Carpenter on 2015-01-01
1. I have had the router set to the 6 since 1 and 11 have more networks that 6.
2. Network is not hidden.
3. I changed this to 20MHz a while back when I was having stability issues.
4. I do not have a b/g/n setting, but I believe "Auto" is equivalent to that; when set to Auto there is no change. I also tend to have some issues with other devices when my router is set to "Auto," so I've found that it works much better in "N only." One thing I have noticed is that if I increase to 40Mhz I end up with double the speed (6Mbps, instead of 3). Again, if I set the router to "G only" the laptop then has full internet bandwidth.

---

### Post by praseodym on 2015-01-01
There is another Realtek driver loaded (from the stick):
```

sudo modprobe -rfv rtl8188ee 8192cu
sudo modprobe -v rtl8188ee
```

Check:
```

dmesg | grep rtl
iwconfig
```

> ```
 The interesting part is that both laptops of different model are experiencing the exact same issue, but only with Ubuntu Linux. 
```
Obviously, a Router thing because of different drivers?!

---

### Post by Derek_Carpenter on 2015-01-01
X:~$ sudo modprobe -rfv rtl8188ee 8192cu
[sudo] password for X:
rmmod rtl8188ee
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
rmmod 8192cu
X:~$ dmesg | grep rtl
[   11.924973] rtl8192cu driver version=v4.0.2_9000.20130911
[   11.925014] usbcore: registered new interface driver rtl8192cu
[   12.057269] rtl8188ee: rtl8188ee: Power Save off (module option)
[   12.057272] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   12.057277] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.511296] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.511505] rtlwifi: wireless switch is on
[  189.641159] usbcore: deregistering interface driver rtl8192cu
X:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


So are you saying that this is a driver conflicting with the router's firmware somehow?

---

### Post by Derek_Carpenter on 2015-01-01
I don't have this issue with my adroid devices nor with my windows 7 laptop.

---

### Post by Derek_Carpenter on 2015-01-01
Oops, that last iwconfig didn't show any networks because the last modprobe command destabilized my wifi connection, causing it to cycle over and over until I performed a reboot.

Here is the result after reboot:

X:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"AlphaMeow"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 76:D0:2B:D1:24:B1   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:55   Missed beacon:0

---

### Post by praseodym on 2015-01-01
Which device is it?
```

cat /etc/udev/rules.d/70-persistent-net.rules
lsmod
```

---

### Post by Derek_Carpenter on 2015-01-01
It's wlan0 in the cat commmand - RTL8188EE

that's listed as rtl_pci in lsmod.

---

### Post by Derek_Carpenter on 2015-01-02
I got to thinking about how I've experienced this problem on two separate Ubuntu machines and how Praseodym had suggested a router issue, so I decided to start taking a look at my advanced wireless settings in Tomato.

As I was systematically changing one setting at a time, checking for any changes, and then checking the results, and then changing them back, I encountered the 802.11n preamble setting. I had previously set my 802.11n preamble to "Green Field" because there are no devices on my network that require 802.11g.

After trying various 802.11n preamble settings, it became clear that the "Green Field" setting was the culprit in limiting my connection speed. I also found that others have had this same issue.

Fixing the problem involved either choosing "GF-BRCM" or "Mixed Mode." Auto might also accomplish the same, but could result in erratic behavior if at some moment Tomato decides that "Green Field" is appropriate.

Thanks for your help, Praseodym! I hope people find this helpful!!

---

