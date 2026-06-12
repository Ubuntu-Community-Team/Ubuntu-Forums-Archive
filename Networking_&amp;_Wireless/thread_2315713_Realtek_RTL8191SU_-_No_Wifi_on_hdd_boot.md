---
title: "Realtek RTL8191SU - No Wifi on hdd boot"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by txcrittr on 2016-03-01
I've read several threads, none marked solved.  

Asus Z97-A mothertboard
32 Gb DDR3
250 GB Samsung 850 EVO
Windows 7 Pro
Ubuntu 15.10
Realtek RTL8191SU USB wireless adapter

!!!  Ubuntu Noob   !!!

When I boot from the "live CD" via usb thumb drive, the adapter is recognized and started.  I just put in the password and I'm connected.
HOWEVER!!!  When I boot from the ssd, 

:~$ sudo lshw -c network
  *-network DISABLED      

No connectivity.  AND!!!

:~$ sudo service network-manager restart


:~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlx14d64d0eab8b
       serial: 14:d6:4d:0e:ab:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.16 multicast=yes wireless=IEEE 802.11bgn

Restarting network-manager corrects the problem.

This IS NOT a hardware problem, since restarting a SERVICE corrects the problem.  It is a timing or sequence issue.  Is there a way to delay the start of network-manager a few seconds? Or get it to try to restart every 30 seconds or so for 4 or 5 times?  I'm convinced that I'd not have to restart the service if it would wait a few seconds to try to start.

Have I missed a thread that solves this?

More complete output below.


********************************************
:~$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlx14d64d0eab8b
       serial: 14:d6:4d:0e:ab:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated



:~$ sudo service network-manager status
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-03-01 09:56:53 CST; 1min 50s ago
 Main PID: 659 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9492;&#9472;659 /usr/sbin/NetworkManager --no-daemon

