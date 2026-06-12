---
title: "wifi keeps disconnecting: is it a matter of drivers?"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by Soonick on 2016-06-15
Similar to this discussion here [URL="http://ubuntuforums.org/showthread.php?t=2234954"]http://ubuntuforums.org/showthread.php?t=2234954
[/URL]my wifi keeps disconnecting, especially (but not only at all) if I suspend the session.
It seems to me that I do have the driver they suggest in the other discussion, and for my limited knowledge this is all I can thought of.
Also, I do not want to mess up with things and end up with a not working wifi at all...
Here is the output of lsmod:
```
:~$ lsmod
Module                  Size  Used by
ses                    17363  0 
enclosure              15368  1 ses
usb_storage            62209  1 
ctr                    13049  1 
ccm                    17773  1 
dm_crypt               23177  0 
cuse                   13445  3 
rfcomm                 69160  4 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
uvcvideo               80885  0 
acer_wmi               32522  0 
arc4                   12608  2 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
sparse_keymap          13948  1 acer_wmi
videodev              134688  2 uvcvideo,videobuf2_core
b43                   387371  0 
snd_hda_codec_realtek    65904  1 
snd_hda_intel          56611  3 
bcma                   52096  1 b43
snd_hda_codec         193017  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              638901  1 b43
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
cfg80211              496328  2 b43,mac80211
parport_pc             32701  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30731  1 snd_seq_midi
snd_seq                61616  2 snd_seq_midi_event,snd_seq_midi
ppdev                  17671  0 
joydev                 17381  0 
lp                     17759  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
dm_multipath           22873  0 
lpc_ich                21080  0 
serio_raw              13462  0 
snd_timer              29549  2 snd_pcm,snd_seq
snd                    69416  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
shpchp                 37032  0 
coretemp               13435  0 
scsi_dh                14882  1 dm_multipath
soundcore              12680  1 snd
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
mxm_wmi                13021  0 
i915                  788212  3 
psmouse               106692  0 
ahci                   34091  1 
i2c_algo_bit           13413  1 i915
drm_kms_helper         55071  1 i915
libahci                32716  1 ahci
atl1c                  46086  0 
drm                   303102  4 i915,drm_kms_helper
ssb                    62379  1 b43
wmi                    19177  2 acer_wmi,mxm_wmi
video                  19476  2 i915,acer_wmi


```

and of lspci:
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)


```

Any suggestions please??:KS

---

### Post by Soonick on 2016-06-28
Any other info requested to help the discussion?

---

### Post by Bucky Ball on 2016-06-28
How about the output of this:

> sudo lshw -C network

... followed by the output of the wirelessinfo script linked in red in my signature, please.

---

### Post by Soonick on 2016-06-28
Ok thanks! here they are
```
:~$ sudo lshw -C network
[sudo] password for nedu: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:94600000-94603fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:3d:3f:bf
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:93500000-9353ffff ioport:1000(size=128)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: f0:7b:cb:10:42:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-91-generic firmware=410.2160 ip=192.168.0.5 link=yes multicast=yes wireless=IEEE 802.11bg


```

And also (I think) this is what you asked from the wireless info script:
```
nedu@nedu:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> 
> chmod +x wireless-info && \
> ./wireless-info
--2016-06-28 13:16:19--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.252.129
Connecting to github.com (github.com)|192.30.252.129|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2016-06-28 13:16:20--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.12.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.12.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16122 (16K) [text/plain]
Saving to: ‘wireless-info’

100%[======================================>] 16,122      --.-K/s   in 0.02s   

Last-modified header missing -- time-stamps turned off.
2016-06-28 13:16:20 (815 KB/s) - ‘wireless-info’ saved [16122/16122]



Results saved in "/home/nedu/wireless-info.txt".

Results also archived in "/home/nedu/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

