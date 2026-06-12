---
title: "Ubuntu 15.10 wifi adapter problem"
date: 2015-10-25
forum: Networking &amp; Wireless
---

### Post by muldengold on 2015-10-25
Hi,

I just swiched from Ubuntu 14.04 to to 15.10 (fresh install). Wifi via USB-dongle works well, however not directly after system start. To spring to live, the wifi adapter needs to be plugged off and plugged in newly. This is a new 15.10 problem - it didn't occur in 14.04 with the same hardware and same wifi-dongle. Can anyone help please?

Kind regards,
Sandro

---

### Post by praseodym on 2015-10-25
Please run the wireless-script from the sticky-thread and show the outputs here.

---

### Post by muldengold on 2015-10-25
Hi, 

thanks for trying to help me. After system start with inactive wifi adapter the wireless-script doesn't work, as there is no internet connection of course.
After pulling out/plugging in the wifi adapter I get the following (wifi works now):


```
########## wireless info START ##########

Report from: 25 Oct 2015 15:59 CET +0100

Booted last: 25 Oct 2015 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0234 Elan Microelectronics Corp. 
Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              548864  0
r8712u                180224  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlx00116b4ce7a8 Link encap:Ethernet  HWaddr <MAC 'wlx00116b4ce7a8' [IF]>  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlx00116b4ce7a8' [IF]>/64 Scope:Link
          inet6 addr: fd00:68b6:fc15:3902:f171:a9e3:50c5:269d/64 Scope:Global
          inet6 addr: 2a02:810a:9140:4828:f171:a9e3:50c5:269d/64 Scope:Global
          inet6 addr: fd00:68b6:fc15:3902:<IP6 'wlx00116b4ce7a8' [IF]>/64 Scope:Global
          inet6 addr: 2a02:810a:9140:4828::2/128 Scope:Global
          inet6 addr: 2a02:810a:9140:4828:<IP6 'wlx00116b4ce7a8' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:28 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32655 (32.6 KB)  TX bytes:24092 (24.0 KB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlx00116b4ce7a8  IEEE 802.11bgn  ESSID:"HITRON-3900"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'HITRON-3900' [AC1]>   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlx00116b4ce7a8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx00116b4ce7a8
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx00116b4ce7a8

##### resolv.conf #######################

nameserver 127.0.1.1
search hitronhub.home

##### network managers ##################

Installed:

	NetworkManager

Running:

root       621     1  0 15:58 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx00116b4ce7a8
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Manufacturer Realtek 
GENERAL.PRODUCT:                        RTL8191S WLAN Adapter 
GENERAL.DRIVER:                         r8712u
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx00116b4ce7a8' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/net/wlx00116b4ce7a8
GENERAL.IP-IFACE:                       wlx00116b4ce7a8
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     HITRON-3900
GENERAL.CON-UUID:                       b3e00489-df31-4054-a055-cfeed9fa8120
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b3e00489-df31-4054-a055-cfeed9fa8120 | HITRON-3900
IP4.ADDRESS[1]:                         192.168.0.12/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          hitronhub.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_interface_mtu = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        host_name = tyrion-desktop
DHCP4.OPTION[8]:                        expiry = 1446389984
DHCP4.OPTION[9]:                        domain_name = hitronhub.home
DHCP4.OPTION[10]:                       requested_domain_name = 1
DHCP4.OPTION[11]:                       next_server = 0.0.0.0
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.12
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_lease_time = 604800
DHCP4.OPTION[20]:                       requested_netbios_scope = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_ntp_servers = 1
DHCP4.OPTION[26]:                       requested_domain_name_servers = 1
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2a02:810a:9140:4828::2/128
IP6.ADDRESS[2]:                         2a02:810a:9140:4828:f171:a9e3:50c5:269d/64
IP6.ADDRESS[3]:                         fd00:68b6:fc15:3902:f171:a9e3:50c5:269d/64
IP6.ADDRESS[4]:                         2a02:810a:9140:4828:<IP6 'wlx00116b4ce7a8' [IF]>/64
IP6.ADDRESS[5]:                         fd00:68b6:fc15:3902:<IP6 'wlx00116b4ce7a8' [IF]>/64
IP6.ADDRESS[6]:                         fe80::<IP6 'wlx00116b4ce7a8' [IF]>/64
IP6.GATEWAY:                            fe80::6ab6:fcff:fe15:3902
IP6.ROUTE[1]:                           dst = 2a02:810a:9140:4828::/62, nh = fe80::6ab6:fcff:fe15:3902, mt = 600
IP6.ROUTE[2]:                           dst = fc00::/7, nh = fe80::6ab6:fcff:fe15:3902, mt = 600
IP6.ROUTE[3]:                           dst = fd00:68b6:fc15:3902::/64, nh = ::, mt = 600
IP6.ROUTE[4]:                           dst = 2a02:810a:9140:4828::/64, nh = ::, mt = 600
IP6.DNS[1]:                             2a02:810a:9140:4828::1
IP6.DOMAIN[1]:                          hitronhub.home

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard (one of many))
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

       
HITRON-3900           <MAC 'HITRON-3900' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  96      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no
```