Mar 01 09:56:55 ********** NetworkManager[659]: <error> [1456847815.760397] ....
Mar 01 09:56:55 ********** NetworkManager[659]: <info>  (wlan0): driver WEXT...d
Mar 01 09:56:55 ********** NetworkManager[659]: <warn>  (wlan0): failed to i...r
Mar 01 09:56:55 ********** NetworkManager[659]: <warn>  wlan0: factory faile...)
Mar 01 09:56:55 ********** NetworkManager[659]: (NetworkManager:659): GLib-G...n
Mar 01 09:56:55 ********** NetworkManager[659]: (NetworkManager:659): GLib-G....
Mar 01 09:56:55 ********** NetworkManager[659]: <info>  devices added (path:...)
Mar 01 09:56:55 ********** NetworkManager[659]: <info>  device added (path: ....
Mar 01 09:57:03 ********** NetworkManager[659]: <info>  WiFi hardware radio ...d
Mar 01 09:57:03 ********** NetworkManager[659]: <info>  WWAN hardware radio ...d
Hint: Some lines were ellipsized, use -l to show in full.


:~$ sudo service network-manager restart


:~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlx14d64d0eab8b
       serial: 14:d6:4d:0e:ab:8b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.16 multicast=yes wireless=IEEE 802.11bgn


:~$ sudo service network-manager status
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-03-01 09:59:40 CST; 28s ago
 Main PID: 1932 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9500;&#9472;1932 /usr/sbin/NetworkManager --no-daemon
           &#9500;&#9472;1938 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-he...
           &#9492;&#9472;1948 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hos...

Mar 01 09:59:53 ********** dnsmasq[1948]: started, version 2.75 cache disabled
Mar 01 09:59:53 ********** dnsmasq[1948]: compile time options: IPv6 GNU-get...y
Mar 01 09:59:53 ********** dnsmasq[1948]: DBus support enabled: connected to...s
Mar 01 09:59:53 ********** dnsmasq[1948]: warning: no upstream servers confi...d
Mar 01 09:59:53 ********** NetworkManager[1932]: <info>  (wlx14d64d0eab8b): ....
Mar 01 09:59:53 ********** NetworkManager[1932]: <warn>  dnsmasq appeared on...7
Mar 01 09:59:53 ********** NetworkManager[1932]: <info>  Writing DNS informa...f
Mar 01 09:59:53 ********** dnsmasq[1948]: setting upstream servers from DBus
Mar 01 09:59:53 ********** dnsmasq[1948]: using nameserver 209.18.47.61#53
Mar 01 09:59:53 ********** dnsmasq[1948]: using nameserver 209.18.47.62#53
Hint: Some lines were ellipsized, use -l to show in full.


:~$ lsusb
Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
Bus 001 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```
:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
cfg80211              548864  0
r8712u                180224  0
joydev                 20480  0
input_leds             16384  0
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
hid_microsoft          16384  0
hid_generic            16384  0
uas                    24576  0
usbhid                 49152  1
usb_storage            69632  2 uas
hid                   118784  5 hid_generic,hid_microsoft,usbhid,hid_logitech_dj,hid_logitech_hidpp
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
nvidia              11407360  41
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   512000  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hda_core           65536  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
serio_raw              16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                24576  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   356352  2 nvidia
soundcore              16384  1 snd
mei_me                 32768  0
mei                    98304  1 mei_me
shpchp                 36864  0
8250_fintek            16384  0
tpm_infineon           20480  0
wmi                    20480  2 mxm_wmi,asus_wmi
acpi_pad               20480  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
ahci                   36864  2
psmouse               126976  0
libahci                32768  1 ahci
video                  40960  1 asus_w
```

---

### Post by Bucky Ball on 2016-03-01
Can't help with your issue apart from saying it appears your network is not being brought up at boot, but can bump your thread by asking you to please use code tags for terminal/CLI output. Neater, space-saving, easier to read, keeps formatting ... 

Thanks. See the link in my signature for how. Good luck.

---

### Post by txcrittr on 2016-03-02
UPDATE!  Added "CODE TAGS".  Thanks Bucky Ball.
I've read several threads, none marked solved.

Asus Z97-A mothertboard
32 Gb DDR3
250 GB Samsung 850 EVO
Windows 7 Pro
Ubuntu 15.10
Realtek RTL8191SU USB wireless adapter

!!! Ubuntu Noob !!!

When I boot from the "live CD" via usb thumb drive, the adapter is recognized and started. I just put in the password and I'm connected.
HOWEVER!!! When I boot from the ssd,

```
:~$ sudo lshw -c network
*-network DISABLED
```

No connectivity. AND!!!

```
:~$ sudo service network-manager restart


:~$ sudo lshw -c network
*-network
description: Wireless interface
physical id: 1
bus info: usb@1:4
logical name: wlx14d64d0eab8b
serial: 14:d6:4d:0e:ab:8b
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=r8712u ip=192.168.0.16 multicast=yes wireless=IEEE 802.11bgn
```

Restarting network-manager corrects the problem.

This IS NOT a hardware problem, since restarting a SERVICE corrects the problem. It is a timing or sequence issue. Is there a way to delay the start of network-manager a few seconds? Or get it to try to restart every 30 seconds or so for 4 or 5 times? I'm convinced that I'd not have to restart the service if it would wait a few seconds to try to start.

Have I missed a thread that solves this?

More complete output below.

```
:~$ sudo lshw -c network
*-network DISABLED
description: Wireless interface
physical id: 1
bus info: usb@1:4
logical name: wlx14d64d0eab8b
serial: 14:d6:4d:0e:ab:8b
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated



:~$ sudo service network-manager status
&#9679; NetworkManager.service - Network Manager
Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
Active: active (running) since Tue 2016-03-01 09:56:53 CST; 1min 50s ago
Main PID: 659 (NetworkManager)
CGroup: /system.slice/NetworkManager.service
&#9492;&#9472;659 /usr/sbin/NetworkManager --no-daemon

Mar 01 09:56:55 ********** NetworkManager[659]: <error> [1456847815.760397] ....
Mar 01 09:56:55 ********** NetworkManager[659]: <info> (wlan0): driver WEXT...d
Mar 01 09:56:55 ********** NetworkManager[659]: <warn> (wlan0): failed to i...r
Mar 01 09:56:55 ********** NetworkManager[659]: <warn> wlan0: factory faile...)
Mar 01 09:56:55 ********** NetworkManager[659]: (NetworkManager:659): GLib-G...n
Mar 01 09:56:55 ********** NetworkManager[659]: (NetworkManager:659): GLib-G....
Mar 01 09:56:55 ********** NetworkManager[659]: <info> devices added (path:...)
Mar 01 09:56:55 ********** NetworkManager[659]: <info> device added (path: ....
Mar 01 09:57:03 ********** NetworkManager[659]: <info> WiFi hardware radio ...d
Mar 01 09:57:03 ********** NetworkManager[659]: <info> WWAN hardware radio ...d
Hint: Some lines were ellipsized, use -l to show in full.


:~$ sudo service network-manager restart


:~$ sudo lshw -c network
*-network
description: Wireless interface
physical id: 1
bus info: usb@1:4
logical name: wlx14d64d0eab8b
serial: 14:d6:4d:0e:ab:8b
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=r8712u ip=192.168.0.16 multicast=yes wireless=IEEE 802.11bgn


:~$ sudo service network-manager status
&#9679; NetworkManager.service - Network Manager
Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
Active: active (running) since Tue 2016-03-01 09:59:40 CST; 28s ago
Main PID: 1932 (NetworkManager)
CGroup: /system.slice/NetworkManager.service
&#9500;&#9472;1932 /usr/sbin/NetworkManager --no-daemon
&#9500;&#9472;1938 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-he...
&#9492;&#9472;1948 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hos...

Mar 01 09:59:53 ********** dnsmasq[1948]: started, version 2.75 cache disabled
Mar 01 09:59:53 ********** dnsmasq[1948]: compile time options: IPv6 GNU-get...y
Mar 01 09:59:53 ********** dnsmasq[1948]: DBus support enabled: connected to...s
Mar 01 09:59:53 ********** dnsmasq[1948]: warning: no upstream servers confi...d
Mar 01 09:59:53 ********** NetworkManager[1932]: <info> (wlx14d64d0eab8b): ....
Mar 01 09:59:53 ********** NetworkManager[1932]: <warn> dnsmasq appeared on...7
Mar 01 09:59:53 ********** NetworkManager[1932]: <info> Writing DNS informa...f
Mar 01 09:59:53 ********** dnsmasq[1948]: setting upstream servers from DBus
Mar 01 09:59:53 ********** dnsmasq[1948]: using nameserver 209.18.47.61#53
Mar 01 09:59:53 ********** dnsmasq[1948]: using nameserver 209.18.47.62#53
Hint: Some lines were ellipsized, use -l to show in full.


:~$ lsusb
Bus 004 Device 002: ID 8087:8001 Intel Corp.
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
Bus 001 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by txcrittr on 2016-03-02
I think I have found another clue.
```
:~$ systemctl -l status network-manager.service
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2016-03-02 10:09:44 CST; 6min ago
 Main PID: 657 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9492;&#9472;657 /usr/sbin/NetworkManager --no-daemon

Mar 02 10:09:46 ********** NetworkManager[657]: <error> [1456934986.687475] [platform/wifi/wifi-utils-wext.c:519] wext_get_range(): (wlan0): couldn't get driver range information (19).
Mar 02 10:09:46 ********** NetworkManager[657]: <info>  (wlan0): driver WEXT range request failed
Mar 02 10:09:46 ********** NetworkManager[657]: <warn>  (wlan0): failed to initialize WiFi driver
Mar 02 10:09:46 ********** NetworkManager[657]: <warn>  wlan0: factory failed to create device: (unknown)
Mar 02 10:09:46 ********** NetworkManager[657]: (NetworkManager:657): GLib-GObject-CRITICAL **: object NMDeviceWifi 0xbc2450 finalized while still in-construction
Mar 02 10:09:46 ********** NetworkManager[657]: (NetworkManager:657): GLib-GObject-CRITICAL **: Custom constructor for class NMDeviceWifi returned NULL (which is invalid). Please use GInitable instead.
Mar 02 10:09:46 ********** NetworkManager[657]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/wlx14d64d0eab8b, iface: wlx14d64d0eab8b)
Mar 02 10:09:46 ********** NetworkManager[657]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/wlx14d64d0eab8b, iface: wlx14d64d0eab8b): no ifupdown configuration found.
Mar 02 10:09:54 ********** NetworkManager[657]: <info>  WiFi hardware radio set enabled
Mar 02 10:09:54 ********** NetworkManager[657]: <info>  WWAN hardware radio set enabled
```

"Mar 02 10:09:46 ********** NetworkManager[657]: <error>  [1456934986.687475] [platform/wifi/wifi-utils-wext.c:519]  wext_get_range(): (wlan0): couldn't get driver range information (19)."

I'll bet that correcting this will fix me right up.  Now if I just knew how???

---

### Post by Bucky Ball on 2016-03-02
Please run the wirelessinfo script in the link in my signature at the bottom of this post with only the USB wireless dongle plugged in, no ethernet cable, then post the output here. Thanks.

---

### Post by txcrittr on 2016-03-03
I hope this is the right script.  My browser is not showing any signatures.
```


