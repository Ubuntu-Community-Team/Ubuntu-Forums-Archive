---
title: "Newbie and Wireless in FIesty (NM and WPA)"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by myidbe on 2007-05-23
Hi forum,

I'm trying to get my (WPA1) wireless connection to work with the following:

Sony PCG-V505EX Laptop
Intel Pro-Wireless 2100 integrated wireless LAN
(running Ubuntu 7.04)

I tried following [this howto]("http://ubuntuforums.org/showthread.php?t=202834"), had little success (I did get some good practice with terminal commands though :) ) and was told to try Network manager.  Network manager works great with cable LAN. It also sees the wireless network, but after I input my password (which it prompts me for in the pop-up window) nothing happens.

Below i've included some info and the situation from the terminal:

hoping you can help...

~Van

uname -a
```

malcolm@malcolm-laptop:~$ uname -a
Linux malcolm-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

ifconfig -a
```

malcolm@malcolm-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:46:CD:1A:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:268898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263632148 (251.4 MiB)  TX bytes:25486778 (24.3 MiB)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:03:2B:01  
          inet6 addr: fe80::20e:35ff:fe03:2b01/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:68 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:295156 (288.2 KiB)  TX bytes:496768 (485.1 KiB)
          Interrupt:9 Base address:0x6000 Memory:d0201000-d0201fff 

eth0:avah Link encap:Ethernet  HWaddr 08:00:46:CD:1A:01  
          inet addr:169.254.3.97  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth1:avah Link encap:Ethernet  HWaddr 00:0E:35:03:2B:01  
          inet addr:169.254.1.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0x6000 Memory:d0201000-d0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1087245 (1.0 MiB)  TX bytes:1087245 (1.0 MiB)

```

route -n
```

malcolm@malcolm-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

iwconfig
```

malcolm@malcolm-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HieglW"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:15:0C:D3:EE:C5   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-56 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:68   Missed beacon:0

```

ifconfig
```
malcolm@malcolm-laptop:~$ ifconfigeth0      Link encap:Ethernet  HWaddr 08:00:46:CD:1A:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:268898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263632148 (251.4 MiB)  TX bytes:25486778 (24.3 MiB)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:03:2B:01  
          inet6 addr: fe80::20e:35ff:fe03:2b01/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:68 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:310637 (303.3 KiB)  TX bytes:524762 (512.4 KiB)
          Interrupt:9 Base address:0x6000 Memory:d0201000-d0201fff 

eth0:avah Link encap:Ethernet  HWaddr 08:00:46:CD:1A:01  
          inet addr:169.254.3.97  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth1:avah Link encap:Ethernet  HWaddr 00:0E:35:03:2B:01  
          inet addr:169.254.1.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0x6000 Memory:d0201000-d0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1089284 (1.0 MiB)  TX bytes:1089284 (1.0 MiB)

```

lsmod
```
malcolm@malcolm-laptop:~$ lsmodModule                  Size  Used by
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14208  0 
fat                    53916  1 vfat
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
sonypi                 23196  0 
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_centrino      9920  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
cpufreq_powersave       2688  0 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5408  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
button                  8720  0 
container               5248  0 
ac                      6020  0 
video                  16388  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
ipv6                  268704  8 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
pcmcia                 39212  0 
joydev                 10816  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
ipw2200               148040  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
serio_raw               7940  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ieee80211              34760  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25116  1 
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  18 
evdev                  11008  3 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
usb_storage            72256  0 
libusual               17936  1 usb_storage
ata_piix               15492  2 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
e100                   36232  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

iwlist scan
```
malcolm@malcolm-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:0C:D3:EE:C5
                    ESSID:"HieglW"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-30 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 2696ms ago
          Cell 02 - Address: 00:03:C9:8B:4C:52
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    Extra: Last beacon: 2536ms ago

```

cat /etc/network/interfaces
```
malcolm@malcolm-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid XXXXXX
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk LotsOfNumbersAndLettersHere0123456789

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

cat /etc/modprobe.d/ndiswrapper
```
malcolm@malcolm-laptop:~$ cat /etc/modprobe.d/ndiswrapper
cat: /etc/modprobe.d/ndiswrapper: No such file or directory

```

cat /etc/resolv.conf
```

malcolm@malcolm-laptop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!



nameserver 192.168.178.1

```

sudo /etc/init.d/networking restart
```
malcolm@malcolm-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/08:00:46:cd:1a:01
Sending on   LPF/eth0/08:00:46:cd:1a:01
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.178.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:03:2b:01
Sending on   LPF/eth1/00:0e:35:03:2b:01
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/08:00:46:cd:1a:01
Sending on   LPF/eth0/08:00:46:cd:1a:01
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:03:2b:01
Sending on   LPF/eth1/00:0e:35:03:2b:01
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

---

### Post by Kobalt on 2007-05-23
Network-Manager needs the /etc/network/interfaces file to be almost blank, which means you'll have to comment out anything but the lo interface. It would look like this : > auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp
# wpa-driver wext
# wpa-ssid XXXXXX
# wpa-ap-scan 1
# wpa-proto WPA RSN
# wpa-pairwise TKIP CCMP
# wpa-group TKIP CCMP
# wpa-key-mgmt WPA-PSK
# wpa-psk LotsOfNumbersAndLettersHere0123456789

# auto eth2
# iface eth2 inet dhcp

#auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp
Once you've done this restart NM and it should be working better : ```
sudo /etc/init.d/dbus restart
```

---

### Post by myidbe on 2007-05-23
Did that:

/etc/network/interfaces
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

sudo /etc/init.d/dbus restart
```

malcolm@malcolm-laptop:~$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ]
```

However the connect still acts the same: asks for the password and then doesn't connect (neither of the little network manager dots lights up either).

Does WPA_supplicant need to be configured in some way before Network Manager can work?

---

### Post by chele on 2007-05-26
> **myidbe said:**
> Does WPA_supplicant need to be configured in some way before Network Manager can work?Nope. It is all automatic in Feisty. You should not have to fiddle with any files or the command line.

---

