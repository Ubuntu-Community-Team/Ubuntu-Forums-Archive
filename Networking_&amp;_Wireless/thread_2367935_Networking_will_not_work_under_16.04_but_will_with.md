---
title: "Networking will not work under 16.04 but will with Windows on dual boot laptop"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by bvargo on 2017-08-04
I went to use my dual-boot laptop for the first time in a couple of weeks and am unable to connect to the internet in Ubuntu 16.04.  I am traveling and tried via WiFi at two different hotels as well as McDonald's.  I also tried via my phone both through WiFi and USB tethering.  I can connect with Windows so evidently it is not a hardware issue.  I've tried the obvious things of restarting the network services and rebooting but to no avail.  I could really use some help as to how to troubleshoot this because I don't even know where to begin.  Because I can only connect to the internet via Windows, it is going to be a bit harder to troubleshoot as I will have to go back and forth b/w the two unless I can pull it from Ext2 Volume Manager.  Thanks in advance.

---

### Post by Hadaka on 2017-08-05
Hi, did Ubuntu 16.04 used to work ?
Please post the output of..
```
uname -r
lspci -n | awk '/0200|0280/{print$3}'
lsmod | awk '/cfg80211/{print$4}'
rfkill list | awk '/yes/'
nmcli nm | awk '{print$1,$2,$3,$4}'
```
Thanks.

---

### Post by BenginM on 2017-08-05
Well, we can't assist you with out looking at the system logs .. network cards/driver informations  .. **" If you aren't able to connect to the internet with the affected system, including via a wired connection, just [navigate to this link ]("https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385")** and follow the instructions there on how to the run wireless script without an internet connection. "

---

### Post by vasa1 on 2017-08-05
@BenginM, did you thoroughly read the link you cited?> If you aren't able to connect to the internet with the affected system, including via a wired connection, ...

---

### Post by BenginM on 2017-08-05
vasa1 , i barely open that sticky , and i don't remember that bit .. i shall edit my post ,thank you.

---

### Post by bvargo on 2017-08-05
Yes, it used to work with 16.04, no idea why it just stopped.  I did try using bluetooth for my wireless but I'm fairly sure that it worked with 802.11b/g after that.

Here is the requested info with a few additional items.  Apparently nmcli nm doesn't work so I just ran nmcli n.

```

:~$ uname -r
4.4.0-83-generic

:~$ lspci -n | awk '/0200|0280/{print$3}'
8086:08b3
10ec:8136

:~$ lsmod | awk '/cfg80211/{print$4}'
iwlwifi,mac80211,iwlmvm


:~$ rfkill list | awk '/yes/'

:~$ nmcli nm | awk '{print$1,$2,$3,$4}'
Error: Object 'nm' is unknown, try 'nmcli help'.


SOME OTHER THINGS:

:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

:~$ nmcli n
enabled


```

---

### Post by bvargo on 2017-08-05
Here is the script output.  I changed the username and some of the SSIDs.  NB:  I turned off the bluetooth so now the rfkill lists it as "Soft blocked: yes" unlike my previous post which lists it as no.

