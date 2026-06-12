---
title: "Unable to connect to wifi w/ Atheros"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Blueapples on 2008-09-25
[B][COLOR="DarkRed"]
#####################
Resolved for me!

If you need a few tips getting your wifi working on your MacBook, see the last post here: [http://ubuntuforums.org/showpost.php?p=5863209&postcount=12](http://ubuntuforums.org/showpost.php?p=5863209&postcount=12)
#####################
[/COLOR][/B]





I have tried all three of the driver options on the MacBook page [https://help.ubuntu.com/community/MacBook#Wireless]("https://help.ubuntu.com/community/MacBook#Wireless"). I still can't get on a wireless network. When I install wicd, it actually lists my network and correctly identifies the encryption type (I have tried with WPA, WPA2, and WEP. It is currently set to WPA2.)

At this point I am a bit worried about having competing wireless drivers, but I just can't parse this stuff well enough to really tell. I *think* I removed MadWifi and ndiswrapper but I'm not really confident on that point. I am currently trying to get ath9k to work.

Ah and I am using the latest ISO download installed on a second partition under bootcamp (sort of, rEFIt is also on there but I can't get into Linu with it, it just freezes, but that's a different problem).

If anyone can help I would really appreciate it. I am kind of frustrated right now... this sounds like it's supposed to work pretty easily.


Here are the seemingly relevant data points. I can provide more of course...


isaac@isaac-laptop:~$ lsmod
```

Module                  Size  Used by
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
hci_usb                16540  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  7 hci_usb,rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  2 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
af_packet              23812  8 
snd_hda_intel         386588  3 
snd_hwdep              10884  1 snd_hda_intel
joydev                 13120  0 
snd_seq_dummy           4996  0 
snd_seq_oss            35968  0 
mac80211              165652  0 
uvcvideo               58116  0 
snd_seq_midi           10784  0 
compat_ioctl32          2304  1 uvcvideo
cfg80211               15112  1 mac80211
appletouch             11264  0 
snd_rawmidi            27168  1 snd_seq_midi
videodev               29440  1 uvcvideo
wlan_scan_sta          16000  1 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
appleir                 7040  0 
snd_pcm_oss            51232  0 
snd_mixer_oss          18432  1 snd_pcm_oss
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
ath_rate_sample        16000  1 
snd_seq                58320  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
usbhid                 31872  0 
snd_pcm                86660  2 snd_hda_intel,snd_pcm_oss
hid                    38784  1 usbhid
ath_pci               250168  0 
wlan                  235760  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               252512  3 ath_rate_sample,ath_pci
sky2                   47492  0 
snd_timer              25988  2 snd_seq,snd_pcm
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc         12168  2 snd_hda_intel,snd_pcm
battery                14212  0 
video                  19856  0 
output                  4736  1 video
snd                    64708  19 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
button                  9232  0 
intel_agp              25492  1 
ac                      6916  0 
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
evdev                  13056  8 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
ata_piix               19588  2 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
uhci_hcd               27024  0 
usbcore               146028  8 hci_usb,uvcvideo,appletouch,appleir,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

isaac@isaac-laptop:~$ sudo ifconfig
```

ath0      Link encap:Ethernet  HWaddr 00:1b:63:c2:d8:ac  
          inet6 addr: fe80::21b:63ff:fec2:d8ac/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1062 errors:20 dropped:20 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:236622 (231.0 KB)  TX bytes:143465 (140.1 KB)

ath0:avahi Link encap:Ethernet  HWaddr 00:1b:63:c2:d8:ac  
          inet addr:169.254.9.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1b:63:1d:d2:ec  
          inet addr:10.0.1.197  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe1d:d2ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1112438 (1.0 MB)  TX bytes:183259 (178.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84712 (82.7 KB)  TX bytes:84712 (82.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-63-C2-D8-AC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14613 errors:0 dropped:0 overruns:0 frame:511
          TX packets:4595 errors:0 dropped:20 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:1770971 (1.6 MB)  TX bytes:398647 (389.3 KB)
          Interrupt:16 

```
isaac@isaac-laptop:~$ sudo iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"Orchard"  Nickname:""
          Mode:Managed  Frequency:5.32 GHz  Access Point: 00:1B:63:2C:BC:0F   
          Bit Rate:54 Mb/s   Tx-Power:11 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=74/70  Signal level=-22 dBm  Noise level=-96 dBm
          Rx invalid nwid:5295  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

isaac@isaac-laptop:~$ sudo cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

#iface ath0 inet dhcp
#wireless-key s:xxxxxxxxxxxxx
#wireless-essid Orchard
iface ath0 inet dhcp
  # driver, "wext" = Linux wireless extensions (generic WLAN driver)
  # SSID
  wpa-ap-scan 1
  # "1" = broadcast of SSID, "2" = hidden broadcast
  # "WPA" = WPA1, "RSN" = WPA2
  wpa-pairwise TKIP
  # "TKIP" for WPA1, "CCMP" for WPA2 (AES)
  wpa-group TKIP
  wpa-driver wext
  wpa-key-mgmt WPA-PSK
  wpa-proto WPA2
  wpa-ssid Orchard
  # "TKIP" for WPA1, "CCMP" for WPA2 (AES)
  # "WPA-PSK" = pre-shared key (usual in home networks), "WPA-EAP" = enterprise authentication server (e.g. RADIUS)
	#psk="xxxxxxxxxxxxxxxxxx"
              
  # use the following command to produce <KEY>:   wpa_passphrase 'SSID' 'PASSPHRASE'

auto ath0

```

---

### Post by Blueapples on 2008-09-26
isaac@isaac-laptop:~$ sudo dhclient3
```

isaac@isaac-laptop:~$ sudo dhclient3
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1b:63:c2:d8:ac
Sending on   LPF/ath0/00:1b:63:c2:d8:ac
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1b:63:1d:d2:ec
Sending on   LPF/eth0/00:1b:63:1d:d2:ec
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST of 10.0.1.197 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST of 10.0.1.197 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
isaac@isaac-laptop:~$ 


```

---

### Post by Blueapples on 2008-09-26
isaac@isaac-laptop:~$ ping -I wifi0 google.com
PING google.com (72.14.207.99) from 10.0.1.197 wifi0: 56(84) bytes of data.
From isaac-laptop.local (10.0.1.197) icmp_seq=1 Destination Host Unreachable

---

### Post by Blueapples on 2008-09-26
isaac@isaac-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        *               255.255.255.0   U     0      0        0 eth0
default         Apple1.local    0.0.0.0         UG    0      0        0 eth0

---

### Post by Blueapples on 2008-09-26
Sorry, was trying to do some interactive collab with someone on the channel. Will post solution if we get one.

---

### Post by Blueapples on 2008-09-26
I am running Hardy Heron on a 3.1 (I think) MacBook. It has the Atheros AR5418 chipset. I posted a thread in the Apple section but I don't think anyone frequenting that has any input for wireless networking - didn't see this section before. The thread is [here]("http://ubuntuforums.org/showthread.php?t=930310") and contains output from ifconfig, iwconfig, lsmod, cat /etc/network/interfaces, dhclient3 (with ethernet cable disconnected), and route. Hopefully someone can take a look at this stuff and tell me what I've done wrong.

I tried to install all three options listed at the [MacBook page]("https://help.ubuntu.com/community/MacBook#Wireless") but none of them seem to work. I'm a little worried that I might have duplicate drivers installed, but lsmod doesn't seem to list anything else. I am pretty experienced with development but the kernel is somewhat baffling to me I guess.

Any help would be very appreciated. I would **really** like to have Ubuntu running with my wireless.

---

### Post by Blueapples on 2008-09-26
Moving request to [http://ubuntuforums.org/showthread.php?p=5861906](http://ubuntuforums.org/showthread.php?p=5861906)

---

### Post by jpeddicord on 2008-09-26
Threads merged. :)

---

### Post by Blueapples on 2008-09-26
Thanks! I'm so sorry I made a mess. Ok so... if we can fix the problem that'd be good too =D

---

### Post by Mgiacchetti on 2008-09-26
Try this man, go to /sys/devices/platforms/  (your machine type) / and look for wifi0 wlan0 or something denoting a wireless interface; and if it holds only a 0  then its off...

---

### Post by Blueapples on 2008-09-26
> **Mgiacchetti said:**
> Try this man, go to /sys/devices/platforms/  (your machine type) / and look for wifi0 wlan0 or something denoting a wireless interface; and if it holds only a 0  then its off...

I can't really figure out where to look in here. This is what I saw in that path:

```

isaac@isaac-laptop:~$ ls /sys/devices/platform
bluetooth  eisa.0  iTCO_wdt  pcspkr  power  serial8250  uevent

```

None of those look like the architecture I'm running, which should be a Intel Core 2 Duo - or whatever the real name of that is.

At any rate, there are no files in that tree with any of these names:

```

isaac@isaac-laptop:~$ ls -R /sys/devices/platform | grep wifi
isaac@isaac-laptop:~$ ls -R /sys/devices/platform | grep wlan
isaac@isaac-laptop:~$ ls -R /sys/devices/platform | grep lan
isaac@isaac-laptop:~$ ls -R /sys/devices/platform | grep eth
isaac@isaac-laptop:~$ ls -R /sys/devices/platform | grep ath

```

I did find these though:

```


isaac@isaac-laptop:~$ ls -R /sys/devices | grep wifi
wifi0
madwifi_name_type
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wifi0:
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wifi0/power:
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wifi0/statistics:
isaac@isaac-laptop:~$ cat /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wifi0


isaac@isaac-laptop:~$ ls /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wifi0
address    carrier  features  iflink     operstate   subsystem     uevent
addr_len   device   flags     link_mode  power       tx_queue_len
broadcast  dormant  ifindex   mtu        statistics  type

isaac@isaac-laptop:~$ ls -R /sys/devices | grep ath
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
path
ath0
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/ath0:
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/ath0/power:
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/ath0/statistics:
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/ath0/wireless:


```

I got to be honest though, I'm not sure where to look from here. It does kind of bug me that (as seen in the ifconfig output above also) that there seem to be **two** wireless devices, or at least two wireless modules (wifi0 and ath0). Is this perhaps part of my problem?

The *numerous* occurance of "path" before it gets to the contents of ath0 above is also a bit odd...

---

### Post by Blueapples on 2008-09-27
Well, I wish I knew how exctly, but this is resolved.

Tips for other people having trouble:

Use ath9k. It works much better than madwifi, from what I can tell.
Use network-manager. This is not installed by default, do

sudo apt-get install network-manager network-manager-gnome

then restart. For me, this tool has been much easier to use than manual config or wicd. This will add a new icon to your tray that can be LEFT clicked to show a list of wireless networks, if you're from Mac OS it works pretty much the same as the AirPort menu (almost identical actually). If you need to change the key for a network, RIGHT click this icon, select "Edit Wireless Networks..." and then just hit "Remove" with the network selected, then go through the initial set up (LEFT click, click the network name, enter key) to get it to work.

If you have tried several drivers and not had success with them, you need to **blacklist** all the ones that didn't work. You can see a list of installed modules in the kernel with the « lsmod » command. To blacklist a module, edit /etc/modprobe.d/blacklist and add « blacklist <modulename> » to the end of the file. Restart after editing this file (technically you can do modprobe -r <modulename> to remove the modules but I prefer restarts just to make sure you did the config correctly and it behaves as expected, I'm no expert though).

Specifically, if you have tried madwifi, you need to add these lines to the end of the file to disable it:

```

blacklist ath_pci
blacklist ath_rate_sample
blacklist ath_hal

```

I am not sure if it was a compatibility issue, but I was having no luck with the setup I had used on the router with Mac OS X. The following set up works with my MacBook on my AirPort Extreme router:

Broadcast SSID
802.11g (b/g compatable)
Let the tool generate a new passcode for you (write it down of course ;)
WPA2 only
AES-CCMP
Channel 6 - maybe different for your area, 6 is very common. Try 11 first if you have trouble connecting because of a lot of networks in your area on channel 6.  Though 11 can get interference from other sources more easily because it is on the edge of the wifi spectrum.

These are just tips! I hope it helps someone get wireless working on their MacBook in Ubuntu.

Lastly I have heard that 2.6.17 will have ath9k built in, so once that gets into Ubuntu we should have **out of the box** wifi on MacBooks! Woooo!

- BA out

---

