---
title: "LAN Transfer speed 10MB/s when using a USB3-E1000 Gigabit adapter"
date: 2014-04-12
forum: Networking &amp; Wireless
---

### Post by DXXPublic on 2014-04-12
Hi all, 

Im fairly new to the linux world and im on the learning process. I have a Dell system with Ubuntu 12.04 installed.  Since i needed  a gigabit nic, i decided to purchase a USB3-E1000 adapter.  I plugged it in and it detected it right away.  When i lshw the network this is what i get 
network
       description: Ethernet interface
       physical id: 2
       bus info: usb@4:1
       logical name: eth1
       serial: 8c:ae:4c:fd:21:8a
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=192.168.0.109 link=yes multicast=yes port=MII speed=1Gbit/s

I thought that i was all set up and also on the connection info it says 1000Mb/s but whenever i try to transfer a file the transfer speed is around 10-14 MB/s.

This is what ive tried so far.   (Sys1 is the laptop where i have the USB3 Adapter connected)
Location A:  
1. Connected Sys1 to Gigabit switch using a Cat5e cable
2. made sure i was not connected to wireless
3. Checked connection info - 1000Mb/s 
4. Started transfer to a WDMyCloud Network HDD (made sure the device led were all green indicating Gigabit connection)
5. Results - 11MB/s

Location B
1.Connected Sys1 to Gigabit switch using different Cat5e cable
2. made sure i was not connected to wireless
3. Checked connection info - 1000Mb/s 
4. Started transfer via SCP to Sys2 (Ubuntu as well) with Gigabit connection also showing 1000Mb/s
5. Results - 13MB/s

Everything seems to be in place from my view, but i might missing something.  Since im learning Linux, im getting a hard time troubleshooting further and i was wondering if you could give me a hand

Thanks in advance

J

---

### Post by varunendra on 2014-04-12
What are the outputs of -
```
ifconfig -a
nm-tool
route -n
modinfo ax88179_178a
lsmod
ping -c4 google.com
```
??

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by DXXPublic on 2014-04-13
Thanks for your reply.

The information below

ifconfig -a
```

eth1  Link encap:Ethernet  HWaddr 8c:ae:4c:fd:21:8a  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8eae:4cff:fefd:218a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:549081 (549.0 KB)  TX bytes:438231 (438.2 KB)

```

nm-tool
```
- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ax88179_178a
  State:             connected
  Default:           yes
  HW Address:        8C:AE:4C:FD:21:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1


```

modinfo ax88179_178a
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
dxx@DXXBuntu:~$ modinfo ax88179_178a
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/usb/ax88179_178a.ko
license:        GPL
description:    ASIX AX88179/178A based USB 3.0/2.0 Gigabit Ethernet Devices
srcversion:     EFC95C503DEFA5D6B2A8853
alias:          usb:v0DF6p0072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B95p178Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B95p1790d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbnet,mii
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 

```

lsmod
```
Module                  Size  Used by
rfcomm                 74718  12 
bnep                   24107  2 
parport_pc             32866  0 
ppdev                  17711  0 
uvcvideo               82247  0 
videobuf2_core         40815  1 uvcvideo
binfmt_misc            17508  1 
snd_hda_codec_hdmi     41773  1 
videodev              138562  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
arc4                   12573  2 
snd_hda_codec_realtek    57219  1 
ath9k                 162124  0 
i915                  688399  3 
snd_hda_intel          57134  3 
mac80211              623607  1 ath9k
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ax88179_178a           22488  0 
snd_hwdep              13613  1 snd_hda_codec
rts5139               318185  0 
usbnet                 39575  1 ax88179_178a
drm_kms_helper         53237  1 i915
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm                   306660  4 i915,drm_kms_helper
ath9k_common           13859  1 ath9k
ath9k_hw              457718  2 ath9k,ath9k_common
joydev                 17613  0 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
dell_wmi               12761  0 
sparse_keymap          13890  1 dell_wmi
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            17425  0 
wmi                    19256  1 dell_wmi
ath3k                  13368  0 
btusb                  28374  0 
lpc_ich                21163  0 
mei_me                 18418  0 
i2c_algo_bit           13564  1 i915
dcdbas                 14936  1 dell_laptop
cfg80211              499466  3 ath9k,mac80211,ath
snd                    73753  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    78537  1 mei_me
bluetooth             391726  25 rfcomm,bnep,ath3k,btusb
psmouse               104093  0 
soundcore              12680  1 snd
mac_hid                13253  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
serio_raw              13413  0 
video                  19574  1 i915
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  2 hid_generic,usbhid
r8169                  73299  0 
ahci                   30063  1 
mii                    13981  3 ax88179_178a,usbnet,r8169
libahci                32118  1 ahci
```

ping -c4 google.com
```
PING google.com (173.194.37.104) 56(84) bytes of data.
64 bytes from mia05s17-in-f8.1e100.net (173.194.37.104): icmp_req=1 ttl=56 time=62.8 ms
64 bytes from mia05s17-in-f8.1e100.net (173.194.37.104): icmp_req=2 ttl=56 time=80.0 ms
64 bytes from mia05s17-in-f8.1e100.net (173.194.37.104): icmp_req=3 ttl=56 time=64.1 ms
64 bytes from mia05s17-in-f8.1e100.net (173.194.37.104): icmp_req=4 ttl=56 time=62.5 ms