```


########## wireless info START ##########

Report from: 05 Aug 2017 07:26 EDT -0400

Booted last: 05 Aug 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

06:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
    Kernel driver in use: iwlwifi

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:06b0]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 0bda:5683 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 18d1:4ee1 Google Inc. Nexus 4 / 10
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
iwlmvm                311296  0
snd_soc_rt5640        114688  0
mac80211              737280  1 iwlmvm
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
iwlwifi               200704  1 iwlmvm
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:26159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1793310 (1.7 MB)  TX bytes:1793310 (1.7 MB)

wlp6s0    Link encap:Ethernet  HWaddr <MAC 'wlp6s0' [IF2]>  
          inet addr:192.168.43.3  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::11c0:d7f2:e882:dc99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1545666 (1.5 MB)  TX bytes:186450 (186.4 KB)

##### iwconfig ##########################

enp7s0    no wireless extensions.

lo        no wireless extensions.

wlp6s0    IEEE 802.11abgn  ESSID:"name.suppressed-m"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'name.suppressed-m' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    600    0        0 wlp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp6s0
192.168.43.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp6s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       859     1  0 07:08 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp6s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-83-generic
GENERAL.FIRMWARE-VERSION:               17.459231.0
GENERAL.HWADDR:                         <MAC 'wlp6s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0/net/wlp6s0
GENERAL.IP-IFACE:                       wlp6s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     name.suppressed-m
GENERAL.CON-UUID:                       0642e095-2f4b-423b-9bac-8938b36bce6d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15,19,20,6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6731bc0d-f6e4-41d6-a929-26bedd0e908d | Rodeway Inn
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   0642e095-2f4b-423b-9bac-8938b36bce6d | name.suppressed-m
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   6e8d6960-fc08-43b1-91d2-632e1e0701b1 | WIN_d1ff_0
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   47cf84d0-dde6-4ab4-bc16-d12d69c2652c | name.suppressed_white 1
IP4.ADDRESS[1]:                         192.168.43.3/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.3
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1501920521
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = inspiron
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::11c0:d7f2:e882:dc99/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/enp7s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
name.suppressed-m  <MAC 'name.suppressed-m' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  84      â–‚â–„â–†â–ˆ  WPA2      yes     * 
Rodeway Inn  <MAC 'Rodeway Inn' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  47      â–‚â–„__  --        no        
Rodeway Inn  <MAC 'Rodeway Inn' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  35      â–‚â–„__  --        no        
Rodeway Inn  <MAC 'Rodeway Inn' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  32      â–‚â–„__  --        no        

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

[[/etc/NetworkManager/system-connections/name.suppressed_black]] (600 root)
[connection] id=name.suppressed_black | type=wifi | permissions=user:username.suppressed:;
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=name.suppressed_black
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/name.suppressed_white 2]] (600 root)
[connection] id=name.suppressed_white 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=name.suppressed_white
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/name.suppressed_white 1]] (600 root)
[connection] id=name.suppressed_white 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=name.suppressed_white
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/name.suppressed_white]] (600 root)
[connection] id=name.suppressed_white | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=name.suppressed_white
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rodeway Inn]] (600 root)
[connection] id=Rodeway Inn | type=wifi | permissions=user:username.suppressed:;
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=Rodeway Inn
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIN_d1ff_EXT2]] (600 root)
[connection] id=WIN_d1ff_EXT2 | type=wifi | permissions=user:username.suppressed:;
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=WIN_d1ff_EXT2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIN_d1ff_EXT1]] (600 root)
[connection] id=WIN_d1ff_EXT1 | type=wifi | permissions=user:username.suppressed:;
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=WIN_d1ff_EXT1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Library-Public]] (600 root)
[connection] id=Library-Public | type=wifi | permissions=user:username.suppressed:;
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=Library-Public
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIN_d1ff_0]] (600 root)
[connection] id=WIN_d1ff_0 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=WIN_d1ff_0
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIN_d1ff_EXT]] (600 root)
[connection] id=WIN_d1ff_EXT | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=WIN_d1ff_EXT
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/name.suppressed-m]] (600 root)
[connection] id=name.suppressed-m | type=wifi | permissions=user:username.suppressed:;
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=name.suppressed-m
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIN_d1ff]] (600 root)
[connection] id=WIN_d1ff | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp6s0' [IF2]> | mac-address-blacklist= | ssid=WIN_d1ff
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

enp7s0    no frequency information.

lo        no frequency information.

wlp6s0    32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp7s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp6s0    Scan completed :
          Cell 01 - Address: <MAC 'name.suppressed-m' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"name.suppressed-m"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007a50c4d90
                    Extra: Last beacon: 5852ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Rodeway Inn' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Rodeway Inn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f68b9ba8bb
                    Extra: Last beacon: 5852ms ago
          Cell 03 - Address: <MAC 'Rodeway Inn' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"Rodeway Inn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000046a331624c
                    Extra: Last beacon: 5692ms ago
          Cell 04 - Address: <MAC 'Rodeway Inn' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"Rodeway Inn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f68b3da2d8
                    Extra: Last beacon: 5552ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     6E932A4867C43B598CE49EB
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-83-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     EFF66BE1B3C123F1C2078FB
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     4116E844336D79483D28F6F
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-83-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     48C96882CCDC964173BE1D1
depends:        
intree:         Y
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

coretemp

##### modprobe options ##################

[/etc/modprobe.conf]
options parport_pc io=0x378 irq=7 dma=3

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
blacklist rtsx_usb_sdmmc
blacklist rtsx_usb_ms
blacklist rtsx_usb

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.143637] hid-rmi 0018:06CB:78F1.0001: firmware id: 2019836
[   13.232277] iwlwifi 0000:06:00.0 wlp6s0: renamed from wlan0
[   36.130480] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   36.417460] r8169 0000:07:00.0 enp7s0: link down
[   36.417516] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   36.460739] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready
[   36.460845] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   36.588674] IPv6: ADDRCONF(NETDEV_UP): wlp6s0: link is not ready (repeated 2 times)
[   48.703255] wlp6s0: authenticate with <MAC 'Rodeway Inn' [AC3]>
[   48.705018] wlp6s0: send auth to <MAC 'Rodeway Inn' [AC3]> (try 1/3)
[   48.706814] wlp6s0: authenticated
[   48.706941] iwlwifi 0000:06:00.0 wlp6s0: disabling HT as WMM/QoS is not supported by the AP
[   48.706947] iwlwifi 0000:06:00.0 wlp6s0: disabling VHT as WMM/QoS is not supported by the AP
[   48.708866] wlp6s0: associate with <MAC 'Rodeway Inn' [AC3]> (try 1/3)
[   48.711154] wlp6s0: RX AssocResp from <MAC 'Rodeway Inn' [AC3]> (capab=0x421 status=0 aid=1)
[   48.712226] wlp6s0: associated
[   48.712262] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[   79.385134] wlp6s0: deauthenticating from <MAC 'Rodeway Inn' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   82.768617] wlp6s0: authenticate with <MAC 'name.suppressed-m' [AC1]>
[   82.771957] wlp6s0: send auth to <MAC 'name.suppressed-m' [AC1]> (try 1/3)
[   82.773741] wlp6s0: authenticated
[   82.774933] wlp6s0: associate with <MAC 'name.suppressed-m' [AC1]> (try 1/3)
[   82.780254] wlp6s0: RX AssocResp from <MAC 'name.suppressed-m' [AC1]> (capab=0x411 status=0 aid=1)
[   82.780874] wlp6s0: associated
[   82.873199] wlp6s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'name.suppressed-m' [AC1]>

########## wireless info END ############



```