########## wireless info START ##########


Report from: 02 Mar 2016 22:57 CST -0600


Booted last: 02 Mar 2016 00:00 CST -0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


##### lsusb #############################


Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
Bus 001 Device 005: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              548864  0
r8712u                180224  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlx14d64d0eab8b Link encap:Ethernet  HWaddr <MAC 'wlx14d64d0eab8b' [IF]>  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx14d64d0eab8b' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2947 errors:0 dropped:20 overruns:0 frame:0
          TX packets:2583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2833594 (2.8 MB)  TX bytes:424481 (424.4 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlx14d64d0eab8b  IEEE 802.11bg  ESSID:"Maggie"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Maggie' [AC1]>   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlx14d64d0eab8b
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx14d64d0eab8b
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx14d64d0eab8b


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2022     1  0 22:52 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx14d64d0eab8b
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Manufacturer Realtek 
GENERAL.PRODUCT:                        11n Adapter
GENERAL.DRIVER:                         r8712u
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx14d64d0eab8b' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/wlx14d64d0eab8b
GENERAL.IP-IFACE:                       wlx14d64d0eab8b
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Maggie
GENERAL.CON-UUID:                       e18f712a-cc1a-4998-ab49-f12fcd118a72
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e18f712a-cc1a-4998-ab49-f12fcd118a72 | Maggie
IP4.ADDRESS[1]:                         192.168.0.16/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.61
IP4.DNS[2]:                             209.18.47.62
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 209.18.47.61 209.18.47.62
DHCP4.OPTION[5]:                        ip_address = 192.168.0.16
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1456984404
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'wlx14d64d0eab8b' [IF]>/64
IP6.GATEWAY:                            


SSID                        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FiOS-KOKUG                  <MAC 'FiOS-KOKUG' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
LANA                        <MAC 'LANA' [AC13]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
--                          <MAC '--' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA2       no        
BWSD8                       <MAC 'BWSD8' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
CG3000DV2C0                 <MAC 'CG3000DV2C0' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
MJWDQ_2GEXT                 <MAC 'MJWDQ_2GEXT' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
TC8717T15                   <MAC 'TC8717T15' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
MAZEY.net                   <MAC 'MAZEY.net' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
8P7PL                       <MAC '8P7PL' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  26      &#9602;___  WPA2       no        
HP-Print-B7-Officejet 4630  <MAC 'HP-Print-B7-Officejet 4630' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  7       &#9602;___  --         no        
Maggie                      <MAC 'Maggie' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
89GS4                       <MAC '89GS4' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
Nkem's                      <MAC 'Nkem's' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  26      &#9602;___  WPA2       no        
33I60                       <MAC '33I60' [AN14]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WEP        no        
--                          <MAC '<hidden>' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  43      &#9602;&#9604;__  --         no        
Maggie                      <MAC 'Maggie' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Maggie]] (600 root)
[connection] id=Maggie | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx14d64d0eab8b' [IF]> | mac-address-blacklist= | ssid=Maggie
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


