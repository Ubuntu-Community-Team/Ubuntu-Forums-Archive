---
title: "Wireless conectivty issues. connection shows as still connected, but &quot;disconnects&quot;"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by spayed on 2011-03-29
Basically, what happens is, i can connect to my network just fine.  Within minutes (sometimes seconds!) I stop being able to connect to  anything, however my icon says I'm still connected just fine. Everything  is just dandy with an enthernet cable. My ISP is Shaw, and I use a  gateway box..thing rather than a modem that connects to a router which I  connect to. In order to "reconnect", all i have to do is just  disconnect and reconnect from the network. resetting the gateway box  doesn't help.

 THe laptop with this problem is a toshiba NB200.

So,  some time ago I installed Ubuntu 10.10 over my winXP install. I've  nearly always had this issue with wireless, but only at home and only  with this computer. I don't have this issue on any other network. I had  another computer also running ubuntu 10.10, which did not have this  problem. Nor did I have any problems when either computers ran XP or  Vista. My roommate who runs XP does not have this problem, either.

I really don't know if the problem is with my computer, the gateway box, or the ISP, So I'm not sure where to start.

---

### Post by wep940 on 2011-03-29
Do you know if you have the correct driver for your wireless card?  Is this an internal wireless adapter, or is this a USB or PCMCIA adapter?
 
Go to a terminal window (applications/accessories/terminal)
 
Type:
 
lshw -C network <press enter>
 
ifconfig <press enter>
 
iwconfig <press enter>
 
Post your answers to the opening questions, along with the outputs from the above 3 commands in a reply back here and we can go from there.

---

### Post by spayed on 2011-03-29
```
leviathan@leviathan:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:fb:52:58  
          inet6 addr: fe80::223:5aff:fefb:5258/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14968082 (14.9 MB)  TX bytes:1898945 (1.8 MB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26488 (26.4 KB)  TX bytes:26488 (26.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:9a:23:f1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe9a:23f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123387 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:221215388 (221.2 MB)  TX bytes:16455125 (16.4 MB)

leviathan@leviathan:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TARDIS"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:26:F3:0A:E0:40   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:08:9a:23:f1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:fb:52:58
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:44 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff
```


And it's internal. I dont know if it's the right driver, but it works elsewhere.

---

### Post by wep940 on 2011-03-29
Looks like the correct driver - ath9k.   I'd be lost trying to help you further, so I hope someone else has some ideas.
 
Best of luck!!

---

### Post by collisionystm on 2011-03-29
When you are connected with wireless, do an ifconfig in terminal.

If you have an 192.168.1.*** address for your wlan0 than your router most likely is 192.168.1.1

So just type ping 192.168.1.1, make sure you get replies. Minimize the terminal and surf the web...etc. when you have a connection problem, look back at the terminal and make sure you are still pinging the router. Let me know what happens.

---

### Post by collisionystm on 2011-03-29
woops didnt look at your capture, just type ping 192.168.0.1

---