---

### Post by bvargo on 2017-08-05
For the record, at present I have no access to a wired connection other than via USB tethering to my phone which, as previously mentioned, is not working.  I should be able to do that tonight or tomorrow.

Thanks for the help.

---

### Post by Hadaka on 2017-08-05
Hi, please open a terminal and do..
#none of this needs internet access.

```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a  /etc/modprobe.d/iwlwifi.conf
```
*There were a bunch of...Rodeway Inn..access points..so it was roaming between them, if you want
to attach to that ssid..i would suggest binding to the strongest signal mac address to the one of your choice.
see attached..
[ATTACH=CONFIG]276260[/ATTACH]
#To find the access point Mac Address with the highest  "Quality" signal..
```
sudo iwlist wlp6s0 scan | awk '/Cell|Quality|ESSID/'
```

---

### Post by bvargo on 2017-08-05
So I don't know how to figure out the MAC address for the strongest signal, but they're all b/w -30 and -39 dB so they should be fairly close to each other.

Here is the requested info, the first couple of commands did not return anything.  I should note that the Rodeway Inn WiFi does require a login and password which I have not been able to enter in either opera or chrome.  That said, tethering to my phone via WiFi or USB does not require such a login, just the WiFi password and that has not worked either.  

```

:~$ echo "options iwlwifi 11n_disable=8" | sudo tee -a  /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=8

:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.17.1.1      0.0.0.0         UG    600    0        0 wlp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp6s0
172.17.0.0      0.0.0.0         255.255.0.0     U     600    0        0 wlp6s0

:~$ ping 172.17.1.1
PING 172.17.1.1 (172.17.1.1) 56(84) bytes of data.
64 bytes from 172.17.1.1: icmp_seq=1 ttl=64 time=71.6 ms
64 bytes from 172.17.1.1: icmp_seq=2 ttl=64 time=3.25 ms
64 bytes from 172.17.1.1: icmp_seq=3 ttl=64 time=4.21 ms
^C
--- 172.17.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.252/26.372/71.651/32.019 ms

:~$ ifconfig
enp7s0    Link encap:Ethernet  HWaddr 14:18:77:c7:bb:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:220545 (220.5 KB)  TX bytes:220545 (220.5 KB)

wlp6s0    Link encap:Ethernet  HWaddr e4:02:9b:2f:10:61  
          inet addr:172.17.100.111  Bcast:172.17.255.255  Mask:255.255.0.0
          inet6 addr: fe80::4905:47d:a6c5:9523/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:764053 (764.0 KB)  TX bytes:215478 (215.4 KB)

```

---

### Post by bvargo on 2017-08-05
```

:~$ sudo iwlist wlp6s0 scan | awk '/Cell|Quality|ESSID/'
          Cell 01 - Address: 0C:85:25:9E:AE:4E
                    Quality=47/70  Signal level=-63 dBm  
                    ESSID:"TPA"
          Cell 08 - Address: 0C:85:25:9E:A9:2F
                    Quality=50/70  Signal level=-60 dBm  
                    ESSID:"TPA"
          Cell 10 - Address: 0C:85:25:9E:BF:BF
                    Quality=41/70  Signal level=-69 dBm  
                    ESSID:"TPA"
          Cell 12 - Address: 2C:36:F8:0C:73:7F
                    Quality=37/70  Signal level=-73 dBm  
                    ESSID:"TPA"
          Cell 15 - Address: 0C:85:25:9E:BF:5E
                    Quality=52/70  Signal level=-58 dBm  
                    ESSID:"TPA"

```

Cell 01 (0C:85:25:9E:AE:4E) is the only BSSID MAC listed in the edit connections dialog, but 47 vs. 52 shouldn't make a difference.  Again, Windows will connect but Ubuntu will not...so any other thoughts?

---

### Post by Hadaka on 2017-08-05
Hi,please open a terminal and do..
```
route -n | awk 'FNR==3{print$2}'
ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/'
ping -c2 8.8.8.8 | awk '/ping/,/2 /'
ping -c2 google.com | awk '/ping/,/2 /'
```