```

---

### Post by varunendra on 2014-04-13
Doesn't look like complete output of the commands, and the posted part of "ifconfig" is also not in line with the output of nm-tool (nm-tool is showing eth1 as connected, ifconfig is not).

Please post the complete outputs of the commands, run at the same time (when the usb adapter is connected and working).

**PS:**
Unless the adapter connects to a USB3 interface in USB 3 mode, you won't get gigabit speeds anyway, because the maximum theoretical speed of USB 2.0 is only 480 Mb/s. Practically, the data transfer speed on USB 2.0 goes about 360-380 Mb/s.

---

### Post by DXXPublic on 2014-04-13
Apologies let me re-do that.   The Adapter is connected to a USB3 (at least thats the port says). Im also adding an extract of the lsusb output, maybe im missing something.  thanks

ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr e0:db:55:b0:f4:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 8c:ae:4c:fd:21:8a  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8eae:4cff:fefd:218a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36790212 (36.7 MB)  TX bytes:27022876 (27.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:502982 (502.9 KB)  TX bytes:502982 (502.9 KB)

wlan0     Link encap:Ethernet  HWaddr 64:5a:04:80:7f:7c  
          inet6 addr: fe80::665a:4ff:fe80:7f7c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14784 (14.7 KB)  TX bytes:23171 (23.1 KB)


```

nm-tool
```
State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E0:DB:55:B0:F4:09

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        64:5A:04:80:7F:7C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    DXX:             Infra, C8:D3:A3:55:C8:02, Freq 2417 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    belkin.9c7:      Infra, 08:86:3B:94:E9:C7, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA2
    belkin.9c7.guests: Infra, 0A:86:3B:94:E9:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    DXXtended:       Infra, 00:1D:7E:E1:0D:32, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA2
    UP wifi:         Infra, 00:15:6D:B0:5C:DC, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    Inversiones2:    Infra, C8:D3:A3:67:D1:22, Freq 2422 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ax88179_178a
  State:             connected
  Default:           yes
  HW Address:        8C:AE:4C:FD:21:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1


```

modinfo ax88179_178a
```
filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/usb/ax88179_178a.ko
license:        GPL
description:    ASIX AX88179/178A based USB 3.0/2.0 Gigabit Ethernet Devices
srcversion:     EFC95C503DEFA5D6B2A8853
alias:          usb:v0DF6p0072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B95p178Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B95p1790d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbnet,mii
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions
```

lsmod
```
Module                  Size  Used by
usb_storage            66567  1 
rfcomm                 74718  12 
parport_pc             32866  0 
ppdev                  17711  0 
bnep                   24107  2 
snd_hda_codec_hdmi     41773  1 
snd_hda_codec_realtek    57219  1 
snd_hda_intel          57134  3 
snd_hda_codec         194817  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               82247  0 
arc4                   12573  2 
videobuf2_core         40815  1 uvcvideo
i915                  688399  3 
videodev              138562  2 uvcvideo,videobuf2_core
drm_kms_helper         53237  1 i915
ath9k                 162124  0 
snd_seq_midi           13324  0 
videobuf2_vmalloc      13216  1 uvcvideo
snd_rawmidi            30416  1 snd_seq_midi
rts5139               318185  0 
drm                   306660  4 i915,drm_kms_helper
ath3k                  13368  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
btusb                  28374  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              623607  1 ath9k
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
ax88179_178a           22488  0 
ath9k_common           13859  1 ath9k
bluetooth             391726  25 rfcomm,bnep,ath3k,btusb
ath9k_hw              457718  2 ath9k,ath9k_common
usbnet                 39575  1 ax88179_178a
psmouse               104093  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
dell_wmi               12761  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            17425  0 
wmi                    19256  1 dell_wmi
serio_raw              13413  0 
mei_me                 18418  0 
i2c_algo_bit           13564  1 i915
lpc_ich                21163  0 
cfg80211              499466  3 ath9k,mac80211,ath
mei                    78537  1 mei_me
snd                    73753  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17613  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
video                  19574  1 i915
dcdbas                 14936  1 dell_laptop
binfmt_misc            17508  1 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  2 hid_generic,usbhid
ahci                   30063  1 
libahci                32118  1 ahci
r8169                  73299  0 
mii                    13981  3 ax88179_178a,usbnet,r816
```