wlx14d64d0eab8b  14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      9   APs on   Frequency:2.437 GHz (Channel 6)
      5   APs on   Frequency:2.462 GHz (Channel 11)


wlx14d64d0eab8b  Scan completed :
          Cell 01 - Address: <MAC 'Maggie' [AC1]>
                    ESSID:"Maggie"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC '89GS4' [AC2]>
                    ESSID:"89GS4"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  
          Cell 03 - Address: <MAC 'BWSD8' [AC3]>
                    ESSID:"BWSD8"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 04 - Address: <MAC 'MJWDQ_2GEXT' [AC4]>
                    ESSID:"MJWDQ_2GEXT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 05 - Address: <MAC 'TC8717T15' [AC5]>
                    ESSID:"TC8717T15"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 06 - Address: <MAC '<hidden>' [AC6]>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11gn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=92/100  
          Cell 07 - Address: <MAC 'MJWDQ' [AC7]>
                    ESSID:"MJWDQ"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 08 - Address: <MAC 'HP-Print-B7-Officejet 4630' [AC8]>
                    ESSID:"HP-Print-B7-Officejet 4630"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  
          Cell 09 - Address: <MAC '8P7PL' [AC9]>
                    ESSID:"8P7PL"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 10 - Address: <MAC 'FiOS-KOKUG' [AC10]>
                    ESSID:"FiOS-KOKUG"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=62/100  
          Cell 11 - Address: <MAC 'Maggie' [AC11]>
                    ESSID:"Maggie"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=58/100  
          Cell 12 - Address: <MAC '<hidden>' [AC12]>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=47/100  
          Cell 13 - Address: <MAC 'LANA' [AC13]>
                    ESSID:"LANA"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=62/100  
          Cell 14 - Address: <MAC 'MAZEY.net' [AC14]>
                    ESSID:"MAZEY.net"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[r8712u]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     D30681639AA713DFA58C271