**If you have 100% loss on 8.8.8.8 or google.com then configure like attached..
*Change method to -> Automatic (DHCP) addresses only
[ATTACH=CONFIG]276269[/ATTACH]
Thanks.

---

### Post by bvargo on 2017-08-06
So, I am able to connect to my home network in Ubuntu via WiFi and a wired ethernet connection and can ping my router as well as another computer on my network.  Unfortunately, I cannot get to anything outside of my local network, e.g. cannot ping google.com nor 8.8.8.8 and cannot use the internet via a web browser.  There is no problem doing any of this in Windows (which I am currently using to post this).  

Still looking for a way to fix this or re-install networking...

---

### Post by bvargo on 2017-08-06
> **Hadaka said:**
> Hi,please open a terminal and do..
```
route -n | awk 'FNR==3{print$2}'
ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/'
ping -c2 8.8.8.8 | awk '/ping/,/2 /'
ping -c2 google.com | awk '/ping/,/2 /'
```

**If you have 100% loss on 8.8.8.8 or google.com then configure like attached..
*Change method to -> Automatic (DHCP) addresses only
[ATTACH=CONFIG]276269[/ATTACH]
Thanks.

I did not see your post (quoted) until after I posted my previous one.  My default configuration at home is fixed IP of 192.168.1.3 and DNS servers of 8.8.8.8, 151.197.0.39 which is what I used when I posted the previous info as well as the following:
```

:~$ route -n | awk 'FNR==3{print$2}'
192.168.1.1


:~$ ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/'
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1007ms


:~$ ping -c2 8.8.8.8 | awk '/ping/,/2 /'
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms


:~$ ping -c2 google.com | awk '/ping/,/2 /'
ping: unknown host google.com

```

I'm not sure what changing to a DHCP-assigned IP and DNS servers of 8.8.4.4,8.8.8.8 is going to change, but I did so.

---

