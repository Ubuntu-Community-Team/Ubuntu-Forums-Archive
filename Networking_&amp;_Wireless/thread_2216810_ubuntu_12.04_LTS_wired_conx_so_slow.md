---
title: "ubuntu 12.04 LTS wired conx so slow"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by 5vlastkzn on 2014-04-14
Hello guys, 
i am using ubuntu 12.04 64 bit fresh install my MB is gigabyte X58A-ud7 my lan card RTL8111D 
since allot of articls talking about  the driver r8169 i had download and install the driver from realteak website which it's r8168 
[TABLE="width: 600"]
[TR]
[TD="class: etxt-top10-box, bgcolor: #FFFFFF"][LEFT]LINUX driver for kernel 3.x and 2.6.x and 2.4.x
[/LEFT]
[/TD]
[TD="class: etxt-center, bgcolor: #FFFFFF"]8.038[/TD]
[TD="class: etxt-center, bgcolor: #FFFFFF"]2014/3/4[/TD]
[TD="class: etxt-right, bgcolor: #FFFFFF"][/TD]
[/TR]
[/TABLE]
i had update server source select best server 
when i am downloading with firefox a file it's get normal rate 200KB / S but when i am downloading from source apt-get it's really slow max 16 KB/ Second i did not had such problem with my correctly conx what else case this problem

---

### Post by praseodym on 2014-04-14
Please show
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
```
Did you blacklist r8169?

---

### Post by 5vlastkzn on 2014-04-14
thank you for the fire replay 

uname -a
```
Linux server-X58A-UD7 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

lspci -nnk | grep -iA2 net
```
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8168
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8168
```
lsmod
```

Module                  Size  Used by
bnep                   24107  2 
rfcomm                 74718  0 
bluetooth             391726  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
uvcvideo               82247  0 
snd_usb_audio         155876  1 
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_usbmidi_lib        29527  1 snd_usb_audio
joydev                 17613  0 
radeon               1447330  3 
ttm                    84837  1 radeon
rt2800usb              27225  0 
rt2800lib              81972  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
mxm_wmi                13021  0 
drm_kms_helper         53237  1 radeon
drm                   306660  5 radeon,ttm,drm_kms_helper
rt2x00usb              20886  1 rt2800usb
rt2x00lib              56180  3 rt2800usb,rt2800lib,rt2x00usb
wmi                    19256  1 mxm_wmi
i2c_algo_bit           13564  1 radeon
snd_hda_codec_hdmi     41736  1 
serio_raw              13413  0 
snd_hda_codec_realtek    56448  1 
i7core_edac            24565  0 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              619465  3 rt2800lib,rt2x00usb,rt2x00lib
snd_hwdep              13613  2 snd_usb_audio,snd_hda_codec
snd_pcm               107140  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30416  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    73753  25 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
cfg80211              499466  2 rt2x00lib,mac80211
gpio_ich               13526  0 
edac_core              62944  2 i7core_edac
lpc_ich                21163  0 
mac_hid                13253  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
hid_a4tech             12685  0 
usbhid                 53329  0 
hid                   106315  3 hid_generic,hid_a4tech,usbhid
firewire_ohci          45076  0 
firewire_core          65168  1 firewire_ohci
pata_acpi              13038  0 
crc_itu_t              12707  1 firewire_core
pata_jmicron           12758  0 
ahci                   30063  2 
libahci                32118  1 ahci
r8168                 266113  0 

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:94:58:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:53 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 1c:6f:65:94:58:cf  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fe94:58cf/64 Scope:Link
          inet6 addr: fd58:48c8:2da5:0:4853:c66d:6ad8:d04a/64 Scope:Global
          inet6 addr: fd58:48c8:2da5:0:1e6f:65ff:fe94:58cf/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:434988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:587032181 (587.0 MB)  TX bytes:23980377 (23.9 MB)
          Interrupt:54 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:733664 (733.6 KB)  TX bytes:733664 (733.6 KB)


```

cat /etc/resolv.conf

```

server@server-X58A-UD7:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1


```

YES I DID BLACKLIST IT

---

### Post by praseodym on 2014-04-14
You are online with a wireless stick? Try to "Ignore" IPv6 in the network-manager applet. Reconnect. If its not enough try these nameservers:
```

echo "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by 5vlastkzn on 2014-04-14
no i am useing lan i do not have wlan hardware

---

### Post by 5vlastkzn on 2014-04-14
nothing change :( very slow using apt

---

### Post by praseodym on 2014-04-14
There is a wireless driver loaded:
```

sudo modprobe -rfv rt2800usb
sudo service network-manager restart
```
Please also show:
```

sudo apt-get install ethtool
sudo ethtool eth1
```

---

### Post by 5vlastkzn on 2014-04-14
ethtool eth1
```

Settings for eth1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes


```

---

### Post by praseodym on 2014-04-14
Lets check:
```

sudo ethtool -s eth1 speed 1000 duplex full
sudo ethtool eth1
```
If theres no connection afterwards, reverse it

```
sudo ethtool -s eth1 speed 100 duplex full
```

---

### Post by 5vlastkzn on 2014-04-14
```

Settings for eth1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Half
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no


```

---

### Post by praseodym on 2014-04-14
```
    Speed: Unknown!
...
    Link detected: no
```
So, this does not work, reverse it. You may want to try to deactivate the auto-negotiation of the card:

```
sudo ethtool -s eth1 autoneg off
```

---

### Post by 5vlastkzn on 2014-04-14
```

5,609 B/s 13min

```
NOTHING WORK

---

### Post by praseodym on 2014-04-14
I'm running out of ideas. How do you connect? Is it a router? Are the Login/PW of your ISP in the router interface?

---

### Post by 5vlastkzn on 2014-04-14
Yes i am connecting throw router ZyXEL_KEENETIC_4G_4BD558 | and i had in the same machine ubuntu 10.04 lts i did not face such problem i just made fresh install of this facing that over apt-get only very slow download rate with browsers it's just fantastic

---

### Post by 5vlastkzn on 2014-04-14
PLease Help what else i can do

---

### Post by praseodym on 2014-04-14
Did you add Login/PW in the "DSL" section of the network-manager or in your router interface? Tried to reset the router?

---