### Post by spayed on 2011-03-30
```

64 bytes from 192.168.0.1: icmp_req=183 ttl=64 time=2.51 ms
64 bytes from 192.168.0.1: icmp_req=184 ttl=64 time=2.57 ms
64 bytes from 192.168.0.1: icmp_req=185 ttl=64 time=2.46 ms
64 bytes from 192.168.0.1: icmp_req=186 ttl=64 time=2.50 ms         // at this point temporarily stopped working
64 bytes from 192.168.0.1: icmp_req=268 ttl=64 time=1.72 ms            // reconnected on its own
64 bytes from 192.168.0.1: icmp_req=269 ttl=64 time=1.07 ms
64 bytes from 192.168.0.1: icmp_req=270 ttl=64 time=1.13 ms
64 bytes from 192.168.0.1: icmp_req=271 ttl=64 time=1.45 ms

--- 192.168.0.1 ping statistics --- // some time later
2143 packets transmitted, 1572 received, 26% packet loss, time 2147529ms
rtt min/avg/max/mdev = 1.076/4.825/1026.966/34.955 ms, pipe 2



64 bytes from 192.168.0.1: icmp_req=550 ttl=64 time=5.08 ms
64 bytes from 192.168.0.1: icmp_req=551 ttl=64 time=1.12 ms
64 bytes from 192.168.0.1: icmp_req=552 ttl=64 time=2.98 ms
64 bytes from 192.168.0.1: icmp_req=553 ttl=64 time=2.00 ms
64 bytes from 192.168.0.1: icmp_req=554 ttl=64 time=3.22 ms
64 bytes from 192.168.0.1: icmp_req=555 ttl=64 time=1.72 ms
64 bytes from 192.168.0.1: icmp_req=556 ttl=64 time=2.12 ms // pages stopped loading
ping: sendmsg: Network is unreachable                    //reconnecting to network
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.0.1: icmp_req=560 ttl=64 time=7.62 ms // connected again
64 bytes from 192.168.0.1: icmp_req=561 ttl=64 time=2.03 ms
64 bytes from 192.168.0.1: icmp_req=562 ttl=64 time=1.38 ms
64 bytes from 192.168.0.1: icmp_req=563 ttl=64 time=1.94 ms
64 bytes from 192.168.0.1: icmp_req=564 ttl=64 time=3.30 ms
64 bytes from 192.168.0.1: icmp_req=565 ttl=64 time=1.64 ms
64 bytes from 192.168.0.1: icmp_req=566 ttl=64 time=1.40 ms
64 bytes from 192.168.0.1: icmp_req=567 ttl=64 time=2.85 ms
64 bytes from 192.168.0.1: icmp_req=568 ttl=64 time=2.49 ms
64 bytes from 192.168.0.1: icmp_req=569 ttl=64 time=5.11 ms
64 bytes from 192.168.0.1: icmp_req=570 ttl=64 time=2.55 ms
^C
--- 192.168.0.1 ping statistics ---
570 packets transmitted, 404 received, 29% packet loss, time 570640ms
rtt min/avg/max/mdev = 1.080/2.983/61.910/4.236 ms



```

So, no pings when im "disconnected". sometimes it seems to "reconnect" itself. Basically, pages just take longer to load at this point. 
And I have a strange feeling that packet loss that high is .. not normal.

---

### Post by Hippytaff on 2011-03-30
The link in my sig to the wireless script might shed some light on the issue if you want to download and run it.

---