### Post by Hadaka on 2017-08-06
Hi, here is some info from my network...
```
hadaka:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0 
```
*The IP address to my router...Exactly the same as yours. The Gateway address
*This command .."route -n | awk 'FNR==3{print$2}' " means..route -n and print the 3rd line second field."
*The gateway address to the router.
```
hadaka:~$ route -n | awk 'FNR==3{print$2}'
192.168.1.1
``` My route / gateway is Exactly the same as yours.
*This command means ping the Gateway address../ the router ...192.168.1.1
```
hadaka:~$ ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/'
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
```
**[COLOR=#ff0000]*[/COLOR]**You have 100% Loss attempting to ping your router..
```
:~$ ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/' 
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 0 received, **[COLOR=#ff0000]100%[/COLOR]** packet loss, time 1007ms
```
You state..
"#My default configuration at home is fixed IP of 192.168.1.3 and DNS servers of 8.8.8.8, 151.197.0.39"
Try an "unfixed" address...allow the router to assign ~OR~ configure your ssid IPv4 connection as attached..
** Change Method to Manual
[ATTACH=CONFIG]276279[/ATTACH]
Thanks

---

### Post by bvargo on 2017-08-06
Hello,

I didn't notice the 100% loss, and it is odd, because I *was* able to ping 192.168.1.1 and 192.168.1.2 before that.  Anyway, attached is the editing network connections screen shot.  For some reason, even thought I put 255.255.255.0 in for the Netmask and save it, it comes up as 24...but google tells me that means 255.255.255.0.

[ATTACH=CONFIG]276280[/ATTACH]



Anyway, here is the ping info:

```

:~$ ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/' 
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms

:~$ ping -c2 192.168.1.2|awk '/ping|loss/' 
--- 192.168.1.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms

```

---

### Post by Hadaka on 2017-08-07
ok, glad to see you can now ping your router...192.168.1.1
what is ?? 192.168.1.2 ?? I thought your fixed address was
192.168.1.3 ...which should really be 192.168.1.223 to be out of
the basic DHCP assignment range. The router and wifi card work with windows.
This only means both are functional. Windows runs fine with a TKIP setting, not
so with Ubuntu/linux.Try first undoing any and all fixed addresses and allow the
router to do an automatic dhcp assignment. Tripple check everything in the router
settings...like checking that it is set to b/g/n not just n only. It acts like  dns problem
but the last change that was done should have fixed that.
please also post the output of...
```
cat /etc/network/interfaces
```
thanks.

---

### Post by bvargo on 2017-08-07
Thanks for the response.  I'll jump over to the Ubuntu side to do what needs to be done in the  morning, but to answer a couple of your questions, 192.168.1.2 is  another computer on the network and DHCP only assigns addresses b/w  192.168.1.11-192.168.1.254.  The security was already set to WPA2-PSK [AES].  I think it  will only do b/g/n in 2.4 GHz mode:
[ATTACH=CONFIG]276281[/ATTACH]

Thanks

---

### Post by bvargo on 2017-08-07
Hi,  I'm guessing you meant /etc/network/interfaces b/c cat network interfaces resulted in "No such file or directory."
```

:/etc/network$ cat network interfaces
 No such file or directory
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

[ATTACH=CONFIG]276286[/ATTACH]

Here is the config info in DHCP/Address only mode:
```

:/etc/network$ ifconfig wlp6s0
wlp6s0    Link encap:Ethernet  HWaddr e4:02:9b:2f:10:61  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::78d4:e73d:6f1b:59f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:887402 (887.4 KB)  TX bytes:119910 (119.9 KB)

```

Ping results (forgot to include ping results for 192.168.1.1 but it worked):
```
 
:/etc/network$ ping -c2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1007ms

:/etc/network$ ping -c2 google.com
ping: unknown host google.com

```

In Windows:
```

C:\Users>ping 8.8.8.8

Ping statistics for 8.8.8.8:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 18ms, Average = 17ms

C:\Users>ping 151.197.0.39

Ping statistics for 151.197.0.39:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 9ms, Maximum = 15ms, Average = 11ms

C:\Users>ping google.com

Ping statistics for 172.217.3.46:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 12ms, Maximum = 14ms, Average = 13ms

```

---

### Post by Hadaka on 2017-08-07
please post the output of..
```
cat /var/log/syslog | grep -i dns
```
*If there is minimal output , then try..
```
cat /var/log/syslog.1 | grep -i dns
```
and just to humor me, please do and post..
```
ping -c2 localhost | awk '/ping/,/2/'
ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/'
```
Thanks.

---

### Post by bvargo on 2017-08-07
Thanks, the output is below and the first syslog output was plenty long.  It wouldn't be a DNS issue if I cannot ping an outside IP address (e.g. 8.8.8.8), right?

```

:~$ cat /var/log/syslog | grep -i dns
Aug  7 05:35:42 ins avahi-daemon[913]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 05:35:42 ins avahi-daemon[913]: Interface wlp6s0.IPv6 no longer relevant for mDNS.
Aug  7 05:35:42 ins avahi-daemon[913]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 05:35:42 ins avahi-daemon[913]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 05:35:42 ins NetworkManager[900]: <info>  [1502098542.1910] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 05:35:42 ins dnsmasq[1871]: setting upstream servers from DBus
Aug  7 05:35:46 ins avahi-daemon[913]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 05:35:46 ins avahi-daemon[913]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 05:35:46 ins NetworkManager[900]: <info>  [1502098546.6069] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 05:35:46 ins NetworkManager[900]: <info>  [1502098546.6071] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 05:35:46 ins dnsmasq[1871]: setting upstream servers from DBus
Aug  7 05:35:46 ins dnsmasq[1871]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 05:35:46 ins dnsmasq[1871]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 05:35:47 ins avahi-daemon[913]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 05:35:47 ins avahi-daemon[913]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 05:44:57 ins NetworkManager[900]: <info>  [1502099097.1682] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 05:44:57 ins avahi-daemon[913]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 05:44:57 ins avahi-daemon[913]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 05:44:57 ins avahi-daemon[913]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 05:44:57 ins avahi-daemon[913]: Interface wlp6s0.IPv6 no longer relevant for mDNS.
Aug  7 05:44:57 ins dnsmasq[1871]: setting upstream servers from DBus
Aug  7 05:44:57 ins NetworkManager[4952]: <info>  [1502099097.2401] dns-mgr[0x205f960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 05:47:16 ins systemd[1]: Starting Clean up any mess left by 0dns-up...
Aug  7 05:47:16 ins systemd[1]: Started Clean up any mess left by 0dns-up.
Aug  7 05:47:16 ins systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Aug  7 05:47:16 ins systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Aug  7 05:47:16 ins systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Aug  7 05:47:16 ins kernel: [    0.956999] Key type dns_resolver registered
Aug  7 05:47:19 ins NetworkManager[839]: <info>  [1502099239.8619] dns-mgr[0xc8d960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 05:50:41 ins NetworkManager[2627]: <info>  [1502099441.7525] dns-mgr[0x1e5b950]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 05:53:10 ins avahi-daemon[872]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 05:53:10 ins avahi-daemon[872]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 05:54:35 ins avahi-daemon[872]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 05:54:35 ins avahi-daemon[872]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 05:54:39 ins avahi-daemon[872]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 05:54:39 ins avahi-daemon[872]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 05:56:00 ins NetworkManager[3311]: <info>  [1502099760.8191] dns-mgr[0x1fb5960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 05:56:01 ins avahi-daemon[872]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 05:56:01 ins avahi-daemon[872]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 05:56:08 ins avahi-daemon[872]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 05:56:08 ins avahi-daemon[872]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 05:56:21 ins avahi-daemon[872]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 05:56:21 ins avahi-daemon[872]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 05:56:21 ins NetworkManager[3311]: <info>  [1502099781.8948] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 05:56:21 ins NetworkManager[3311]: <info>  [1502099781.8950] dns-plugin[0x1fe4900]: starting dnsmasq...
Aug  7 05:56:21 ins NetworkManager[3311]: <info>  [1502099781.9163] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 05:56:21 ins dnsmasq[3433]: started, version 2.75 cache disabled
Aug  7 05:56:21 ins dnsmasq[3433]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Aug  7 05:56:21 ins dnsmasq[3433]: DBus support enabled: connected to system bus
Aug  7 05:56:21 ins dnsmasq[3433]: warning: no upstream servers configured
Aug  7 05:56:31 ins NetworkManager[3311]: <info>  [1502099791.9740] dnsmasq[0x1fe4900]: dnsmasq appeared as :1.126
Aug  7 05:56:31 ins dnsmasq[3433]: setting upstream servers from DBus
Aug  7 05:56:31 ins dnsmasq[3433]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 05:56:31 ins dnsmasq[3433]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 05:59:23 ins systemd[1]: Starting Clean up any mess left by 0dns-up...
Aug  7 05:59:23 ins systemd[1]: Started Clean up any mess left by 0dns-up.
Aug  7 05:59:23 ins systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Aug  7 05:59:23 ins systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Aug  7 05:59:23 ins kernel: [    0.969576] Key type dns_resolver registered
Aug  7 05:59:24 ins systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Aug  7 05:59:27 ins NetworkManager[910]: <info>  [1502099967.3854] dns-mgr[0x115a960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 05:59:55 ins avahi-daemon[905]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 05:59:55 ins avahi-daemon[905]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 06:00:04 ins avahi-daemon[905]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 06:00:04 ins avahi-daemon[905]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 06:00:04 ins NetworkManager[910]: <info>  [1502100004.4818] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 06:00:04 ins NetworkManager[910]: <info>  [1502100004.4819] dns-plugin[0x1189900]: starting dnsmasq...
Aug  7 06:00:04 ins NetworkManager[910]: <info>  [1502100004.7582] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:00:05 ins dnsmasq[2162]: started, version 2.75 cache disabled
Aug  7 06:00:05 ins dnsmasq[2162]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Aug  7 06:00:05 ins dnsmasq[2162]: DBus support enabled: connected to system bus
Aug  7 06:00:05 ins dnsmasq[2162]: warning: no upstream servers configured
Aug  7 06:00:08 ins NetworkManager[910]: <info>  [1502100008.7050] dnsmasq[0x1189900]: dnsmasq appeared as :1.90
Aug  7 06:00:08 ins dnsmasq[2162]: setting upstream servers from DBus
Aug  7 06:00:08 ins dnsmasq[2162]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 06:00:08 ins dnsmasq[2162]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 06:01:43 ins NetworkManager[910]: <info>  [1502100103.2203] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:01:43 ins avahi-daemon[905]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 06:01:43 ins avahi-daemon[905]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 06:01:43 ins avahi-daemon[905]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:01:43 ins avahi-daemon[905]: Interface wlp6s0.IPv6 no longer relevant for mDNS.
Aug  7 06:01:43 ins dnsmasq[2162]: setting upstream servers from DBus
Aug  7 06:01:43 ins NetworkManager[2844]: <info>  [1502100103.2886] dns-mgr[0x2608a90]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 06:01:51 ins avahi-daemon[905]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:01:51 ins avahi-daemon[905]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 06:01:58 ins avahi-daemon[905]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 06:01:58 ins avahi-daemon[905]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 06:01:58 ins NetworkManager[2844]: <info>  [1502100118.6032] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 06:01:58 ins NetworkManager[2844]: <info>  [1502100118.6197] dns-plugin[0x2642d00]: starting dnsmasq...
Aug  7 06:01:58 ins NetworkManager[2844]: <info>  [1502100118.6212] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:01:58 ins dnsmasq[2989]: started, version 2.75 cache disabled
Aug  7 06:01:58 ins dnsmasq[2989]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Aug  7 06:01:58 ins dnsmasq[2989]: DBus support enabled: connected to system bus
Aug  7 06:01:58 ins dnsmasq[2989]: warning: no upstream servers configured
Aug  7 06:01:58 ins NetworkManager[2844]: <info>  [1502100118.6480] dnsmasq[0x2642d00]: dnsmasq appeared as :1.115
Aug  7 06:01:58 ins dnsmasq[2989]: setting upstream servers from DBus
Aug  7 06:01:58 ins dnsmasq[2989]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 06:01:58 ins dnsmasq[2989]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 06:03:32 ins systemd[1]: Starting Clean up any mess left by 0dns-up...
Aug  7 06:03:32 ins systemd[1]: Started Clean up any mess left by 0dns-up.
Aug  7 06:03:32 ins systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Aug  7 06:03:32 ins systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Aug  7 06:03:32 ins kernel: [    0.955465] Key type dns_resolver registered
Aug  7 06:03:37 ins systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Aug  7 06:03:44 ins NetworkManager[885]: <info>  [1502100224.0344] dns-mgr[0x13a5960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 06:03:59 ins avahi-daemon[816]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:03:59 ins avahi-daemon[816]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 06:04:20 ins avahi-daemon[816]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 06:04:20 ins avahi-daemon[816]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 06:04:20 ins NetworkManager[885]: <info>  [1502100260.8521] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 06:04:20 ins NetworkManager[885]: <info>  [1502100260.8522] dns-plugin[0x13d4d00]: starting dnsmasq...
Aug  7 06:04:20 ins NetworkManager[885]: <info>  [1502100260.8944] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:04:21 ins dnsmasq[2291]: started, version 2.75 cache disabled
Aug  7 06:04:21 ins dnsmasq[2291]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Aug  7 06:04:21 ins dnsmasq[2291]: DBus support enabled: connected to system bus
Aug  7 06:04:21 ins dnsmasq[2291]: warning: no upstream servers configured
Aug  7 06:04:23 ins NetworkManager[885]: <info>  [1502100263.0281] dnsmasq[0x13d4d00]: dnsmasq appeared as :1.97
Aug  7 06:04:23 ins dnsmasq[2291]: setting upstream servers from DBus
Aug  7 06:04:23 ins dnsmasq[2291]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 06:04:23 ins dnsmasq[2291]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 06:06:40 ins avahi-daemon[816]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:06:40 ins avahi-daemon[816]: Interface wlp6s0.IPv6 no longer relevant for mDNS.
Aug  7 06:06:40 ins avahi-daemon[816]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.12.
Aug  7 06:06:40 ins avahi-daemon[816]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 06:06:40 ins NetworkManager[885]: <info>  [1502100400.7617] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:06:40 ins dnsmasq[2291]: setting upstream servers from DBus
Aug  7 06:06:43 ins avahi-daemon[816]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 06:06:43 ins avahi-daemon[816]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 06:06:43 ins NetworkManager[885]: <info>  [1502100403.9193] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 06:06:43 ins NetworkManager[885]: <info>  [1502100403.9195] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:06:43 ins dnsmasq[2291]: setting upstream servers from DBus
Aug  7 06:06:43 ins dnsmasq[2291]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 06:06:43 ins dnsmasq[2291]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 06:06:45 ins avahi-daemon[816]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:06:45 ins avahi-daemon[816]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 06:08:32 ins avahi-daemon[816]: Leaving mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:08:32 ins avahi-daemon[816]: Interface wlp6s0.IPv6 no longer relevant for mDNS.
Aug  7 06:08:32 ins avahi-daemon[816]: Leaving mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 06:08:32 ins avahi-daemon[816]: Interface wlp6s0.IPv4 no longer relevant for mDNS.
Aug  7 06:08:32 ins NetworkManager[885]: <info>  [1502100512.7843] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:08:32 ins dnsmasq[2291]: setting upstream servers from DBus
Aug  7 06:08:37 ins avahi-daemon[816]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 06:08:37 ins avahi-daemon[816]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 06:08:37 ins NetworkManager[885]: <info>  [1502100517.1785] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 06:08:37 ins NetworkManager[885]: <info>  [1502100517.1788] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 06:08:37 ins dnsmasq[2291]: setting upstream servers from DBus
Aug  7 06:08:37 ins dnsmasq[2291]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 06:08:37 ins dnsmasq[2291]: using nameserver 151.197.0.39#53(via wlp6s0)
Aug  7 06:08:38 ins avahi-daemon[816]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 06:08:38 ins avahi-daemon[816]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 10:18:55 ins kernel: [    0.956502] Key type dns_resolver registered
Aug  7 10:18:55 ins systemd[1]: Starting Clean up any mess left by 0dns-up...
Aug  7 10:18:55 ins systemd[1]: Started Clean up any mess left by 0dns-up.
Aug  7 10:18:55 ins systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Aug  7 10:18:55 ins systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Aug  7 10:18:55 ins systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Aug  7 10:18:59 ins NetworkManager[846]: <info>  [1502115539.6454] dns-mgr[0x2574960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Aug  7 10:19:27 ins avahi-daemon[864]: Joining mDNS multicast group on interface wlp6s0.IPv4 with address 192.168.1.3.
Aug  7 10:19:27 ins avahi-daemon[864]: New relevant interface wlp6s0.IPv4 for mDNS.
Aug  7 10:19:28 ins NetworkManager[846]: <info>  [1502115568.0540] policy: set '_white' (wlp6s0) as default for IPv4 routing and DNS
Aug  7 10:19:28 ins NetworkManager[846]: <info>  [1502115568.0542] dns-plugin[0x25a3900]: starting dnsmasq...
Aug  7 10:19:28 ins NetworkManager[846]: <info>  [1502115568.1808] dns-mgr: Writing DNS information to /sbin/resolvconf
Aug  7 10:19:28 ins dnsmasq[1953]: started, version 2.75 cache disabled
Aug  7 10:19:28 ins dnsmasq[1953]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Aug  7 10:19:28 ins dnsmasq[1953]: DBus support enabled: connected to system bus
Aug  7 10:19:28 ins dnsmasq[1953]: warning: no upstream servers configured
Aug  7 10:19:29 ins avahi-daemon[864]: Joining mDNS multicast group on interface wlp6s0.IPv6 with address fe80::78d4:e73d:6f1b:59f8.
Aug  7 10:19:29 ins avahi-daemon[864]: New relevant interface wlp6s0.IPv6 for mDNS.
Aug  7 10:19:32 ins NetworkManager[846]: <info>  [1502115572.3377] dnsmasq[0x25a3900]: dnsmasq appeared as :1.72
Aug  7 10:19:32 ins dnsmasq[1953]: setting upstream servers from DBus
Aug  7 10:19:32 ins dnsmasq[1953]: using nameserver 8.8.8.8#53(via wlp6s0)
Aug  7 10:19:32 ins dnsmasq[1953]: using nameserver 151.197.0.39#53(via wlp6s0)

```

```

:~$ ifconfig wlp6s0
wlp6s0    Link encap:Ethernet  HWaddr e4:02:9b:2f:10:61  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::78d4:e73d:6f1b:59f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192729 (192.7 KB)  TX bytes:65292 (65.2 KB)

:~$ ping -c2 localhost | awk '/ping/,/2/'
--- localhost ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms

:~$ ping -c2 192.168.1.12
--- 192.168.1.12 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms

:~$ ping -c2 $(route -n |awk 'FNR==3{print$2}')|awk '/ping|loss/'
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms

:~$ ping -c2 192.168.1.1
--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms

:~$ ping -c2 8.8.8.8
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms

```

---

### Post by Hadaka on 2017-08-08
Hi, your last post ..
```
--- **[COLOR=#ff0000]localhost[/COLOR]** ping statistics ---
2 packets transmitted, 0 received, **[COLOR=#ff0000]100%[/COLOR]** packet loss, time 1008ms
```
and another post with 192.168.1.1 with 100% loss is unsual.
Nothing in the wireless-info report or anything we have done is indicating the cause
of the problem. We suggest you try booting to a live 16.04 session, and see if you are able to
access the internet. If that is successful, then reloading Ubuntu would be the next step.
Please try the live session and report back your findings.
Thanks.

---

### Post by bvargo on 2017-08-12
So I booted from a live USB and here are the results:

```

ubuntu@ubuntu:~$ uname -r
4.4.0-31-generic

ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

ubuntu@ubuntu:~$ ping -c2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=47 time=23.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=47 time=24.8 ms

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 23.618/24.212/24.806/0.594 ms

ubuntu@ubuntu:~$ ping -c2 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.055 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.079 ms

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.055/0.067/0.079/0.012 ms

ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp6s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp6s0

ubuntu@ubuntu:~$ ifconfig
enp7s0    Link encap:Ethernet  HWaddr 14:18:77:c7:bb:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:69253 (69.2 KB)  TX bytes:69253 (69.2 KB)

wlp6s0    Link encap:Ethernet  HWaddr e4:02:9b:2f:10:61  
          inet addr:192.168.0.22  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4b74:86ba:9973:5f7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6882 (6.8 KB)  TX bytes:12498 (12.4 KB)

```

Is there a way to reinstall just the network portion of Ubuntu?  I don't want to loose all of my settings, etc.

Thanks

---

### Post by bvargo on 2017-08-12
Will this still work in 16.04?  [https://ubuntuforums.org/showthread.php?t=2057342](https://ubuntuforums.org/showthread.php?t=2057342)  I do not want to have to reconfigure all of my system services, e.g. minidlna, deluge, ssh, etc.

---

### Post by Hadaka on 2017-08-12
Hi, to answer your question yes that link should still work.
I would recommend using * rsync instead to get a clean backup.
Here is an older link, but still valid information for backing up hidden files.
 [http://www.linuxquestions.org/questions/linux-newbie-8/recursively-cp-all-directories-files-and-hidden-files-808403/](http://www.linuxquestions.org/questions/linux-newbie-8/recursively-cp-all-directories-files-and-hidden-files-808403/)
" I do not want to have to reconfigure all of my system services, e.g. minidlna, deluge, ssh, etc."
be sure to back up the hidden files.. /.ssh and other possible hidden files you created..not the system.
also files in /etc as in /etc/ssh
please keep us updated.
Thanks.

---

### Post by bvargo on 2017-09-13
So I'm just wondering if there are any other ideas about how to restore the networking portion of my current Ubuntu installation without wiping out everything I have set up in terms of programs like minidlna, ssh, etc.  I have not done anything with this since August and am really getting tired of using Windows.

Thanks

---