ping -c 4 google.com
```
PING google.com (201.227.61.35) 56(84) bytes of data.
64 bytes from 201.227.61.35: icmp_req=1 ttl=60 time=11.3 ms
64 bytes from 201.227.61.35: icmp_req=2 ttl=60 time=11.0 ms
64 bytes from 201.227.61.35: icmp_req=3 ttl=60 time=26.7 ms
64 bytes from 201.227.61.35: icmp_req=4 ttl=60 time=12.8 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 16273ms
rtt min/avg/max/mdev = 11.077/15.492/26.703/6.507 ms


```

lsusb -v  (only posting the part of the ASIX device)
```
Bus 004 Device 002: ID 0b95:1790 ASIX Electronics Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x0b95 ASIX Electronics Corp.
  idProduct          0x1790 
  bcdDevice            1.00
  iManufacturer           1 ASIX Elec. Corp.
  iProduct                2 AX88179
  iSerial                 3 008CAE4CFD218A
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           57
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              124mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol      0 
      iInterface              4 Network_Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              11
        bMaxBurst               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst               3
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
      Latency Tolerance Messages (LTM) Supported
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat           1 micro seconds
    bU2DevExitLat         101 micro seconds
Device Status:     0x000c
  (Bus Powered)
  Test Mode
```

---

### Post by varunendra on 2014-04-13
Everything looks good to me. There are no packet errors, so no problems 'during' packet transfers either.

Please try disabling IPv6 as per this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

A couple of other things you may try -

**1)** Try setting MTU value in Network Manager to 1492 or 1392.

**2)** If you are not going to use the inbuilt NIC, try disabling its driver so there are no chances of possible conflict over resources -
```
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by DXXPublic on 2014-04-13
Tried everthing and still getting the same thing. 12.0MB/s

---

### Post by varunendra on 2014-04-13
I think I am out of ideas then, but I'd like to see the full and exact outputs of the following before saying 'quits' :
```
lsusb
ifconfig -a
sudo lshw -C network
nm-tool
```

---

### Post by DXXPublic on 2014-04-13
Thanks for this man.

lsusb
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 045e:07b2 Microsoft Corp. 
Bus 004 Device 002: ID 0b95:1790 ASIX Electronics Corp. 
Bus 004 Device 003: ID 0bc2:2312 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 005: ID 0bda:58c2 Realtek Semiconductor Corp. 

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr e0:db:55:b0:f4:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 8c:ae:4c:fd:21:8a  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:90214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1101395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5931762 (5.9 MB)  TX bytes:1663458404 (1.6 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15147 (15.1 KB)  TX bytes:15147 (15.1 KB)

wlan0     Link encap:Ethernet  HWaddr 64:5a:04:80:7f:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23823 (23.8 KB)  TX bytes:9257 (9.2 KB)
```

sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 64:5a:04:80:7f:7c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-19-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: e0:db:55:b0:f4:09
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@4:1
       logical name: eth1
       serial: 8c:ae:4c:fd:21:8a
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=192.168.0.109 link=yes multicast=yes port=MII speed=1Gbit/s
```

nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E0:DB:55:B0:F4:09

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        64:5A:04:80:7F:7C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    DXX:             Infra, C8:D3:A3:55:C8:02, Freq 2417 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    belkin.9c7:      Infra, 08:86:3B:94:E9:C7, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2
    belkin.9c7.guests: Infra, 0A:86:3B:94:E9:C8, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    UP wifi:         Infra, 00:15:6D:B0:5C:DC, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    DXXtended:       Infra, 00:1D:7E:E1:0D:32, Freq 2417 MHz, Rate 54 Mb/s, Strength 54 WPA2
    COWiFi-35921678/0: Infra, 3C:75:4A:23:16:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WEP


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ax88179_178a
  State:             connected
  Default:           yes
  HW Address:        8C:AE:4C:FD:21:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
```

---

### Post by DXXPublic on 2014-04-15
Hi.

Anyone else have other idea i could try?

Thanks

---

### Post by varunendra on 2014-04-16
In your previous post, the lsusb output shows the USB3 hub being shared between the USB adapter and a Seagate external drive. Although generally it shouldn't matter, but just to make sure, could you please try without any other device connected to the USB 3 hub/port? The "lsusb" output should show only one device connected to **"Bus 004"** in that case *(Bus 004 Device 002..)*.

I have never seen or heard of this driver that your device is using, and apart from above, I still have no ideas about what maybe wrong (and no time to dig deeper). Let's hope this post works as a lucky bump for you and someone with better ideas notices it and joins us with their suggestions.

---