### Post by spayed on 2011-04-02
k, results from wireless script.
Sorry that took a while - problem dissappeared mysteriosly for a few days (... it's done that before)

```

Version: 1.1
Sat Apr 2 03:10:36 MDT 2011

************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

************************************
        Kernel
************************************

Linux leviathan 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

************************************
        pci wireless devices
************************************

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Accton Technology Corporation Device [1113:e811]
    Kernel driver in use: ath9k
    Kernel modules: ath9k

************************************
        usb wireless devices
************************************


************************************
        List of network devices
************************************

  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:08:9a:23:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:fb:52:58
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

************************************
          List of drivers
************************************

Module                  Size  Used by
usblp                  10651  0 
usbhid                 36882  0 
hid                    67742  1 usbhid
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
rfcomm                 33811  4 
parport_pc             26058  0 
ppdev                   5556  0 
sco                     7998  2 
bnep                    9542  2 
snd_hda_codec_realtek   218492  1 
l2cap                  37008  16 rfcomm,bnep
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22235  2 
ath9k                  88884  0 
btusb                  10969  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
snd_hwdep               5040  1 snd_hda_codec
ath9k_common            5982  1 ath9k
i915                  295435  4 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ath9k_hw              292329  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
drm_kms_helper         30200  1 i915
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231959  2 ath9k,ath9k_common
drm                   168060  4 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59033  0 
uvcvideo               55847  0 
toshiba_bluetooth       1723  0 
cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211
intel_agp              26566  2 i915
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
videodev               43098  1 uvcvideo
soundcore                880  1 snd
v4l1_compat            13359  2 uvcvideo,videodev
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
coretemp                5326  0 
led_class               2633  1 ath9k
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
r8169                  36521  0 
mii                     4425  1 r8169

************************************
           network info
************************************

eth0      Link encap:Ethernet  HWaddr 00:23:5a:fb:52:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104720 (104.7 KB)  TX bytes:104720 (104.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:9a:23:f1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe9a:23f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:552379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:555450338 (555.4 MB)  TX bytes:75237973 (75.2 MB)


************************************
 Wireless specific network info
************************************

wlan0     IEEE 802.11bgn  ESSID:"TARDIS"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:26:F3:0A:E0:40   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

************************************
 Rfkill Blocks
************************************

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
8: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

************************************

*************************************************************************
interfaces
*************************************************************************
auto lo
iface lo inet loopback


**************************************************************************
resolv.conf
**************************************************************************
# Generated by NetworkManager
nameserver 192.168.0.1

**************************************************************************
Modules file
**************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Sun Jan  9 17:10:36 2011
# Chip drivers
coretemp

*************************************************************************
Blacklist file
*************************************************************************
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

**************************************************************************
Files in folder /etc/modprobe.d/*
**************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf

***************************************************************************
Route info
***************************************************************************
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

******************************************************************************
Using nm-tool
******************************************************************************

NetworkManager Tool

State: connected

- Device: wlan0  [Auto TARDIS] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        00:23:08:9A:23:F1

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TRENDnet:        Infra, 00:14:D1:45:61:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    honzky@home:     Infra, 00:13:46:41:E0:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    dlink:           Infra, 00:24:01:D0:05:99, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA
    TELUS2861:       Infra, 00:26:B8:F1:4D:04, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    Telus:           Infra, 00:26:B8:EE:B9:54, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Route Boxxx:     Infra, 00:25:9C:0A:BD:B3, Freq 2452 MHz, Rate 54 Mb/s, Strength 31 WPA2
    TELUS2597:       Infra, 00:26:B8:F0:E9:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    Thompson Network:Infra, 00:11:95:07:C5:BE, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    C3DFFD:          Infra, 00:26:F3:C3:E0:00, Freq 2442 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    *TARDIS:         Infra, 00:26:F3:0A:E0:40, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    linksys:         Infra, 00:1E:E5:04:6C:F6, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    SNORTH:          Infra, 04:05:37:7C:C2:64, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WEP
    Rob's Savage Network: Infra, 00:1F:F3:07:20:C3, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WEP
    TELUS7240:       Infra, 00:26:B8:F0:C0:44, Freq 2412 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    Bert:            Infra, 00:25:9C:2E:B4:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    T&A:             Infra, 1C:6D:1C:E8:60:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    TELUS5147:       Infra, 00:26:B8:F1:FF:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    dlink:           Infra, 00:17:9A:36:27:52, Freq 2412 MHz, Rate 54 Mb/s, Strength 62
    casaloca:        Infra, 00:13:46:88:53:96, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
    Kla:             Infra, 00:17:3F:BD:8E:D4, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    Thompson:        Infra, 00:26:88:E5:ED:58, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Rob's Savage Network: Infra, 00:1F:F3:07:20:C3, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Rabbmans World:  Infra, 00:23:69:DE:F2:22, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    samour:          Infra, 00:25:9C:02:E0:2F, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    SAKK Wireless D-Link: Infra, 00:1B:11:EC:AD:72, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    E0DAD5:          Infra, 00:22:2D:E0:DA:D8, Freq 2457 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    UNICORN:         Infra, 00:25:9C:2C:8E:AC, Freq 2452 MHz, Rate 54 Mb/s, Strength 42 WPA2
    RAYSHON:         Infra, 00:21:27:F0:8C:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    cooperz:         Infra, E8:BE:81:F9:0E:B0, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA
    191E55:          Infra, 00:26:F3:19:1E:58, Freq 2427 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:23:5A:FB:52:58

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off



******************************************************************************
Using iwlist scan
******************************************************************************
wlan0     Scan completed :
          Cell 01 - Address: 00:26:F3:0A:E0:41
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=000002846dc14c13
                    Extra: Last beacon: 620ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1604050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020025127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3404050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 02 - Address: 00:26:F3:0A:E0:42
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=000002846dbfc68e
                    Extra: Last beacon: 720ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1604050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020025127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3404050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: 00:26:F3:0A:E0:43
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=000002846dbfd107
                    Extra: Last beacon: 716ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1604050700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020025127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3404050700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 04 - Address: 00:26:F3:19:1E:58
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"191E55"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000412b4323153
                    Extra: Last beacon: 676ms ago
                    IE: Unknown: 0006313931453535
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1604000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010026127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3404000600000000000000000000000000000000000000
          Cell 05 - Address: 00:26:F3:0A:E0:40
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"TARDIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002846dca254b
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0006544152444953
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1604050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020026127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3404050700000000000000000000000000000000000000
          Cell 06 - Address: 00:21:27:F0:8C:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"RAYSHON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b633a3bb5
                    Extra: Last beacon: 568ms ago
                    IE: Unknown: 000752415953484F4E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:25:9C:2C:8E:AC
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UNICORN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ce5b3c4a
                    Extra: Last beacon: 424ms ago
                    IE: Unknown: 0007554E49434F524E
                    IE: Unknown: 010882848B968C9298A4
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B0C8E0EC
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259C2C8EAC1021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303010420001301054000800060050F20400011011000757525435344732100800020084103C000103
          Cell 08 - Address: 00:17:3F:BD:8E:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Kla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002552e859177
                    Extra: Last beacon: 216ms ago
                    IE: Unknown: 00034B6C61
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 09 - Address: 00:17:9A:36:27:52
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005bd4822181
                    Extra: Last beacon: 1108ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F01010006FF7F
                    IE: Unknown: DD0C00037F020101090002A44000
          Cell 10 - Address: 00:23:69:DE:F2:22
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Rabbmans World"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bd6da7d80
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 000E526162626D616E7320576F726C64
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010002369FFFFFFDEFFFFFFF223000000001021001C4C696E6B7379732C2041204469766973696F6E206F6620436973636F102300075752543430304E102400075752543430304E1042000C4D554A30304A3530393135351054000800060050F2040001101100075752543430304E100800020086103C000103
          Cell 11 - Address: 1C:6D:1C:E8:60:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"T&A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000de50cc9007
                    Extra: Last beacon: 668ms ago
                    IE: Unknown: 0003542641
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:13:46:88:53:96
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"casaloca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001fc54125d
                    Extra: Last beacon: 584ms ago
                    IE: Unknown: 0008636173616C6F6361
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000
          Cell 13 - Address: E8:BE:81:F9:0E:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"cooperz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009f1b415e
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 0007636F6F7065727A
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: 00:1F:F3:07:20:C3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Rob's Savage Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005ee42c18177
                    Extra: Last beacon: 264ms ago
                    IE: Unknown: 0014526F62277320536176616765204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C4017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001100000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120
                    IE: Unknown: DD070017F203020180
          Cell 15 - Address: 00:26:B8:F0:C0:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"TELUS7240"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002621705e82a
                    Extra: Last beacon: 1188ms ago
                    IE: Unknown: 000954454C555337323430
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B0001031047001048038EAF89B622085E858A0C677E0BFB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000751313030304150100800020088
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000
          Cell 16 - Address: 00:26:B8:F1:FF:B4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TELUS5147"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000177f7a99187
                    Extra: Last beacon: 1176ms ago
                    IE: Unknown: 000954454C555335313437
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081100000000000000000000000000000000000000
          Cell 17 - Address: 00:24:01:74:E0:21
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"lats"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000abf2a73c2
                    Extra: Last beacon: 1164ms ago
                    IE: Unknown: 00046C617473
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD270050F204104A000110104400010210470010565AA94967C14C0EAA8FF349E6F59311103C000101
          Cell 18 - Address: 00:25:9C:02:E0:2F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"samour"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ab4fd314
                    Extra: Last beacon: 588ms ago
                    IE: Unknown: 000673616D6F7572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 070C55532001021B0307140A021B
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B000103104700100000000000000001100000259C02E02F102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30311042000A4A3933323036383631391054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
          Cell 19 - Address: 00:26:F3:C3:E0:00
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"C3DFFD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=00000099f1f60fc6
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 0006433344464644
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000024127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 20 - Address: 00:26:F3:C3:E0:01
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=00000099f1f61a6f
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000024127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 21 - Address: 00:26:F3:C3:E0:02
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=00000099f1f624e8
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000024127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 22 - Address: 00:26:F3:C3:E0:03
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=00000099f1f62f62
                    Extra: Last beacon: 544ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000024127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 23 - Address: 00:1B:11:EC:AD:72
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SAKK Wireless D-Link"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ac877c3180
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 001453414B4B20576972656C65737320442D4C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B07070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A6E101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160B07010000000F000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102


********************************************************************************
Checking connectivity
********************************************************************************


*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=32.3 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.95 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.00 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.956/12.094/32.320/14.301 ms
sucessfully pinged 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=32.3 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.95 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.00 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.956/12.094/32.320/14.301 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=80.0 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=80.0 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=71.0 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 71.058/77.060/80.092/4.244 ms
sucessfully pinged 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=80.0 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=80.0 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=71.0 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 71.058/77.060/80.092/4.244 ms

*************************************************************************
nslookup test
*************************************************************************
sucessfully looked up www.google.com
Server: 192.168.0.1 Address: 192.168.0.1#53 Non-authoritative answer: www.google.com canonical name = www.l.google.com. Name: www.l.google.com Address: 74.125.225.18 Name: www.l.google.com Address: 74.125.225.16 Name: www.l.google.com Address: 74.125.225.20 Name: www.l.google.com Address: 74.125.225.19 Name: www.l.google.com Address: 74.125.225.17

*******************************************************************************
wget test
*******************************************************************************
sucessfully retrieved file www.google.com


*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.03 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.41 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=1.53 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.416/1.662/2.038/0.273 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=81.0 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=85.3 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=88.8 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 81.036/85.074/88.841/3.192 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=14.2 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.50 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=8.11 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 402ms rtt min/avg/max/mdev = 2.505/8.305/14.293/4.814 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=71.8 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=77.4 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=79.9 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 71.835/76.431/79.985/3.407 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=3.76 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.37 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.52 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 402ms rtt min/avg/max/mdev = 1.376/2.555/3.766/0.977 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=70.0 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=72.6 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=71.7 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 400ms rtt min/avg/max/mdev = 70.056/71.486/72.621/1.089 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.50 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.60 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.51 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 402ms rtt min/avg/max/mdev = 2.503/2.540/2.606/0.074 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=70.3 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=71.3 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=72.3 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 70.394/71.361/72.355/0.858 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.69 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.88 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.60 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 2.604/2.727/2.889/0.133 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=72.0 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=91.4 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=72.0 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 72.060/78.540/91.461/9.136 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.39 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.47 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.76 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.397/2.212/2.767/0.591 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=72.0 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=70.3 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=73.6 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 70.307/72.003/73.691/1.381 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.88 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.57 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.60 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 2.571/2.686/2.884/0.152 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=72.1 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=77.7 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=71.6 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 71.687/73.858/77.748/2.774 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.51 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.63 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.57 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 402ms rtt min/avg/max/mdev = 2.517/2.573/2.630/0.062 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=76.8 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=97.1 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=71.1 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 400ms rtt min/avg/max/mdev = 71.158/81.711/97.153/11.165 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.45 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.37 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=1.39 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.379/1.411/1.457/0.045 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=70.1 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=86.2 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=91.9 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 70.174/82.792/91.994/9.229 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.42 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.39 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=4.38 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 402ms rtt min/avg/max/mdev = 1.391/2.400/4.385/1.404 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=77.8 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=89.4 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=80.6 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 77.883/82.681/89.487/4.956 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=2.59 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=1.46 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=1.44 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.440/1.835/2.597/0.538 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=70.9 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=70.0 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=91.2 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 400ms rtt min/avg/max/mdev = 70.026/77.420/91.275/9.804 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************

*********************************************************************************
Ping test
*********************************************************************************
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=1.59 ms 64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.51 ms 64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=4.34 ms --- 192.168.0.1 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 1.592/2.817/4.345/1.144 ms

*********************************************************************************
Ping test
*********************************************************************************
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 64 bytes from 8.8.8.8: icmp_req=1 ttl=54 time=71.3 ms 64 bytes from 8.8.8.8: icmp_req=2 ttl=54 time=72.7 ms 64 bytes from 8.8.8.8: icmp_req=3 ttl=54 time=78.8 ms --- 8.8.8.8 ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 401ms rtt min/avg/max/mdev = 71.354/74.336/78.865/3.270 ms

*************************************************************************
nslookup test
*************************************************************************

*******************************************************************************
wget test
*******************************************************************************
_unsucessfully_ retrieved file www.google.com

******************************************************************************************
******************************************************************************************
Log file: /var/log/syslog
******************************************************************************************
******************************************************************************************

Apr  2 03:09:54 leviathan NetworkManager[772]: <info> dhclient started with pid 18709
Apr  2 03:09:54 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr  2 03:09:54 leviathan dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr  2 03:09:54 leviathan dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr  2 03:09:54 leviathan dhclient: All rights reserved.
Apr  2 03:09:54 leviathan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr  2 03:09:54 leviathan dhclient: 
Apr  2 03:09:55 leviathan NetworkManager[772]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  2 03:09:55 leviathan dhclient: Listening on LPF/wlan0/00:23:08:9a:23:f1
Apr  2 03:09:55 leviathan dhclient: Sending on   LPF/wlan0/00:23:08:9a:23:f1
Apr  2 03:09:55 leviathan dhclient: Sending on   Socket/fallback
Apr  2 03:09:55 leviathan dhclient: DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
Apr  2 03:10:02 leviathan dhclient: last message repeated 2 times
Apr  2 03:10:02 leviathan dhclient: DHCPACK of 192.168.0.100 from 192.168.0.1
Apr  2 03:10:02 leviathan dhclient: bound to 192.168.0.100 -- renewal in 292676 seconds.
Apr  2 03:10:02 leviathan NetworkManager[772]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  2 03:10:02 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  2 03:10:02 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  2 03:10:02 leviathan NetworkManager[772]: <info>   address 192.168.0.100
Apr  2 03:10:02 leviathan NetworkManager[772]: <info>   prefix 24 (255.255.255.0)
Apr  2 03:10:02 leviathan NetworkManager[772]: <info>   gateway 192.168.0.1
Apr  2 03:10:02 leviathan NetworkManager[772]: <info>   nameserver '192.168.0.1'
Apr  2 03:10:02 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr  2 03:10:02 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  2 03:10:02 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr  2 03:10:03 leviathan NetworkManager[772]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr  2 03:10:03 leviathan NetworkManager[772]: <info> Policy set 'Auto TARDIS' (wlan0) as default for IPv4 routing and DNS.
Apr  2 03:10:03 leviathan NetworkManager[772]: <info> Activation (wlan0) successful, device activated.
Apr  2 03:10:03 leviathan NetworkManager[772]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  2 03:10:06 leviathan ntpdate[18761]: adjust time server 91.189.94.4 offset -0.035309 sec

******************************************************************************************
******************************************************************************************
Log file: /var/log/messages
******************************************************************************************
******************************************************************************************

Apr  2 02:56:49 leviathan kernel: [116100.842606]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 02:56:49 leviathan kernel: [116100.842616]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 02:56:49 leviathan kernel: [116100.842625]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 02:56:49 leviathan kernel: [116100.842633]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 02:56:49 leviathan kernel: [116100.842642]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 02:56:49 leviathan kernel: [116100.842651]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:00:30 leviathan kernel: [116322.186410] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 03:00:31 leviathan kernel: [116322.998565] cfg80211: World regulatory domain updated:
Apr  2 03:00:31 leviathan kernel: [116322.998576]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 03:00:31 leviathan kernel: [116322.998586]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:00:31 leviathan kernel: [116322.998595]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:00:31 leviathan kernel: [116322.998604]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:00:31 leviathan kernel: [116322.998613]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:00:31 leviathan kernel: [116322.998622]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.373697] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 03:07:04 leviathan kernel: [116715.643583] cfg80211: World regulatory domain updated:
Apr  2 03:07:04 leviathan kernel: [116715.643591]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 03:07:04 leviathan kernel: [116715.643599]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643606]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643613]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643619]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643626]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:52 leviathan kernel: [116884.305712] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 03:09:53 leviathan kernel: [116884.410920] cfg80211: World regulatory domain updated:
Apr  2 03:09:53 leviathan kernel: [116884.410930]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 03:09:53 leviathan kernel: [116884.410941]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410950]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410959]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410968]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410977]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

******************************************************************************************
******************************************************************************************
Log file: /var/log/kern.log
******************************************************************************************
******************************************************************************************

Apr  2 03:07:04 leviathan kernel: [116715.373688] cfg80211: Restoring regulatory settings
Apr  2 03:07:04 leviathan kernel: [116715.373697] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 03:07:04 leviathan kernel: [116715.643583] cfg80211: World regulatory domain updated:
Apr  2 03:07:04 leviathan kernel: [116715.643591]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 03:07:04 leviathan kernel: [116715.643599]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643606]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643613]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643619]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:04 leviathan kernel: [116715.643626]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:07:05 leviathan kernel: [116716.960642] wlan0: authenticate with 00:26:f3:0a:e0:40 (try 1)
Apr  2 03:07:05 leviathan kernel: [116716.963086] wlan0: authenticated
Apr  2 03:07:05 leviathan kernel: [116716.963147] wlan0: associate with 00:26:f3:0a:e0:40 (try 1)
Apr  2 03:07:05 leviathan kernel: [116716.972479] wlan0: RX AssocResp from 00:26:f3:0a:e0:40 (capab=0x411 status=0 aid=2)
Apr  2 03:07:05 leviathan kernel: [116716.972491] wlan0: associated
Apr  2 03:09:52 leviathan kernel: [116884.285185] wlan0: deauthenticating from 00:26:f3:0a:e0:40 by local choice (reason=3)
Apr  2 03:09:52 leviathan kernel: [116884.305689] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr  2 03:09:52 leviathan kernel: [116884.305703] cfg80211: Restoring regulatory settings
Apr  2 03:09:52 leviathan kernel: [116884.305712] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 03:09:53 leviathan kernel: [116884.410920] cfg80211: World regulatory domain updated:
Apr  2 03:09:53 leviathan kernel: [116884.410930]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 03:09:53 leviathan kernel: [116884.410941]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410950]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410959]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410968]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:53 leviathan kernel: [116884.410977]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 03:09:54 leviathan kernel: [116885.975460] wlan0: authenticate with 00:26:f3:0a:e0:40 (try 1)
Apr  2 03:09:54 leviathan kernel: [116885.979751] wlan0: authenticated
Apr  2 03:09:54 leviathan kernel: [116885.979813] wlan0: associate with 00:26:f3:0a:e0:40 (try 1)
Apr  2 03:09:54 leviathan kernel: [116885.988993] wlan0: RX AssocResp from 00:26:f3:0a:e0:40 (capab=0x411 status=0 aid=2)
Apr  2 03:09:54 leviathan kernel: [116885.989005] wlan0: associated
failure

```

---