---

### Post by praseodym on 2015-10-25
Try these module parameters

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```Also change the encryption mode in your router to pure WPA2-AES (CCMP).Please also run the script when it doesn't work (if this is not the solution!).

---

### Post by muldengold on 2015-10-25
Yes, this works - the wifi adapter comes to life! What exactly did these commands do? However after rebooting it's still the same. How can I change the encryption mode to pure WPA2-AES and (soory for the noob question) what is the reason behind this? Thanks again for your help!

---

### Post by praseodym on 2015-10-25
The network-manager disconnects often with mixed mode WPA/WPA2. The encryption is changed in your router, check the manual. Check directly after rebooting:
```

lsusb
lsmod
ifconfig -a
iwconfig
grep r8 /etc/modprobe.d/*
```

---

### Post by muldengold on 2015-10-25
Thank you - my wifi encryption is now on WPA2 (AES) only. Just read about it and I think this was good advice!

Here is the output directly after booting (wifi NOT working):
```

tyrion@tyrion-desktop:~$ lsusb
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0234 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tyrion@tyrion-desktop:~$ lsmod
Module                  Size  Used by
nls_utf8               16384  0
isofs                  40960  0
cfg80211              548864  0
r8712u                180224  0
kvm_amd                65536  0
kvm                   512000  1 kvm_amd
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
input_leds             16384  0
snd_hda_intel          36864  5
serio_raw              16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
k10temp                16384  0
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_seq_midi           16384  0
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi_event     16384  1 snd_seq_midi
shpchp                 36864  0
snd_rawmidi            32768  1 snd_seq_midi
i2c_piix4              24576  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
8250_fintek            16384  0
nuvoton_cir            20480  0
rc_core                28672  1 nuvoton_cir
mac_hid                16384  0
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
pata_acpi              16384  0
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd
radeon               1519616  3
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
r8169                  81920  0
drm_kms_helper        126976  1 radeon
mii                    16384  1 r8169
pata_atiixp            16384  0
drm                   356352  6 ttm,drm_kms_helper,radeon
ahci                   36864  3
libahci                32768  1 ahci
tyrion@tyrion-desktop:~$ ifconfig -a
enp3s0    Link encap:Ethernet  HWaddr bc:5f:f4:95:f2:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54259 (54.2 KB)  TX bytes:54259 (54.2 KB)

wlx00116b4ce7a8 Link encap:Ethernet  HWaddr 00:11:6b:4c:e7:a8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tyrion@tyrion-desktop:~$ iwconfig
enp3s0    no wireless extensions.

wlx00116b4ce7a8  unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

tyrion@tyrion-desktop:~$ grep r8 /etc/modprobe.d/*
/etc/modprobe.d/r8712u.conf:options r8712u low_power=1 power_mgnt=0 ht_enable=0
tyrion@tyrion-desktop:~$

``` 

Sandro

---

### Post by praseodym on 2015-10-25
Thats weird, the driver is loaded, but no IP for the wifi is shown. Why are your interface names looking like "wlan79tr4zihki"?
```

cat /etc/udev/rules.d/70-persistent-net.rules
```
Try deactivating IPv6 in the networking profile.

---

### Post by muldengold on 2015-10-25
The code doesn't work for me:

```

tyrion@tyrion-desktop:~$ cat /etc/udev/rules.d/70-persistent-net.rules
cat: /etc/udev/rules.d/70-persistent-net.rules: No such file or directory
tyrion@tyrion-desktop:~$ 

```

I don't know exactly how to deactivate IPv6. I can access the IPv6 settings in the network profile. The method is set on "automatic" at the moment.
Thanks again for patiently helping me.

---

### Post by praseodym on 2015-10-25
Lets try:
```

sudo touch /etc/udev/rules.d/70-persistent-net.rules
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
cat /etc/udev/rules.d/70-persistent-net.rules
```
Set IPv6 to "Ignore"

---

### Post by muldengold on 2015-10-26
Ok, I did what you said - nothing happened though?! I noticed that when plugging in the wifi adapter I get the message " You are now connected to 'none' ", even if I'm connceted to to HITRON3900 (which it used to tell me in 14.04 AND also during the 15.10 installation process). Could there be any connection? Have you got any other idea? Shall I swich back to IPv6 "automatic" for the time being?

Thanks

---

### Post by praseodym on 2015-10-26
No, lets check:
```

ping -c 2 $(route -n | grep UG | awk {'print $2'})
ping -c 2 www.ubuntuusers.de
ping -c 2 213.95.41.4 
arp -av
ip neigh show
cat /etc/resolv.conf
```

---

### Post by muldengold on 2015-10-27
That is the result after booting (no wifi):
```

tyrion@tyrion-desktop:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
tyrion@tyrion-desktop:~$ ping -c 2 www.ubuntuusers.de
ping: unknown host www.ubuntuusers.de
tyrion@tyrion-desktop:~$ ping -c 2 213.95.41.4 
connect: Network is unreachable
tyrion@tyrion-desktop:~$ arp -av
Entries: 0	Skipped: 0	Found: 0
tyrion@tyrion-desktop:~$ ip neigh show
tyrion@tyrion-desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


```

This is it after reconnecting the adapter:
```

tyrion@tyrion-desktop:~$ ping -c 2 $(route -n | grep UG | awk {'print $2'})
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.50 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.890 ms

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.890/1.195/1.501/0.307 ms
tyrion@tyrion-desktop:~$ ping -c 2 www.ubuntuusers.de
PING ubuntuusers.de (213.95.41.4) 56(84) bytes of data.
64 bytes from ha.ubuntu-eu.org (213.95.41.4): icmp_seq=1 ttl=57 time=24.2 ms
64 bytes from ha.ubuntu-eu.org (213.95.41.4): icmp_seq=2 ttl=57 time=20.6 ms

--- ubuntuusers.de ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 20.600/22.443/24.286/1.843 ms
tyrion@tyrion-desktop:~$ ping -c 2 213.95.41.4 
PING 213.95.41.4 (213.95.41.4) 56(84) bytes of data.
64 bytes from 213.95.41.4: icmp_seq=1 ttl=57 time=23.9 ms
64 bytes from 213.95.41.4: icmp_seq=2 ttl=57 time=21.9 ms

--- 213.95.41.4 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 21.915/22.956/23.998/1.052 ms
tyrion@tyrion-desktop:~$ arp -av
hitronhub.home (192.168.0.1) at 68:b6:fc:15:39:02 [ether] on wlx00116b4ce7a8
Entries: 1	Skipped: 0	Found: 1
tyrion@tyrion-desktop:~$ ip neigh show
192.168.0.1 dev wlx00116b4ce7a8 lladdr 68:b6:fc:15:39:02 REACHABLE
fe80::6ab6:fcff:fe15:3902 dev wlx00116b4ce7a8 lladdr 68:b6:fc:15:39:02 router STALE
tyrion@tyrion-desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hitronhub.home


```

---

### Post by praseodym on 2015-10-27
There are no nameservers listed after the boot. Add the nameserver 127.0.1.1 and the domain in the network-manager profile:
> ```

nameserver 127.0.1.1
search hitronhub.home
```

---

### Post by muldengold on 2015-10-28
Sorry for the delay. I added the nameserver 127.0.1.1 to Additional DNS Servers and hitronhub.home to search domains in the IPv4 settings. But didn't work. Any other ideas, please?

Sandro

---

### Post by praseodym on 2015-10-28
Remove it again and try:
```

sudo apt-get remove --purge resolvconf
```
Reboot. If "cat /etc/resolv.conf" shows no output, then run
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by muldengold on 2015-10-28
After
```
sudo apt-get remove --purge resolvconf
``` I had to reboot - but no wifi; then

```

tyrion@tyrion-desktop:~$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
[sudo] password for tyrion: 
tee: /etc/resolv.conf: No such file or directory
nameserver 8.8.8.8
nameserver 8.8.4.4
tyrion@tyrion-desktop:~$ sudo service network-manager restart

```

It connected to my Wifi-network, but failed to reconnect automatically after rebooting. Thanks for your patience.

---

### Post by praseodym on 2015-10-28
Then add 192.168.0.1 plus these nameservers to the profile

---

### Post by muldengold on 2015-10-28
I can only add one additional nameserver, can I not??? I added 192.168.01. Same as before, unfortunately.  

As before, after reconnecting the adapter I'm connected via wifi to the internet but apparently not to my home network (connected to 'none' - the wifi symbol also looks greyish but now white). To what am I connected then?? I sort of have lost any understanding what I'm doing here.

---

### Post by praseodym on 2015-10-28
Separate the nameservers by commas

---

### Post by muldengold on 2015-10-29
Sorry didn't work. 

I added 3 snapshots of the network settings dialog after I replugged the wifi adapter.The first shows that I'm apparently on HITRON3900. Opening that network tells me that I'm not connected (second screenshot) and the third is the settings.

[ATTACH=CONFIG]265238[/ATTACH][ATTACH=CONFIG]265239[/ATTACH][ATTACH=CONFIG]265240[/ATTACH]

Perhaps this gives you any clue? Thanks.

---

### Post by muldengold on 2015-10-29
Forgot to add a screenshot from the IPv4 settings...

[ATTACH=CONFIG]265241[/ATTACH]

---

### Post by praseodym on 2015-10-29
You need "Infrastructure" mode, not "Ad-hoc", remove the profile and set-up a new one.

---

### Post by muldengold on 2015-10-29
I deleted the profile and set up a new one from scratch with "infrastructure" mode but didn't help. Any other suggestion what I could do please? Going back to 14.04 might solve it but I'd rather stick with 15.10.

---

### Post by praseodym on 2015-10-29
Do not use the Device MAC address, leave it empty.

---

### Post by muldengold on 2015-10-30
I left it empty - but didn't work for me. :confused:

---

### Post by praseodym on 2015-10-30
The file is emtpy after booting?

cat /etc/resolv.conf

---

### Post by muldengold on 2015-10-30
That is the file's content after booting:

# Generated by NetworkManager
nameserver 127.0.1.1

and that after reconnecting:

# Generated by NetworkManager
search hitronhub.home hitronhub.home.
nameserver 127.0.1.1

---

### Post by muldengold on 2015-11-02
I gave up and went back to 14.04. This solved the problem. I plan to upgrade to 16.04 next year and do hope that the problem will not re-appear (if so I might get back to this thread). However, thanks a lot for your help praseodym, which is really appreciated!!!

---

### Post by gaurav26 on 2016-05-28
Hello, I am also facing the problem with Wireless Adapter over Ubuntu 15.10 and Lenovo Thinkpad E420 machine. I went through the post and figured out that I have to post the output of a script. Please help.





########## wireless info START ##########


Report from: 28 May 2016 20:09 CEST +0200


Booted last: 28 May 2016 00:00 CEST +0200


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


##### kernel ############################


Linux 4.2.0-35-generic #40-Ubuntu SMP Tue Mar 15 22:15:45 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:21e2]
	Kernel driver in use: r8169


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]


##### lsusb #############################


Bus 002 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 002 Device 003: ID 24ae:2010  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b257 Chicony Electronics Co., Ltd Lenovo Integrated Camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6365184  0
mac80211              745472  0
cfg80211              557056  2 wl,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:212.201.86.168  Bcast:212.201.87.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF1]>/64 Scope:Link
          inet6 addr: 2002:d4c9:5676:a:<IP6 'enp2s0' [IF1]>/64 Scope:Global
          inet6 addr: fec0::a:<IP6 'enp2s0' [IF1]>/64 Scope:Site
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16192663 (16.1 MB)  TX bytes:1447133 (1.4 MB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         212.201.86.1    0.0.0.0         UG    100    0        0 enp2s0
129.70.182.19   212.201.86.1    255.255.255.255 UGH   100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
212.201.86.0    0.0.0.0         255.255.254.0   U     100    0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search dhcp.uni-bielefeld.de uni-bielefeld.de


##### network managers ##################


Installed:


	NetworkManager


Running:


root       636     1  0 19:40 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b725c4cf-225b-4f3f-a025-7cfe3702630c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b725c4cf-225b-4f3f-a025-7cfe3702630c | Wired connection 1
IP4.ADDRESS[1]:                         212.201.86.168/23
IP4.GATEWAY:                            212.201.86.1
IP4.ROUTE[1]:                           dst = 129.70.182.19/32, nh = 212.201.86.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             129.70.182.19
IP4.DNS[2]:                             129.70.199.6
IP4.DOMAIN[1]:                          dhcp.studentenwerk-bielefeld.de
IP4.WINS[1]:                            129.70.4.79
IP4.WINS[2]:                            129.70.4.80
DHCP4.OPTION[1]:                        domain_name_servers = 129.70.182.19 129.70.199.6
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        netbios_name_servers = 129.70.4.79 129.70.4.80
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        domain_search = dhcp.uni-bielefeld.de. uni-bielefeld.de.
DHCP4.OPTION[8]:                        requested_domain_name = 1
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       expiry = 1464500441
DHCP4.OPTION[11]:                       next_server = 0.0.0.0
DHCP4.OPTION[12]:                       domain_name = dhcp.studentenwerk-bielefeld.de
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       broadcast_address = 212.201.87.255
DHCP4.OPTION[16]:                       routers = 212.201.86.1
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       dhcp_lease_time = 43200
DHCP4.OPTION[19]:                       ip_address = 212.201.86.168
DHCP4.OPTION[20]:                       subnet_mask = 255.255.254.0
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_domain_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 212.201.86.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 129.70.182.19
IP6.ADDRESS[1]:                         2002:d4c9:5676:a:<IP6 'enp2s0' [IF1]>/64
IP6.ADDRESS[2]:                         fec0::a:<IP6 'enp2s0' [IF1]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'enp2s0' [IF1]>/64
IP6.GATEWAY:                            fe80::21d6:bba0:b37d:5b12
IP6.ROUTE[1]:                           dst = 2002::/16, nh = fe80::21d6:bba0:b37d:5b12, mt = 100
IP6.ROUTE[2]:                           dst = fec0:0:0:a::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = 2002:d4c9:5676:a::/64, nh = ::, mt = 100


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


[[/etc/NetworkManager/system-connections/GTPPRIME]] (600 root)
[connection] id=GTPPRIME | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=GTPPRIME
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/GTPPRIME~]] (600 root)
[connection] id=GTPPRIME | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=GTPPRIME
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Anila]] (600 root)
[connection] id=Anila | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Anila
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/gkmmg]] (600 root)
[connection] id=gkmmg | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=gkmmg
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


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


enp2s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/4.2.0-35-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D2:CD:13:F4:5F:A3:B0:12:FC:89:B8:D5:00:F9:1D:CC:A4:D9:E0:A8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


8192cu


##### modprobe options ##################


[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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
blacklist rtl8192cu


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
install rtl8xxxu /bin/false


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=0
options rtl8192ce fwlps=0
options rtl8192ce swenc=1


[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[    3.001657] wl: module license 'MIXED/Proprietary' taints kernel.
[    4.115476] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.263806] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[    4.263891] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    5.885311] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    5.927043] r8169 0000:02:00.0 enp2s0: link up
[    5.927060] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


########## wireless info END ############

---