nedu@nedu:~$
```

---

### Post by Bucky Ball on 2016-06-28
At the bottom of the output of wirelessinfo script it tells you it has created the file "/home/nedu/wireless-info.txt".

If you go to /home/nedu you should see a new file called 'wireless-info.txt'. Copy paste contents of that between code tags, thanks.

But before you do that, looks like the wrong driver. You need lp-phy driver. [See here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"). You have the -bridge one installed.

```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

You may need to blacklist the one you have currently installed, b43-pci-bridge. I'm not fully au fait with doing that, so rather than give you the wrong information, hopefully someone can jump in that can give you the good oil.

---

### Post by Soonick on 2016-06-29
Here is the txt file content:
```

########## wireless info START ##########

Report from: 28 Jun 2016 13:16 CEST +0200

Booted last: 28 Jun 2016 15:09 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-91-generic #138-Ubuntu SMP Fri Jun 24 17:00:34 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, acpi_osi=Linux, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card [105b:e01b]
    Kernel driver in use: b43-pci-bridge

05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0212]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
b43                   387371  0 
bcma                   52096  1 b43
mac80211              638901  1 b43
cfg80211              496328  2 b43,mac80211
mxm_wmi                13021  0 
ssb                    62379  1 b43
wmi                    19177  2 acer_wmi,mxm_wmi
video                  19476  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          inet6 addr: 2a02:8070:898d:ca00:a04f:5b6c:ea29:1439/64 Scope:Global
          inet6 addr: 2a02:8070:898d:ca00:<IP6 'wlan0' [IF2]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6821063 (6.8 MB)  TX bytes:467846 (467.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UPC4833776"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'UPC4833776' [AC2]>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-16 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:147   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search local

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1038     1  0 13:09 ?        00:00:01 NetworkManager
root      1501  1038  0 13:09 ?        00:00:00 sh -c /sbin/resolvconf -a NetworkManager
root      1529  1503  0 13:09 ?        00:00:00 /bin/sh /etc/resolvconf/update.d/libc -a NetworkManager

##### NetworkManager info ###############

** (process:2654): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (process:2654): WARNING **: error: could not connect to NetworkManager

NetworkManager Tool

State: unknown

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto D-Link-e289758b-c8f9-474e-a60e-07fd51a5a51f]] (600 root)
[connection] id=Auto D-Link | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=D-Link
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Wi2premium]] (600 root)
[connection] id=Wi2premium | type=802-11-wireless
[802-11-wireless] ssid=Wi2premium | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Max-Planck IMPRS 3]] (600 root)
[connection] id=Max-Planck IMPRS 3 | type=802-11-wireless
[802-11-wireless] ssid=Max-Planck IMPRS 3 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Todtmoos]] (600 root)
[connection] id=Auto Todtmoos | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Todtmoos

[[/etc/NetworkManager/system-connections/Auto DLINK_WIRELESS]] (600 root)
[connection] id=Auto DLINK_WIRELESS | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=DLINK_WIRELESS

[[/etc/NetworkManager/system-connections/Auto HP8CBC11]] (600 root)
[connection] id=Auto HP8CBC11 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=HP8CBC11

[[/etc/NetworkManager/system-connections/UPC5857886]] (600 root)
[connection] id=UPC5857886 | type=802-11-wireless
[802-11-wireless] ssid=UPC5857886 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Alice-75116800]] (600 root)
[connection] id=Auto Alice-75116800 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-75116800

[[/etc/NetworkManager/system-connections/0001softbank]] (600 root)
[connection] id=0001softbank | type=802-11-wireless
[802-11-wireless] ssid=0001softbank | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Mybitch]] (600 root)
[connection] id=Mybitch | type=802-11-wireless
[802-11-wireless] ssid=Mybitch | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto InfostradaWiFi-e0a63997-fbbe-4bdd-ae90-196e82905931]] (600 root)
[connection] id=Auto InfostradaWiFi | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=InfostradaWiFi

[[/etc/NetworkManager/system-connections/Auto eminent]] (600 root)
[connection] id=Auto eminent | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=eminent

[[/etc/NetworkManager/system-connections/Auto InfostradaWiFi]] (600 root)
[connection] id=Auto InfostradaWiFi | type=802-11-wireless
[802-11-wireless] ssid=InfostradaWiFi
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/000740CDD107]] (600 root)
[connection] id=000740CDD107 | type=802-11-wireless
[802-11-wireless] ssid=000740CDD107 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto ALMAWIFI]] (600 root)
[connection] id=Auto ALMAWIFI | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=ALMAWIFI

[[/etc/NetworkManager/system-connections/Auto ALICE-WLAN43]] (600 root)
[connection] id=Auto ALICE-WLAN43 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=ALICE-WLAN43

[[/etc/NetworkManager/system-connections/000740CDD107 1]] (600 root)
[connection] id=000740CDD107 1 | type=802-11-wireless
[802-11-wireless] ssid=000740CDD107 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/tsdisee]] (600 root)
[connection] id=tsdisee | type=802-11-wireless
[802-11-wireless] ssid=tsdisee | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto WifiCasa]] (600 root)
[connection] id=Auto WifiCasa | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=WifiCasa

[[/etc/NetworkManager/system-connections/Air11]] (600 root)
[connection] id=Air11 | type=802-11-wireless
[802-11-wireless] ssid=Air11 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SWS1day]] (600 root)
[connection] id=SWS1day | type=802-11-wireless
[802-11-wireless] ssid=SWS1day | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto sapienza]] (600 root)
[connection] id=Auto sapienza | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=sapienza

[[/etc/NetworkManager/system-connections/Auto Alice-38104830]] (600 root)
[connection] id=Auto Alice-38104830 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-38104830

[[/etc/NetworkManager/system-connections/Mybitch_EXT 1]] (600 root)
[connection] id=Mybitch_EXT 1 | type=802-11-wireless
[802-11-wireless] ssid=Mybitch_EXT | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Haus Geyer]] (600 root)
[connection] id=Haus Geyer | type=802-11-wireless
[802-11-wireless] ssid=Haus Geyer | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Alice-65675342]] (600 root)
[connection] id=Auto Alice-65675342 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-65675342

[[/etc/NetworkManager/system-connections/ADSL_ZAMPA]] (600 root)
[connection] id=ADSL_ZAMPA | type=802-11-wireless
[802-11-wireless] ssid=ADSL_ZAMPA | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto FASTWEB-1-00036F9C840C]] (600 root)
[connection] id=Auto FASTWEB-1-00036F9C840C | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=FASTWEB-1-00036F9C840C

[[/etc/NetworkManager/system-connections/Auto FASTWEB-1-001CA2BFB554]] (600 root)
[connection] id=Auto FASTWEB-1-001CA2BFB554 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=FASTWEB-1-001CA2BFB554

[[/etc/NetworkManager/system-connections/Auto Alice-64647553]] (600 root)
[connection] id=Auto Alice-64647553 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-64647553

[[/etc/NetworkManager/system-connections/TNCAPB509F9]] (600 root)
[connection] id=TNCAPB509F9 | type=802-11-wireless
[802-11-wireless] ssid=TNCAPB509F9 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/I-know-who-you-are]] (600 root)
[connection] id=I-know-who-you-are | type=802-11-wireless
[802-11-wireless] ssid=I-know-who-you-are | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UPC3255855]] (600 root)
[connection] id=UPC3255855 | type=802-11-wireless
[802-11-wireless] ssid=UPC3255855 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Alice-37689116]] (600 root)
[connection] id=Auto Alice-37689116 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-37689116

[[/etc/NetworkManager/system-connections/Auto Alice-42913486]] (600 root)
[connection] id=Auto Alice-42913486 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-42913486

[[/etc/NetworkManager/system-connections/Auto wlan-ap]] (600 root)
[connection] id=Auto wlan-ap | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=wlan-ap

[[/etc/NetworkManager/system-connections/asj2014]] (600 root)
[connection] id=asj2014 | type=802-11-wireless
[802-11-wireless] ssid=asj2014 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto HP43C8F6]] (600 root)
[connection] id=Auto HP43C8F6 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=HP43C8F6

[[/etc/NetworkManager/system-connections/Ddr]] (600 root)
[connection] id=Ddr | type=802-11-wireless
[802-11-wireless] ssid=Ddr | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto ROBERTO-PC_Network_1]] (600 root)
[connection] id=Auto ROBERTO-PC_Network_1 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=ROBERTO-PC_Network_1

[[/etc/NetworkManager/system-connections/B-LINK-MP01]] (600 root)
[connection] id=B-LINK-MP01 | type=802-11-wireless
[802-11-wireless] ssid=B-LINK-MP01 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Max-Planck IMPRS 1]] (600 root)
[connection] id=Max-Planck IMPRS 1 | type=802-11-wireless
[802-11-wireless] ssid=Max-Planck IMPRS 1 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/shiencenterB]] (600 root)
[connection] id=shiencenterB | type=802-11-wireless
[802-11-wireless] ssid=shiencenterB | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box 7412]] (600 root)
[connection] id=FRITZ!Box 7412 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7412 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cisco NT-ospite]] (600 root)
[connection] id=Cisco NT-ospite | type=802-11-wireless
[802-11-wireless] ssid=Cisco NT-ospite | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WebPocket. 21.6-28D6]] (600 root)
[connection] id=WebPocket. 21.6-28D6 | type=802-11-wireless
[802-11-wireless] ssid=WebPocket. 21.6-28D6 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto FASTWEB-1-38229DF7B4D4]] (600 root)
[connection] id=Auto FASTWEB-1-38229DF7B4D4 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=FASTWEB-1-38229DF7B4D4

[[/etc/NetworkManager/system-connections/Auto WLAN-D91703]] (600 root)
[connection] id=Auto WLAN-D91703 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=WLAN-D91703

[[/etc/NetworkManager/system-connections/Lange Gasse WG 1]] (600 root)
[connection] id=Lange Gasse WG 1 | type=802-11-wireless
[802-11-wireless] ssid=Lange Gasse WG | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto milou]] (600 root)
[connection] id=Auto milou | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=milou

[[/etc/NetworkManager/system-connections/Auto Control_Wireless_Net_Area]] (600 root)
[connection] id=Auto Control_Wireless_Net_Area | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Control_Wireless_Net_Area

[[/etc/NetworkManager/system-connections/Guest]] (600 root)
[connection] id=Guest | type=802-11-wireless
[802-11-wireless] ssid=Guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto USR9111]] (600 root)
[connection] id=Auto USR9111 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=USR9111

[[/etc/NetworkManager/system-connections/HOTSPOT]] (600 root)
[connection] id=HOTSPOT | type=802-11-wireless
[802-11-wireless] ssid=HOTSPOT | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto TISCALI]] (600 root)
[connection] id=Auto TISCALI | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=TISCALI

[[/etc/NetworkManager/system-connections/Auto WLAN-1E9D44]] (600 root)
[connection] id=Auto WLAN-1E9D44 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=WLAN-1E9D44

[[/etc/NetworkManager/system-connections/IESC AP 6]] (600 root)
[connection] id=IESC AP 6 | type=802-11-wireless
[802-11-wireless] ssid=IESC AP 6 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto TNCAPB602B9]] (600 root)
[connection] id=Auto TNCAPB602B9 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=TNCAPB602B9

[[/etc/NetworkManager/system-connections/Auto Sitecom4A1D57]] (600 root)
[connection] id=Auto Sitecom4A1D57 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Sitecom4A1D57

[[/etc/NetworkManager/system-connections/Auto WiGateEST]] (600 root)
[connection] id=Auto WiGateEST | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=WiGateEST

[[/etc/NetworkManager/system-connections/Auto D-Link-f30fba5f-8aed-4854-9b2f-b8633e9e89cf]] (600 root)
[connection] id=Auto D-Link | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=D-Link

[[/etc/NetworkManager/system-connections/000A79F2EB69]] (600 root)
[connection] id=000A79F2EB69 | type=802-11-wireless
[802-11-wireless] ssid=000A79F2EB69 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto BELWUE]] (600 root)
[connection] id=Auto BELWUE | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=BELWUE

[[/etc/NetworkManager/system-connections/UFFICIO_M&F]] (600 root)
[connection] id=UFFICIO_M&F | type=802-11-wireless
[802-11-wireless] ssid=UFFICIO_M&F | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto hpsetup]] (600 root)
[connection] id=Auto hpsetup | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=hpsetup

[[/etc/NetworkManager/system-connections/UPC4833776]] (600 root)
[connection] id=UPC4833776 | type=802-11-wireless
[802-11-wireless] ssid=UPC4833776 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Max-Planck IMPRS 2]] (600 root)
[connection] id=Max-Planck IMPRS 2 | type=802-11-wireless
[802-11-wireless] ssid=Max-Planck IMPRS 2 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/mycloud]] (600 root)
[connection] id=mycloud | type=802-11-wireless
[802-11-wireless] ssid=mycloud | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/wlan55]] (600 root)
[connection] id=wlan55 | type=802-11-wireless
[802-11-wireless] ssid=wlan55 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto DLINK_WIRELESS-16eff49d-353a-4a98-9f81-e31459abd16e]] (600 root)
[connection] id=Auto DLINK_WIRELESS | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=DLINK_WIRELESS

[[/etc/NetworkManager/system-connections/Lina09]] (600 root)
[connection] id=Lina09 | type=802-11-wireless
[802-11-wireless] ssid=Lina09 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto FASTWEB-1-001CA2C94B04]] (600 root)
[connection] id=Auto FASTWEB-1-001CA2C94B04 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=FASTWEB-1-001CA2C94B04

[[/etc/NetworkManager/system-connections/ICH-Guest]] (600 root)
[connection] id=ICH-Guest | type=802-11-wireless
[802-11-wireless] ssid=ICH-Guest | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-11209641]] (600 root)
[connection] id=Vodafone-11209641 | type=802-11-wireless
[802-11-wireless] ssid=Vodafone-11209641 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BUFFALO-2F3E60_G]] (600 root)
[connection] id=BUFFALO-2F3E60_G | type=802-11-wireless
[802-11-wireless] ssid=BUFFALO-2F3E60_G | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Boingo Hotspot]] (600 root)
[connection] id=Boingo Hotspot | type=802-11-wireless
[802-11-wireless] ssid=Boingo Hotspot | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/logitec67]] (600 root)
[connection] id=logitec67 | type=802-11-wireless
[802-11-wireless] ssid=logitec67 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEDIACOM]] (600 root)
[connection] id=MEDIACOM | type=802-11-wireless
[802-11-wireless] ssid=MEDIACOM | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WebPocket-0fc0]] (600 root)
[connection] id=WebPocket-0fc0 | type=802-11-wireless
[802-11-wireless] ssid=WebPocket-0fc0 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto WiGateSUD]] (600 root)
[connection] id=Auto WiGateSUD | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=WiGateSUD

[[/etc/NetworkManager/system-connections/IESC_EXT2]] (600 root)
[connection] id=IESC_EXT2 | type=802-11-wireless
[802-11-wireless] ssid=IESC_EXT2 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WebPocket. 21.6-28D6 1]] (600 root)
[connection] id=WebPocket. 21.6-28D6 1 | type=802-11-wireless
[802-11-wireless] ssid=WebPocket. 21.6-28D6 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto essi]] (600 root)
[connection] id=Auto essi | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=essi

[[/etc/NetworkManager/system-connections/Auto wimove]] (600 root)
[connection] id=Auto wimove | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=wimove

[[/etc/NetworkManager/system-connections/Mybitch_EXT]] (600 root)
[connection] id=Mybitch_EXT | type=802-11-wireless
[802-11-wireless] ssid=Mybitch_EXT | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/swisscom]] (600 root)
[connection] id=swisscom | type=802-11-wireless
[802-11-wireless] ssid=swisscom | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Lange Gasse WG]] (600 root)
[connection] id=Lange Gasse WG | type=802-11-wireless
[802-11-wireless] ssid=Lange Gasse WG | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto D-Link]] (600 root)
[connection] id=Auto D-Link | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=D-Link

[[/etc/NetworkManager/system-connections/CITEU]] (600 root)
[connection] id=CITEU | type=802-11-wireless
[802-11-wireless] ssid=CITEU | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto FRITZ!Box Fon WLAN 7270]] (600 root)
[connection] id=Auto FRITZ!Box Fon WLAN 7270 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7270

[[/etc/NetworkManager/system-connections/Auto WiFi Frecciarossa]] (600 root)
[connection] id=Auto WiFi Frecciarossa | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=WiFi Frecciarossa

[[/etc/NetworkManager/system-connections/Auto linksys]] (600 root)
[connection] id=Auto linksys | type=802-11-wireless | permissions=user:nedu:; | autoconnect=false
[802-11-wireless] ssid=linksys

[[/etc/NetworkManager/system-connections/Ayon76]] (600 root)
[connection] id=Ayon76 | type=802-11-wireless
[802-11-wireless] ssid=Ayon76 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto Guest]] (600 root)
[connection] id=Auto Guest | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Guest

[[/etc/NetworkManager/system-connections/Mybitch 1]] (600 root)
[connection] id=Mybitch 1 | type=802-11-wireless
[802-11-wireless] ssid=Mybitch | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WLAN-D91703]] (600 root)
[connection] id=WLAN-D91703 | type=802-11-wireless
[802-11-wireless] ssid=WLAN-D91703 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto NETSTARTINFORMATICA0961725623]] (600 root)
[connection] id=Auto NETSTARTINFORMATICA0961725623 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=NETSTARTINFORMATICA0961725623

[[/etc/NetworkManager/system-connections/IESC_EXT3]] (600 root)
[connection] id=IESC_EXT3 | type=802-11-wireless
[802-11-wireless] ssid=IESC_EXT3 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto MATTEO-PC-Wireless]] (600 root)
[connection] id=Auto MATTEO-PC-Wireless | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=MATTEO-PC-Wireless

[[/etc/NetworkManager/system-connections/maxipi]] (600 root)
[connection] id=maxipi | type=802-11-wireless
[802-11-wireless] ssid=maxipi | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto ONAIR]] (600 root)
[connection] id=Auto ONAIR | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=ONAIR

[[/etc/NetworkManager/system-connections/Auto Alice-46037303]] (600 root)
[connection] id=Auto Alice-46037303 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Alice-46037303

[[/etc/NetworkManager/system-connections/UNIGE]] (600 root)
[connection] id=UNIGE | type=802-11-wireless
[802-11-wireless] ssid=UNIGE | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/iPhone di NEDU]] (600 root)
[connection] id=iPhone di NEDU | type=802-11-wireless
[802-11-wireless] ssid=iPhone di NEDU | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto HAS_CLOUD]] (600 root)
[connection] id=Auto HAS_CLOUD | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=HAS_CLOUD

[[/etc/NetworkManager/system-connections/Auto Snippysnappy]] (600 root)
[connection] id=Auto Snippysnappy | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=Snippysnappy

[[/etc/NetworkManager/system-connections/Auto FASTWEB-1-00036FD381B0]] (600 root)
[connection] id=Auto FASTWEB-1-00036FD381B0 | type=802-11-wireless | permissions=user:nedu:;
[802-11-wireless] ssid=FASTWEB-1-00036FD381B0

[[/etc/NetworkManager/system-connections/toyoko-inn.com]] (600 root)
[connection] id=toyoko-inn.com | type=802-11-wireless
[802-11-wireless] ssid=toyoko-inn.com | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC5630885]] (600 root)
[connection] id=UPC5630885 | type=802-11-wireless
[802-11-wireless] ssid=UPC5630885 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-21025739]] (600 root)
[connection] id=Vodafone-21025739 | type=802-11-wireless
[802-11-wireless] ssid=Vodafone-21025739 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Mybitch 2]] (600 root)
[connection] id=Mybitch 2 | type=802-11-wireless
[802-11-wireless] ssid=Mybitch | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

country NL:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5330 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'UPC5630885' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"UPC5630885"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000100d7862c3
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC4833776' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-13 dBm  
                    Encryption key:on
                    ESSID:"UPC4833776"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014ef7d040ba
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FRITZ!Box 7412' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7412"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000028b3ceb87b6
                    Extra: Last beacon: 852ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'WLAN-490279' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"WLAN-490279"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000292b8525fcd
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Strickstube' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Strickstube"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002492652b21
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/3.13.0-91-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-91-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:F6:1D:6D:82:8D:37:AE:8D:46:13:25:C8:49:8A:1C:3E:5E:66:C4
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-91-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-91-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:F6:1D:6D:82:8D:37:AE:8D:46:13:25:C8:49:8A:1C:3E:5E:66:C4
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-91-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-91-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:F6:1D:6D:82:8D:37:AE:8D:46:13:25:C8:49:8A:1C:3E:5E:66:C4
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-91-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-91-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:F6:1D:6D:82:8D:37:AE:8D:46:13:25:C8:49:8A:1C:3E:5E:66:C4
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-91-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-91-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:F6:1D:6D:82:8D:37:AE:8D:46:13:25:C8:49:8A:1C:3E:5E:66:C4
sig_hashalgo:   sha512

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=1

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

echo 70 > /sys/class/backlight/intel_backlight/brightness

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_wireless_sleep] (755 root)
    case "$1" in
    suspend|hibernate)
    /sbin/rmmod b43
    ;;
    resume|thaw)
    /sbin/rmmod b43
    /sbin/modprobe b43
    ;;
    esac
    exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x0bb4:0x0b12 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x12d1:0x14ac (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

##### dmesg #############################

[   32.790895] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   32.832484] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   42.524272] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   48.137132] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   48.253417] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   49.457314] wlan0: authenticate with <MAC 'UPC4833776' [AC2]>
[   49.468674] wlan0: send auth to <MAC 'UPC4833776' [AC2]> (try 1/3)
[   49.472982] wlan0: authenticated
[   49.476271] wlan0: associate with <MAC 'UPC4833776' [AC2]> (try 1/3)
[   49.479310] wlan0: RX AssocResp from <MAC 'UPC4833776' [AC2]> (capab=0x411 status=0 aid=2)
[   49.480057] wlan0: associated
[   49.480111] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

The suggested pckage is not available:
```
:~$ sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firmware-b43-lpphy-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firmware-b43-installer

E: Package 'firmware-b43-lpphy-installer' has no installation candidate
```
And therefore I have installed [B]firmware-b43-installer.


[/B]

---

### Post by praseodym on 2016-06-29
Deactivate IPv6 in the networking settings. Reconnect

---

### Post by Soonick on 2016-06-29
> **praseodym said:**
> Deactivate IPv6 in the networking settings. Reconnect

Sorry, this is to do what?
And by "deactivate" you mean put to "**ignore**"?

---

### Post by Bucky Ball on 2016-06-30
> **Soonick said:**
> 
And by "deactivate" you mean put to "**ignore**"?

Yes.

---