depends:        
staging:        Y
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 0
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 1
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0


##### /etc/modules ######################


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    2.849936] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    2.850330] r8712u: register rtl8712_netdev_ops to netdev_ops
[    2.850332] usb 1-4: r8712u: USB_SPEED_HIGH with 4 endpoints
[    2.850622] usb 1-4: r8712u: Boot from EFUSE: Autoload OK
[    3.185986] usb 1-4: r8712u: CustomerID = 0x0006
[    3.185989] usb 1-4: r8712u: MAC Address from efuse = <MAC 'wlx14d64d0eab8b' [IF]>
[    3.185990] usb 1-4: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    3.189459] r8712u 1-4:1.0 wlx14d64d0eab8b: renamed from wlan0
[   95.906531] IPv6: ADDRCONF(NETDEV_UP): wlx14d64d0eab8b: link is not ready
[   96.609827] r8712u 1-4:1.0 wlx14d64d0eab8b: 1 RCR=0x153f00e
[   96.610346] r8712u 1-4:1.0 wlx14d64d0eab8b: 2 RCR=0x553f00e
[   96.713651] IPv6: ADDRCONF(NETDEV_UP): wlx14d64d0eab8b: link is not ready (repeated 4 times)
[  117.430084] IPv6: ADDRCONF(NETDEV_CHANGE): wlx14d64d0eab8b: link becomes ready


########## wireless info END ############



```

---

### Post by txcrittr on 2016-03-03
Here is wireless-info.txt before network-manager restart
```
########## wireless info START ##########


Report from: 03 Mar 2016 01:15 CST -0600


Booted last: 03 Mar 2016 00:00 CST -0600


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


##### lsusb #############################


Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 07d1:3300 D-Link System DWA-130 802.11n Wireless N Adapter(rev.E) [Realtek RTL8191SU]
Bus 001 Device 005: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              548864  0
r8712u                180224  0
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlx14d64d0eab8b Link encap:Ethernet  HWaddr <MAC 'wlx14d64d0eab8b' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


wlx14d64d0eab8b  unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       671     1  0 01:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Maggie]] (600 root)
[connection] id=Maggie | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx14d64d0eab8b' [IF]> | mac-address-blacklist= | ssid=Maggie
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


wlx14d64d0eab8b  14 channels in total; available frequencies :
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


##### iwlist scan #######################


wlx14d64d0eab8b  Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[r8712u]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     D30681639AA713DFA58C271
depends:        
staging:        Y
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        AA:46:91:2A:20:E4:E1:7B:1E:4A:6C:CC:08:BD:3C:70:D4:D8:F4:64
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 0
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 1
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0


##### /etc/modules ######################


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    3.061024] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    3.061440] r8712u: register rtl8712_netdev_ops to netdev_ops
[    3.061444] usb 1-4: r8712u: USB_SPEED_HIGH with 4 endpoints
[    3.061710] usb 1-4: r8712u: Boot from EFUSE: Autoload OK
[    3.394327] usb 1-4: r8712u: CustomerID = 0x0006
[    3.394330] usb 1-4: r8712u: MAC Address from efuse = <MAC 'wlx14d64d0eab8b' [IF]>
[    3.394332] usb 1-4: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    3.397732] r8712u 1-4:1.0 wlx14d64d0eab8b: renamed from wlan0


########## wireless info END ############

