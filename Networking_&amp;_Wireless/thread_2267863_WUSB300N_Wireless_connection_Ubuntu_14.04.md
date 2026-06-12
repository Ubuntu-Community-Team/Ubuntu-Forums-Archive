---
title: "WUSB300N Wireless connection Ubuntu 14.04"
date: 2015-03-04
forum: Networking &amp; Wireless
---

### Post by jeff122 on 2015-03-04
My first post---

I am currently working on a machine and in a CLI class and I have scoured the forums here the past couple of days trying to resolve this issue using a WUSB300N linksys usb dongle.  I have made much progress or it seemed like it and I can see the networks but when I try to connect it will ask me for the wifi password again and then just disconnect me.  I thought it was a password problem so I changed it.  I have the drivers.  I know I have missed a step or just don't know enough to finish it.  Looking at other forums and information requested to help resolve the issue I have attached some logs.  I know I am close, it had connected twice but then dropped connections and I tried some other things to keep the connection on and rebooted and then I wasn't able to connect wirelessly again.  I just haven't learned all the commands I need yet.

#sudo lshw -C network
  *-network              
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 01
       serial: 00:0c:f1:ae:75:c7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.75 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:ff9ef000-ff9effff ioport:b000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:70:37:5d:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.59+Linksys, A Division of Cisc link=no multicast=yes wireless=IEEE 802.11g

# iwconfig
wlan0     IEEE 802.11g  ESSID:off/any 
          Mode:Managed  Channel:0  Access Point: Not-Associated  
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm 
          RTS thr=2346 B   Fragment thr=2346 B  
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
lo        no wireless extensions.
 
eth1      no wireless extensions.


# lspci -nnk | grep -iA2 net
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
            Subsystem: Intel Corporation D865PERL mainboard [8086:3020]
            Kernel driver in use: e100
 
 
 
 
# iwconfig
wlan0     IEEE 802.11g  ESSID:off/any 
          Mode:Managed  Channel:0  Access Point: Not-Associated  
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm 
          RTS thr=2346 B   Fragment thr=2346 B  
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
lo        no wireless extensions.
 
eth1      no wireless extensions.


# lsmod
Module                  Size  Used by
cfg80211              418839  0
bnep                   18895  2
rfcomm                 58045  0
bluetooth             391253  10 bnep,rfcomm
6lowpan_iphc           18262  1 bluetooth
hid_generic            12503  0
ppdev                  17391  0
snd_emu10k1x           19415  4
snd_intel8x0           37321  4
snd_ac97_codec        105860  2 snd_intel8x0,snd_emu10k1x
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                87194  3 snd_ac97_codec,snd_intel8x0,snd_emu10k1x
snd_seq_midi           13324  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25722  2 snd_emu10k1x,snd_seq_midi
snd_seq                56592  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28648  2 snd_pcm,snd_seq
radeon               1308240  3
ttm                    85257  1 radeon
drm_kms_helper         55007  1 radeon
snd                    66670  24 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_emu10k1x
serio_raw              13251  0
drm                   255469  6 ttm,drm_kms_helper,radeon
soundcore              14599  1 snd
i2c_algo_bit           13197  1 radeon
emu10k1_gp             12550  0
gameport               15189  2 emu10k1_gp
lpc_ich                16877  0
intel_rng              12709  0
parport_pc             32021  1
shpchp                 32143  0
ndiswrapper           192915  0
lp                     13299  0
mac_hid                13059  0
parport                40836  3 lp,ppdev,parport_pc
usbhid                 47035  0
hid                    95946  2 hid_generic,usbhid
pata_acpi              12901  0
e100                   35960  0
mii                    13654  1 e100
floppy                 59708  0



# sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Mar  4 07:24:15 Elmer-desktop avahi-daemon[785]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21a:70ff:fe37:5d9d.
Mar  4 07:24:15 Elmer-desktop avahi-daemon[785]: Withdrawing address record for fe80::21a:70ff:fe37:5d9d on wlan0.
Mar  4 07:24:15 Elmer-desktop avahi-daemon[785]: Withdrawing workstation service for wlan0.
Mar  4 07:24:15 Elmer-desktop kernel: [  342.913625] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop NetworkManager[856]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Mar  4 07:24:15 Elmer-desktop NetworkManager[856]: <info> (wlan0): cleaning up...
Mar  4 07:24:15 Elmer-desktop kernel: [  342.921241] ndiswrapper: device wlan0 removed
Mar  4 07:24:15 Elmer-desktop NetworkManager[856]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0)
Mar  4 07:24:15 Elmer-desktop kernel: [  342.987425] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop kernel: [  343.026585] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop kernel: [  343.033884] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop kernel: [  343.043327] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop kernel: [  343.051011] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop kernel: [  343.061680] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:24:15 Elmer-desktop wpa_supplicant[2869]: Could not read interface wlan0 flags: No such device
Mar  4 07:24:15 Elmer-desktop kernel: [  343.072507] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead.
Mar  4 07:43:12 Elmer-desktop kernel: [ 1480.252759] wlan0: ethernet device 00:1a:70:37:5d:9d using NDIS driver: netmw245, version: 0x1000402, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 13B1:0029.F.conf
Mar  4 07:43:12 Elmer-desktop kernel: [ 1480.252837] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): using WEXT for WiFi device control
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 4)
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): bringing up device.
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): preparing device.
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  4 07:43:12 Elmer-desktop kernel: [ 1480.293106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0)
Mar  4 07:43:12 Elmer-desktop NetworkManager[856]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  4 07:43:15 Elmer-desktop NetworkManager[856]: <info> (wlan0) supports 1 scan SSIDs
Mar  4 07:43:15 Elmer-desktop NetworkManager[856]: <info> (wlan0): supplicant interface state: starting -> ready
Mar  4 07:43:15 Elmer-desktop NetworkManager[856]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar  4 07:43:15 Elmer-desktop NetworkManager[856]: <info> (wlan0): supplicant interface state: ready -> disconnected
Mar  4 07:43:15 Elmer-desktop NetworkManager[856]: <info> (wlan0) supports 1 scan SSIDs
Mar  4 07:43:25 Elmer-desktop NetworkManager[856]: <info> (wlan0): supplicant interface state: disconnected -> inactive



Any and all help would be greatly appreciated.   Thanks--Jeff

---

### Post by jeff122 on 2015-03-04
I think I posted this in the wrong forums. Anyone want to move it to networking?

---

### Post by mörgæs on 2015-03-04
Done.
Please edit your post and add CODE tags around terminal output.

---

### Post by jeff122 on 2015-03-04
not sure if I edited it correctly and at the moment I have a network outage.  AT&T 2wire.  I think that's the culprit but I won't know until Sun when I get Comcast out.

---

### Post by mörgæs on 2015-03-05
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by jeff122 on 2015-03-16
So, I got it working.  One thing I would like to add for all the newer people like me messing with things is don't forget if you are using IPv4 it has to be checked on.

---