```

---

### Post by Hadaka on 2016-03-03
Hi, this should work for you.
[http://askubuntu.com/questions/627393/d-link-dwa-130-rev-e1-rtl8191su-hard-time-connecting](http://askubuntu.com/questions/627393/d-link-dwa-130-rev-e1-rtl8191su-hard-time-connecting)

---

### Post by Bucky Ball on 2016-03-03
> **Hadaka said:**
> Hi, this should work for you.
[http://askubuntu.com/questions/627393/d-link-dwa-130-rev-e1-rtl8191su-hard-time-connecting](http://askubuntu.com/questions/627393/d-link-dwa-130-rev-e1-rtl8191su-hard-time-connecting)

And Pilot6's second follow up post (last on the link) provides a PPA so you don't need to run the commands every kernel update by the looks. :)

---

### Post by txcrittr on 2016-03-03
I have already applied that fix.  It didn't work the first time, nor just now, when I retried it.  The wireless-info.txt files were generated AFTER this fix was originally applied.

I truly do thank you for your help.  Is there a way to make the network-manager automatically restart, say 15 seconds, after boot?

---

### Post by Hadaka on 2016-03-03
Hi, you shouldnt have to delay network mgr. for wifi to work correctly.
im going to do some more research on this and see what is available.
meantime, please copy and paste the following. your country code is not
set, and that can create wifi problems as well. please do..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
thanks.

---

### Post by txcrittr on 2016-03-03
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo iw reg set US
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda[/FONT][/COLOR]
```

This is done.  I agree that I "shouldn't" need to automatically delay or restart netwrk-mgr to make wifi work.  I am committed to solving this, and I ALSO shouldn't have to "sudo service network-manager restart" on every boot.  A short term workaround is, in my opinion, in order.  Workarounds often point toward a permanent solution.  I can't help but wonder if the SSD is allowing things to happen faster than the OS is expecting, thereby causing a failure because some boot test happens before the network hardware can catch up.

---

### Post by Hadaka on 2016-03-03
If that were the the case there would be thousands of people with the same
problem you are having,i sent a message to an expert to take a look at this
so please be patient while a solution is found,.and while im thinking about it
did you run your updates after you loaded the os ?? if not 
from a working wired connection..,please do...
```
sudo apt-get update
sudo apt-get dist-upgrade #no this does not upgrade your os to the next load
sudo apt-get autoremove
sudo apt-get autoclean
```
thanks

---

### Post by chili555 on 2016-03-03
> Mar 01 09:56:55 ********** NetworkManager[659]: <error> [1456847815.760397] ....
Mar 01 09:56:55 ********** NetworkManager[659]: <info> (wlan0): driver WEXT...d
Mar 01 09:56:55 ********** NetworkManager[659]: <warn> (wlan0): failed to i...r
Mar 01 09:56:55 ********** NetworkManager[659]: <warn> wlan0: factory faile...)
Mar 01 09:56:55 ********** NetworkManager[659]: (NetworkManager:659): GLib-G...n
Mar 01 09:56:55 ********** NetworkManager[659]: (NetworkManager:659): GLib-G....
Mar 01 09:56:55 ********** NetworkManager[659]: <info> devices added (path:...)
Mar 01 09:56:55 ********** NetworkManager[659]: <info> device added (path: ....
Mar 01 09:57:03 ********** NetworkManager[659]: <info> WiFi hardware radio ...d
Mar 01 09:57:03 ********** NetworkManager[659]: <info> WWAN hardware radio ...d
Hint: Some lines were ellipsized, use -l to show in full.Well, yes, we would _love_ to see the exact nature of these errors and warnings. This doesn't provide anything useful:>  NetworkManager[659]: <error> [1456847815.760397] ....While we may be able to dig deep in the code for Network Manager to find and fix the issue, let's try the brute strength approach for now. Please do:```
sudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit.

It should now read:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```Please change it to read:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 3
service network-manager restart

exit 0

```Proofread carefully, save and close the text editor.

Reboot. Any improvement?

---

### Post by txcrittr on 2016-03-03
Hadaka, I had done the updates, but not the autoclean and autoremove, so I redid the whole thing.  I've looked at probably 50 or 75 different threads across the WWW about this very issue, most solved their problem by (a) reverting to an earlier (or different) distro, or (b) replacing the wireless device.

This works.
> [COLOR=#000000]Please change it to read:[/COLOR][COLOR=#000000]Code:
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 3
service network-manager restart

exit 0[/COLOR]
[COLOR=#000000]Proofread carefully, save and close the text editor.[/COLOR]


Thanks Chili555!
```
:~$ systemctl -l status network-manager.service&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2016-03-02 10:09:44 CST; 6min ago
 Main PID: 657 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9492;&#9472;657 /usr/sbin/NetworkManager --no-daemon


Mar 02 10:09:46 ********** NetworkManager[657]: <error> [1456934986.687475] [platform/wifi/wifi-utils-wext.c:519] wext_get_range(): (wlan0): couldn't get driver range information (19).
Mar 02 10:09:46 ********** NetworkManager[657]: <info>  (wlan0): driver WEXT range request failed
Mar 02 10:09:46 ********** NetworkManager[657]: <warn>  (wlan0): failed to initialize WiFi driver
Mar 02 10:09:46 ********** NetworkManager[657]: <warn>  wlan0: factory failed to create device: (unknown)
Mar 02 10:09:46 ********** NetworkManager[657]: (NetworkManager:657): GLib-GObject-CRITICAL **: object NMDeviceWifi 0xbc2450 finalized while still in-construction
Mar 02 10:09:46 ********** NetworkManager[657]: (NetworkManager:657): GLib-GObject-CRITICAL **: Custom constructor for class NMDeviceWifi returned NULL (which is invalid). Please use GInitable instead.
Mar 02 10:09:46 ********** NetworkManager[657]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/wlx14d64d0eab8b, iface: wlx14d64d0eab8b)
Mar 02 10:09:46 ********** NetworkManager[657]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/wlx14d64d0eab8b, iface: wlx14d64d0eab8b): no ifupdown configuration found.
Mar 02 10:09:54 ********** NetworkManager[657]: <info>  WiFi hardware radio set enabled
Mar 02 10:09:54 ********** NetworkManager[657]: <info>  WWAN hardware radio set enabled



```

Maybe this is more useful?

I'm  not really wanting to call this solved, because we haven't really fixed the root problem,  We do however have a workaround that is quite simple.

---

### Post by chili555 on 2016-03-03
It appears to be an as yet unresolved bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986) You will see most of your symptoms there, including:> [platform/wifi/wifi-utils-wext.c:519] wext_get_range(): (wlan0): couldn't get driver range information (19)

What is interesting is that I also run 15.10 and Network Manager and have no problem at all. 

Until the bug is fixed and, I assume, some update to NM is issued, I think the work-around is all we can do.

---

### Post by Hadaka on 2016-03-03
Hi,there may also be another way to rid your Network Manager of this problem.
we will need some additional information to confirm.Please do and post....
```
apt-cache policy network-manager
``` 
then..in the launcher..left side..please click these items in the following order

 #software center
 #edit ...           'top left edge of screen' 'same level as the clock and envelope'
 #software sources
 #updates tab
see if the 'Pre-released updates...Proposed' is checked..
*If yes..UNCHECK
please report if it was checked or unchecked.
thanks.

---

### Post by txcrittr on 2016-03-03
I'm not currently where that computer is, but I'll do it tomorrow.

---

### Post by txcrittr on 2016-03-04
Just for grins, I tried booting with the "sleep 3" line commented in rc.local and then with "sleep 1" (instead of 3).  Both resulted in no wifi at boot, so I'm back at sleep 3.

Hadaka
"Pre-release updates (wily-proposed) was, and remains, unchecked.
```
:~$ apt-cache policy network-managernetwork-manager:
  Installed: 1.0.4-0ubuntu5.2
  Candidate: 1.0.4-0ubuntu5.2
  Version table:
 *** 1.0.4-0ubuntu5.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.4-0ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages



```

Based on this
> ***Chili555: ***"[COLOR=#000000]Until the bug is fixed and, I assume, some update to NM is issued, I think the work-around is all we can do."[/COLOR]
it seems like time to call this solved?

Next question?  How do [FONT=times new roman][COLOR=red][SIZE=6]**I**[/SIZE][/COLOR][/FONT] help fix this?

Thank each of you for your help and patience.  I'll boot more to Linux than MS and I'll help make Ubuntu better.

---

### Post by Bucky Ball on 2016-03-04
You can help now by marking the thread as solved. See the link in my signature for how. This does not close the thread to further discussion. :)

Good luck and enjoy your Ubuntu travels.

---

### Post by txcrittr on 2016-03-04
Now, how to debug network-manager and fix the code?  Launchpad I suppose?

---

### Post by Hadaka on 2016-03-04
Hi, please take a look at this link, and the response about 1/2 way down
post #7 and 8 by..Mathieu Trudel_Lapierre
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1489154](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1489154)
thanks.

---

### Post by txcrittr on 2016-03-04
Bug 1489154 isn't really my issue.  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986) is much closer to what I am dealing with.

---

