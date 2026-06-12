---
title: "QCA6164 in Ubuntu 16.04"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by Arnaud22 on 2016-04-28
i think the new kernel (Linux nonald-Lenovo-Yoga-3-14 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux) creates new problems with this wireless firmware solution for the yoga 3 14... :-( 
I actually don't know myself how to troubleshoot these issues. If anyone manage to find anything on that, it'd help me too.

---

### Post by jeremy31 on 2016-04-28
In 16.04 you likely just need the firmware
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
sudo rm -r/lib/firmware/ath10k/QCA6174/
git clone https://github.com/atondwal/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/
```
You will not need backports with the 4.4 kernel

---

### Post by Arnaud22 on 2016-04-28
didnt work apparently. (is it the binary files from QCA6174 that we're supposed to now use  yeah?)


dmesg | grep ath10k ==>
[    2.304970] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.543921] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    2.544806] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    2.544822] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[    3.840847] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[    3.840851] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    3.923073] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0

---

### Post by jeremy31 on 2016-04-28
Setting the skip otp parameter may fix it
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```
Reboot

---

### Post by Arnaud22 on 2016-04-28
nothing.

same message from    dmesg | grep ath10k

and probably same error here:
 dmesg | grep -i qca6174 ==>
[    2.583919] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    3.878135] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features

---

### Post by jeremy31 on 2016-04-28
I would like you to run the wireless script ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

And post the contents of the wireless-info.**txt** file, please use code tags [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by Arnaud22 on 2016-04-28
here it is.

(For info, on the top panel next to the bluetooth logo, i can see "Ethernet Network (Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter) disconnected" greyed out)


```

########## wireless info START ##########

Report from: 29 Apr 2016 01:24 CEST +0200

Booted last: 29 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 006: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 011: ID 2717:ff88  
Bus 001 Device 002: ID 5986:0535 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci1: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           286720  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
cfg80211              552960  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enxb22af52834e9 Link encap:Ethernet  HWaddr <MAC 'enxb22af52834e9' [IF]>  
          inet addr:192.168.42.152  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::68cc:1d75:fc45:561a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1657 errors:1 dropped:0 overruns:0 frame:1
          TX packets:1657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:781349 (781.3 KB)  TX bytes:297346 (297.3 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enxb22af52834e9  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enxb22af52834e9
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enxb22af52834e9
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enxb22af52834e9

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       812     1  0 Apr28 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enxb22af52834e9
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Xiaomi
GENERAL.PRODUCT:                        Redmi
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enxb22af52834e9' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enxb22af52834e9
GENERAL.IP-IFACE:                       enxb22af52834e9
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       53fbabb9-77ee-4405-92fc-df2e4fcf5880
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{48}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   53fbabb9-77ee-4405-92fc-df2e4fcf5880 | Wired connection 2
IP4.ADDRESS[1]:                         192.168.42.152/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.152
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1461889252
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = nonald-Lenovo-Yoga-3-14
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::68cc:1d75:fc45:561a/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
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

[[/etc/NetworkManager/system-connections/HeureuxRequin-visiteur]] (600 root)
[connection] id=HeureuxRequin-visiteur | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HeureuxRequin-visiteur
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone de Nathalie]] (600 root)
[connection] id=iPhone de Nathalie | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iPhone de Nathalie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/magic335]] (600 root)
[connection] id=magic335 | type=wifi
[wifi] ssid=magic335 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vaio]] (600 root)
[connection] id=vaio | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=vaio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/monwifi]] (600 root)
[connection] id=monwifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=monwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-F550]] (600 root)
[connection] id=Livebox-F550 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-F550
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifirst*B Afpa St-Brieuc]] (600 root)

[[/etc/NetworkManager/system-connections/Mac mini de Ludovic]] (600 root)
[connection] id=Mac mini de Ludovic | type=wifi
[wifi] ssid=Mac mini de Ludovic | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688 1]] (600 root)
[connection] id=Livebox-D688 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/&#32418;&#31859;&#25163;&#26426;]] (600 root)
[connection] id=&#32418;&#31859;&#25163;&#26426; | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=231;186;162;231;177;179;230;137;139;230;156;186;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488]] (600 root)
[connection] id=Livebox-3488 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-532A]] (600 root)
[connection] id=Livebox-532A | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-532A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Alto - GL]] (600 root)
[connection] id=Alto - GL | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Alto - GL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Freebox-A9AD0B]] (600 root)
[connection] id=Freebox-A9AD0B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Freebox-A9AD0B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTHOTSPOT-E0FB]] (600 root)
[connection] id=BTHOTSPOT-E0FB | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BTHOTSPOT-E0FB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hotel-paris-bruxelles]] (600 root)
[connection] id=hotel-paris-bruxelles | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=hotel-paris-bruxelles
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-a02a]] (600 root)
[connection] id=Livebox-a02a | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-a02a
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pharma]] (600 root)
[connection] id=Pharma | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Pharma
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-aFC460 Series]] (600 root)
[connection] id=DIRECT-aFC460 Series | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-aFC460 Series
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488 1]] (600 root)
[connection] id=Livebox-3488 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NEUF_15C0]] (600 root)
[connection] id=NEUF_15C0 | type=wifi
[wifi] ssid=NEUF_15C0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-EF06]] (600 root)
[connection] id=Livebox-EF06 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-EF06
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688]] (600 root)
[connection] id=Livebox-D688 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_SNCF gare-gratuit]] (600 root)
[connection] id=_SNCF gare-gratuit | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=_SNCF gare-gratuit
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bbox-4C589B]] (600 root)
[connection] id=Bbox-4C589B | type=wifi
[wifi] ssid=Bbox-4C589B | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

enxb22af52834e9  no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

enxb22af52834e9  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:5.22 GHz (Channel 44)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'orange' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000158acda6180
                    Extra: Last beacon: 4744ms ago
          Cell 02 - Address: <MAC 'Livebox-3488' [AC2]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Livebox-3488"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000108620c0114
                    Extra: Last beacon: 4444ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'INTRADOM-PDA' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"INTRADOM-PDA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000283045d0b80
                    Extra: Last beacon: 4416ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'INTRADOM-RADIUS' [AC4]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"INTRADOM-RADIUS"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002830455d03b
                    Extra: Last beacon: 3524ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'INTRADOM-PDA' [AC5]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"INTRADOM-PDA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002830456ca3b
                    Extra: Last beacon: 3472ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-21-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20151013-0-ge1ef378) using backports backports-20151013-0-g7d07501
srcversion:     E62AFCCBB7A8CF4754823F7
depends:        ath10k_core,compat
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-21-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     58E54EAFF85BC4029EF448D
depends:        mac80211,cfg80211,ath
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-21-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     38B85B218D8D1E53631A7C6
depends:        cfg80211
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20151013-0-ge1ef378) using backports backports-20151013-0-g7d07501
srcversion:     86578EDB2B18830CC74083C
depends:        cfg80211,compat
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20151013-0-ge1ef378) using backports backports-20151013-0-g7d07501
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     174C41315E50C94DA7D318D
depends:        compat
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N

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

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/ideapad.conf]
blacklist ideapad_laptop

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/myownblacklist.conf]
blacklist ideapad_laptop

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    3.878135] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[    3.878140] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    3.954760] ath: EEPROM regdomain: 0x6c
[    3.954763] ath: EEPROM indicates we should expect a direct regpair map
[    3.954765] ath: Country alpha2 being used: 00
[    3.954766] ath: Regpair used: 0x6c
[    3.967037] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.192159] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[ 9489.506989] rndis_host 1-2:1.0 enxb22af52834e9: renamed from usb0
[ 9489.529495] IPv6: ADDRCONF(NETDEV_UP): enxb22af52834e9: link is not ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-04-28
Your strongest wifi signal is coming from Livebox-3488 and it has TKIP encryption enabled, it may help to get into the router settings and disable TKIP

It may also help to set the country code with
```

sudo iw reg set FR
sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda

```

Thanks to a script from Hadaka

---

### Post by Arnaud22 on 2016-04-28
ok both done and switched to only wpa2-psk/aes on the router, restarted it and rebooted.
same situation.
(TKIP encryption can cause connection problems yeah?)

---

### Post by Hadaka on 2016-04-28
Hi, you may have a conflict with the usb wifi and the internal ath10k
from this enty.
```
[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (r8188eu) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0" 
```
Please remove the usb wifi unit then do...
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot and test wireless

*If you do not connect please post a fresh wireless diagnostic.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
Thanks.

---

### Post by Arnaud22 on 2016-04-29
hi, thanks for your help. no changes apparently.
here s the diagnostic

```

########## wireless info START ##########

Report from: 29 Apr 2016 15:18 CEST +0200

Booted last: 29 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 010: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 008: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 5986:0535 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           286720  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              638976  1 ath10k_core
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
cfg80211              552960  3 ath,mac80211,ath10k_core
compat                 16384  3 cfg80211,mac80211,ath10k_pci
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enxd8eb97bf1ed7 Link encap:Ethernet  HWaddr <MAC 'enxd8eb97bf1ed7' [IF]>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enxd8eb97bf1ed7' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80995 (80.9 KB)  TX bytes:21602 (21.6 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enxd8eb97bf1ed7  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enxd8eb97bf1ed7
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enxd8eb97bf1ed7
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enxd8eb97bf1ed7

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       921     1  2 15:17 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enxd8eb97bf1ed7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88x72A
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772 USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enxd8eb97bf1ed7' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/net/enxd8eb97bf1ed7
GENERAL.IP-IFACE:                       enxd8eb97bf1ed7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       5a154b3c-f566-455b-ba6f-058524869e48
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{42}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5a154b3c-f566-455b-ba6f-058524869e48 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.34/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.34
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1462022325
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:65:38:46:31:42:30:5:f:4c:4b:31:32:31:30:37:44:50:32:36:30:33:36:30:6:f:4c:69:76:65:62:6f:78:20:46:54:54:48:20:76:32
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'enxd8eb97bf1ed7' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
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

[[/etc/NetworkManager/system-connections/HeureuxRequin-visiteur]] (600 root)
[connection] id=HeureuxRequin-visiteur | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HeureuxRequin-visiteur
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone de Nathalie]] (600 root)
[connection] id=iPhone de Nathalie | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iPhone de Nathalie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/magic335]] (600 root)
[connection] id=magic335 | type=wifi
[wifi] ssid=magic335 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vaio]] (600 root)
[connection] id=vaio | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=vaio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/monwifi]] (600 root)
[connection] id=monwifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=monwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-F550]] (600 root)
[connection] id=Livebox-F550 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-F550
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifirst*B Afpa St-Brieuc]] (600 root)

[[/etc/NetworkManager/system-connections/Mac mini de Ludovic]] (600 root)
[connection] id=Mac mini de Ludovic | type=wifi
[wifi] ssid=Mac mini de Ludovic | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688 1]] (600 root)
[connection] id=Livebox-D688 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/&#32418;&#31859;&#25163;&#26426;]] (600 root)
[connection] id=&#32418;&#31859;&#25163;&#26426; | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=231;186;162;231;177;179;230;137;139;230;156;186;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488]] (600 root)
[connection] id=Livebox-3488 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-532A]] (600 root)
[connection] id=Livebox-532A | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-532A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Alto - GL]] (600 root)
[connection] id=Alto - GL | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Alto - GL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Freebox-A9AD0B]] (600 root)
[connection] id=Freebox-A9AD0B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Freebox-A9AD0B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTHOTSPOT-E0FB]] (600 root)
[connection] id=BTHOTSPOT-E0FB | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BTHOTSPOT-E0FB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hotel-paris-bruxelles]] (600 root)
[connection] id=hotel-paris-bruxelles | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=hotel-paris-bruxelles
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-a02a]] (600 root)
[connection] id=Livebox-a02a | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-a02a
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pharma]] (600 root)
[connection] id=Pharma | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Pharma
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-aFC460 Series]] (600 root)
[connection] id=DIRECT-aFC460 Series | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-aFC460 Series
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488 1]] (600 root)
[connection] id=Livebox-3488 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NEUF_15C0]] (600 root)
[connection] id=NEUF_15C0 | type=wifi
[wifi] ssid=NEUF_15C0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-EF06]] (600 root)
[connection] id=Livebox-EF06 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-EF06
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688]] (600 root)
[connection] id=Livebox-D688 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_SNCF gare-gratuit]] (600 root)
[connection] id=_SNCF gare-gratuit | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=_SNCF gare-gratuit
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bbox-4C589B]] (600 root)
[connection] id=Bbox-4C589B | type=wifi
[wifi] ssid=Bbox-4C589B | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country FR: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enxd8eb97bf1ed7  no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

enxd8eb97bf1ed7  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Livebox-3488' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Livebox-3488"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a9d955d09
                    Extra: Last beacon: 3572ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-21-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20151013-0-ge1ef378) using backports backports-20151013-0-g7d07501
srcversion:     E62AFCCBB7A8CF4754823F7
depends:        ath10k_core,compat
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-21-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     58E54EAFF85BC4029EF448D
depends:        mac80211,cfg80211,ath
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-21-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     38B85B218D8D1E53631A7C6
depends:        cfg80211
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20151013-0-ge1ef378) using backports backports-20151013-0-g7d07501
srcversion:     86578EDB2B18830CC74083C
depends:        cfg80211,compat
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20151013-0-ge1ef378) using backports backports-20151013-0-g7d07501
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     174C41315E50C94DA7D318D
depends:        compat
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N

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

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/ideapad.conf]
blacklist ideapad_laptop

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/myownblacklist.conf]
blacklist ideapad_laptop

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    2.536119] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    2.536539] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:0041:17aa:3545.bin failed with error -2
[    2.536551] ath10k_pci 0000:02:00.0: failed to load spec board file, falling back to generic: -2
[    3.748292] ath10k_pci 0000:02:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:0041:17aa:3545 fallback) fw atheros-12.0.0.102-fw api 5 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[    3.748296] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    3.825191] ath: EEPROM regdomain: 0x6c
[    3.825195] ath: EEPROM indicates we should expect a direct regpair map
[    3.825197] ath: Country alpha2 being used: 00
[    3.825199] ath: Regpair used: 0x6c
[    3.846220] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.039316] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  104.630408] asix 1-2.1:1.0 eth0: register 'asix' at usb-0000:00:14.0-2.1, ASIX AX88772 USB 2.0 Ethernet, <MAC 'enxd8eb97bf1ed7' [IF]>
[  104.637542] asix 1-2.1:1.0 enxd8eb97bf1ed7: renamed from eth0
[  104.665966] IPv6: ADDRCONF(NETDEV_UP): enxd8eb97bf1ed7: link is not ready
[  104.667695] asix 1-2.1:1.0 enxd8eb97bf1ed7: link down
[  104.669132] IPv6: ADDRCONF(NETDEV_UP): enxd8eb97bf1ed7: link is not ready
[  106.360569] IPv6: ADDRCONF(NETDEV_CHANGE): enxd8eb97bf1ed7: link becomes ready
[  106.361074] asix 1-2.1:1.0 enxd8eb97bf1ed7: link up, 100Mbps, full-duplex, lpa 0x45E1

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-04-29
Uninstall the backports and see if things work again
```
cd backports-20151013
sudo make uninstall
```
Reboot

---

### Post by Arnaud22 on 2016-04-29
still not.

in case:
```


########## wireless info START ##########

Report from: 29 Apr 2016 16:31 CEST +0200

Booted last: 29 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 006: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 020: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 019: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 018: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 017: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 5986:0535 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci1: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8188eu               454656  0
wl                   6365184  0
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
cfg80211              565248  5 wl,ath,mac80211,r8188eu,ath10k_core
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enxd8eb97bf1ed7 Link encap:Ethernet  HWaddr d8:eb:97:bf:1e:d7  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::daeb:97ff:febf:1ed7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90553 (90.5 KB)  TX bytes:53848 (53.8 KB)

wlp2s0    Link encap:Ethernet  HWaddr d0:53:49:64:0d:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enxd8eb97bf1ed7  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enxd8eb97bf1ed7
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enxd8eb97bf1ed7
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enxd8eb97bf1ed7

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       753     1  1 16:28 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enxd8eb97bf1ed7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88x72A
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772 USB 2.0 Ethernet
GENERAL.HWADDR:                         D8:EB:97:BF:1E:D7
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/net/enxd8eb97bf1ed7
GENERAL.IP-IFACE:                       enxd8eb97bf1ed7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       5a154b3c-f566-455b-ba6f-058524869e48
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{42}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5a154b3c-f566-455b-ba6f-058524869e48 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.34/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.34
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1462026634
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:65:38:46:31:42:30:5:f:4c:4b:31:32:31:30:37:44:50:32:36:30:33:36:30:6:f:4c:69:76:65:62:6f:78:20:46:54:54:48:20:76:32
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::daeb:97ff:febf:1ed7/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         D0:53:49:64:0D:B1
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
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


```

---

### Post by Arnaud22 on 2016-04-29
(is it strange that in the top panel qualcomm atheros QCA6164 is greyed out as ethernet network instead of Wi-fi network?)

---

### Post by Hadaka on 2016-04-29
Hi, The wired connection should be removed when connecting
to wireless. You have a couple items that my be adding to the
the issue. Please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm -rf/etc/modprobe.d/ath9k.conf
sudo modprobe -rf r8188eu
```
remove wired connection,boot and test wireless
thanks.

---

### Post by Arnaud22 on 2016-04-29
thanks!
still not working

```



########## wireless info START ##########

Report from: 29 Apr 2016 19:30 CEST +0200

Booted last: 29 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 010: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 008: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 5986:0535 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
cfg80211              565248  3 ath,mac80211,ath10k_core
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enxd8eb97bf1ed7 Link encap:Ethernet  HWaddr <MAC 'enxd8eb97bf1ed7' [IF]>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enxd8eb97bf1ed7' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73002 (73.0 KB)  TX bytes:17113 (17.1 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enxd8eb97bf1ed7  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enxd8eb97bf1ed7
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enxd8eb97bf1ed7
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enxd8eb97bf1ed7

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       734     1  5 19:29 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enxd8eb97bf1ed7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88x72A
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772 USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enxd8eb97bf1ed7' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/net/enxd8eb97bf1ed7
GENERAL.IP-IFACE:                       enxd8eb97bf1ed7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       5a154b3c-f566-455b-ba6f-058524869e48
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{42}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5a154b3c-f566-455b-ba6f-058524869e48 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.34/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.34
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1462037414
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:65:38:46:31:42:30:5:f:4c:4b:31:32:31:30:37:44:50:32:36:30:33:36:30:6:f:4c:69:76:65:62:6f:78:20:46:54:54:48:20:76:32
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'enxd8eb97bf1ed7' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
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

[[/etc/NetworkManager/system-connections/HeureuxRequin-visiteur]] (600 root)
[connection] id=HeureuxRequin-visiteur | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HeureuxRequin-visiteur
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone de Nathalie]] (600 root)
[connection] id=iPhone de Nathalie | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iPhone de Nathalie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/magic335]] (600 root)
[connection] id=magic335 | type=wifi
[wifi] ssid=magic335 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vaio]] (600 root)
[connection] id=vaio | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=vaio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/monwifi]] (600 root)
[connection] id=monwifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=monwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-F550]] (600 root)
[connection] id=Livebox-F550 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-F550
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifirst*B Afpa St-Brieuc]] (600 root)

[[/etc/NetworkManager/system-connections/Mac mini de Ludovic]] (600 root)
[connection] id=Mac mini de Ludovic | type=wifi
[wifi] ssid=Mac mini de Ludovic | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688 1]] (600 root)
[connection] id=Livebox-D688 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/&#32418;&#31859;&#25163;&#26426;]] (600 root)
[connection] id=&#32418;&#31859;&#25163;&#26426; | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=231;186;162;231;177;179;230;137;139;230;156;186;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488]] (600 root)
[connection] id=Livebox-3488 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-532A]] (600 root)
[connection] id=Livebox-532A | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-532A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Alto - GL]] (600 root)
[connection] id=Alto - GL | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Alto - GL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Freebox-A9AD0B]] (600 root)
[connection] id=Freebox-A9AD0B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Freebox-A9AD0B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTHOTSPOT-E0FB]] (600 root)
[connection] id=BTHOTSPOT-E0FB | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BTHOTSPOT-E0FB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hotel-paris-bruxelles]] (600 root)
[connection] id=hotel-paris-bruxelles | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=hotel-paris-bruxelles
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-a02a]] (600 root)
[connection] id=Livebox-a02a | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-a02a
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pharma]] (600 root)
[connection] id=Pharma | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Pharma
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-aFC460 Series]] (600 root)
[connection] id=DIRECT-aFC460 Series | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-aFC460 Series
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488 1]] (600 root)
[connection] id=Livebox-3488 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NEUF_15C0]] (600 root)
[connection] id=NEUF_15C0 | type=wifi
[wifi] ssid=NEUF_15C0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-EF06]] (600 root)
[connection] id=Livebox-EF06 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-EF06
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688]] (600 root)
[connection] id=Livebox-D688 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_SNCF gare-gratuit]] (600 root)
[connection] id=_SNCF gare-gratuit | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=_SNCF gare-gratuit
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bbox-4C589B]] (600 root)
[connection] id=Bbox-4C589B | type=wifi
[wifi] ssid=Bbox-4C589B | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country FR: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enxd8eb97bf1ed7  no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

enxd8eb97bf1ed7  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Livebox-3488' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Livebox-3488"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e20ab6476
                    Extra: Last beacon: 3496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N

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

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

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

[/etc/modprobe.d/ideapad.conf]
blacklist ideapad_laptop

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/myownblacklist.conf]
blacklist ideapad_laptop

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    2.561597] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[    2.626042] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-2.bin failed with error -2
[    3.865675] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[    3.865679] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.940613] ath: EEPROM regdomain: 0x6c
[    3.940616] ath: EEPROM indicates we should expect a direct regpair map
[    3.940618] ath: Country alpha2 being used: 00
[    3.940619] ath: Regpair used: 0x6c
[    3.952890] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.008485] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   40.990216] asix 1-2.1:1.0 eth0: register 'asix' at usb-0000:00:14.0-2.1, ASIX AX88772 USB 2.0 Ethernet, <MAC 'enxd8eb97bf1ed7' [IF]>
[   40.994086] asix 1-2.1:1.0 enxd8eb97bf1ed7: renamed from eth0
[   41.017849] IPv6: ADDRCONF(NETDEV_UP): enxd8eb97bf1ed7: link is not ready
[   41.019190] asix 1-2.1:1.0 enxd8eb97bf1ed7: link down
[   41.021433] IPv6: ADDRCONF(NETDEV_UP): enxd8eb97bf1ed7: link is not ready
[   42.756235] IPv6: ADDRCONF(NETDEV_CHANGE): enxd8eb97bf1ed7: link becomes ready
[   42.757499] asix 1-2.1:1.0 enxd8eb97bf1ed7: link up, 100Mbps, full-duplex, lpa 0x45E1
[   50.181884] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 2 times)

########## wireless info END ############



```

---

### Post by jeremy31 on 2016-04-29
Strange, it appears to be working.  Try disabling power management with
```
sudo iwconfig wlp2s0 power off
```
Unplug the ethernet cable and see if it works

The wireless script shows that it can detect wireless networks

---

### Post by Arnaud22 on 2016-04-29
nothing either. ran laptop just on batteries and rebooted, but nothing...

---

### Post by jeremy31 on 2016-04-30
Please run the wireless script again

---

### Post by Arnaud22 on 2016-04-30
```


########## wireless info START ##########

Report from: 30 Apr 2016 14:26 CEST +0200

Booted last: 30 Apr 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04f3:206f Elan Microelectronics Corp. 
Bus 001 Device 006: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 011: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 010: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 009: ID 0b95:7720 ASIX Electronics Corp. AX88772
Bus 001 Device 008: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 002: ID 5986:0535 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8188eu               454656  0
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  4 ath,mac80211,r8188eu,ath10k_core
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enxd8eb97bf1ed7 Link encap:Ethernet  HWaddr <MAC 'enxd8eb97bf1ed7' [IF]>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enxd8eb97bf1ed7' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:625939 (625.9 KB)  TX bytes:172874 (172.8 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enxd8eb97bf1ed7  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enxd8eb97bf1ed7
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enxd8eb97bf1ed7
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enxd8eb97bf1ed7

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       727     1  1 14:23 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enxd8eb97bf1ed7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88x72A
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772 USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enxd8eb97bf1ed7' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/net/enxd8eb97bf1ed7
GENERAL.IP-IFACE:                       enxd8eb97bf1ed7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       5a154b3c-f566-455b-ba6f-058524869e48
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{42}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5a154b3c-f566-455b-ba6f-058524869e48 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.34/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.34
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = home
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1462105504
DHCP4.OPTION[21]:                       vendor_unknown_3561 = 4:6:65:38:46:31:42:30:5:f:4c:4b:31:32:31:30:37:44:50:32:36:30:33:36:30:6:f:4c:69:76:65:62:6f:78:20:46:54:54:48:20:76:32
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'enxd8eb97bf1ed7' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
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

[[/etc/NetworkManager/system-connections/HeureuxRequin-visiteur]] (600 root)
[connection] id=HeureuxRequin-visiteur | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HeureuxRequin-visiteur
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone de Nathalie]] (600 root)
[connection] id=iPhone de Nathalie | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iPhone de Nathalie
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/magic335]] (600 root)
[connection] id=magic335 | type=wifi
[wifi] ssid=magic335 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/vaio]] (600 root)
[connection] id=vaio | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=vaio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/monwifi]] (600 root)
[connection] id=monwifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=monwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-F550]] (600 root)
[connection] id=Livebox-F550 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-F550
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifirst*B Afpa St-Brieuc]] (600 root)

[[/etc/NetworkManager/system-connections/Mac mini de Ludovic]] (600 root)
[connection] id=Mac mini de Ludovic | type=wifi
[wifi] ssid=Mac mini de Ludovic | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688 1]] (600 root)
[connection] id=Livebox-D688 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/&#32418;&#31859;&#25163;&#26426;]] (600 root)
[connection] id=&#32418;&#31859;&#25163;&#26426; | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=231;186;162;231;177;179;230;137;139;230;156;186;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488]] (600 root)
[connection] id=Livebox-3488 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-532A]] (600 root)
[connection] id=Livebox-532A | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-532A
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Alto - GL]] (600 root)
[connection] id=Alto - GL | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Alto - GL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Freebox-A9AD0B]] (600 root)
[connection] id=Freebox-A9AD0B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Freebox-A9AD0B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTHOTSPOT-E0FB]] (600 root)
[connection] id=BTHOTSPOT-E0FB | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BTHOTSPOT-E0FB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hotel-paris-bruxelles]] (600 root)
[connection] id=hotel-paris-bruxelles | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=hotel-paris-bruxelles
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-a02a]] (600 root)
[connection] id=Livebox-a02a | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-a02a
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pharma]] (600 root)
[connection] id=Pharma | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Pharma
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-aFC460 Series]] (600 root)
[connection] id=DIRECT-aFC460 Series | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-aFC460 Series
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Redmi]] (600 root)
[connection] id=Redmi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Redmi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3488 1]] (600 root)
[connection] id=Livebox-3488 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Livebox-3488
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NEUF_15C0]] (600 root)
[connection] id=NEUF_15C0 | type=wifi
[wifi] ssid=NEUF_15C0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FreeWifi]] (600 root)
[connection] id=FreeWifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FreeWifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-EF06]] (600 root)
[connection] id=Livebox-EF06 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-EF06
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-D688]] (600 root)
[connection] id=Livebox-D688 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-D688
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_SNCF gare-gratuit]] (600 root)
[connection] id=_SNCF gare-gratuit | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=_SNCF gare-gratuit
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bbox-4C589B]] (600 root)
[connection] id=Bbox-4C589B | type=wifi
[wifi] ssid=Bbox-4C589B | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country FR: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enxd8eb97bf1ed7  no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

enxd8eb97bf1ed7  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:5.22 GHz (Channel 44)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Livebox-3488' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Livebox-3488"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001dff5a1f07
                    Extra: Last beacon: 3536ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'INTRADOM-RADIUS' [AC2]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"INTRADOM-RADIUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a20e305093
                    Extra: Last beacon: 3448ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC 'INTRADOM-PDA' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"INTRADOM-PDA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a20e304b80
                    Extra: Last beacon: 3500ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'INTRADOM-RADIUS' [AC4]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"INTRADOM-RADIUS"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a20e27803b
                    Extra: Last beacon: 2592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[r8188eu]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     367E7DBEF2838E97538C7AB
depends:        cfg80211
staging:        Y
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)
parm:           monitor_enable:Enable monitor inferface (default: false) (bool)

[ath10k_pci]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
monitor_enable: N
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N

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

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

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

[/etc/modprobe.d/ideapad.conf]
blacklist ideapad_laptop

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/myownblacklist.conf]
blacklist ideapad_laptop

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.808171] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[    3.808175] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.884587] ath: EEPROM regdomain: 0x6c
[    3.884590] ath: EEPROM indicates we should expect a direct regpair map
[    3.884593] ath: Country alpha2 being used: 00
[    3.884594] ath: Regpair used: 0x6c
[    3.892256] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.187569] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    4.213450] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[    5.828919] Bluetooth: hci0: QCA: patch rome 0x200 build 0x299, firmware rome 0x200 build 0x111
[    6.752769] r8188eu 1-2:1.0 wlx14cc20269b90: renamed from wlan0
[    6.781324] IPv6: ADDRCONF(NETDEV_UP): wlx14cc20269b90: link is not ready (repeated 4 times)
[    8.565879] IPv6: ADDRCONF(NETDEV_CHANGE): wlx14cc20269b90: link becomes ready
[   80.325955] asix 1-2.1:1.0 eth0: register 'asix' at usb-0000:00:14.0-2.1, ASIX AX88772 USB 2.0 Ethernet, <MAC 'enxd8eb97bf1ed7' [IF]>
[   80.328759] asix 1-2.1:1.0 enxd8eb97bf1ed7: renamed from eth0
[   80.351369] IPv6: ADDRCONF(NETDEV_UP): enxd8eb97bf1ed7: link is not ready
[   80.352465] asix 1-2.1:1.0 enxd8eb97bf1ed7: link down
[   80.354210] IPv6: ADDRCONF(NETDEV_UP): enxd8eb97bf1ed7: link is not ready
[   82.101815] IPv6: ADDRCONF(NETDEV_CHANGE): enxd8eb97bf1ed7: link becomes ready
[   82.102692] asix 1-2.1:1.0 enxd8eb97bf1ed7: link up, 100Mbps, full-duplex, lpa 0x45E1

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-04-30
Found some info involving Network Manager related to it identifying a Wlan device as wired, said stopping and starting network manager fixes the issue until the next restart
```
systemctl stop NetworkManager.service
```
```
systemctl enable NetworkManager.service
```


Edit: actually this was confirmed to work by another user
```
systemctl restart NetworkManager.service
```

---

### Post by Arnaud22 on 2016-05-03
yeeeh!!
thank you for your time jeremy31 and Hadaka! the restart command does the trick

-does it mean that the firmware is not taken into account when the network manager is started at boot up?
-simplest way: should i make an automatic command with this kind of script do you think? [http://askubuntu.com/questions/462143/where-are-the-startup-scripts-for-unity-desktop](http://askubuntu.com/questions/462143/where-are-the-startup-scripts-for-unity-desktop)
-and in next kernel update, will i simply just need to reinstall the firmware as mentioned previously in the thread?

thanks very much again for your help!!

---

### Post by jeremy31 on 2016-05-03
Your wireless was fine from the start.  The bug in network manager caused it to see seen as an ethernet device.  The bug has been fixed upstream, now we wait for a network manager update. You can mark as solved now or wait for the fixed network manager

---

### Post by Arnaud22 on 2016-05-03
ok thanks again!

---

### Post by hemulin2 on 2016-05-18
Hi guys,

I'm on a new laptop (Lenovo u31-70), running Lubuntu 16.04 and experiencing the same issues as described earlier in this thread with respect to the QCA6164 NIC.
Initially the card wasn't recognized at all. Then I updated the FW from the github page and everything worked perfectly. After 2 days, for some reason (maybe some periodic update to the basic components?) the wifi is shown as connected but I don't have any access outside. No ping is working (including to the router).

Then I tried
```
[COLOR=#000000][FONT=Ubuntu Mono]echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf[/FONT][/COLOR]
```
and rebooted.

It worked for some minutes (not sure if it was to options line or the reboot) and then again, no connectivity outside (again, system shows that I am connected).

Tried the networkManager service restart, also nothing.

Here are the results of my wireless diagnostic script:
```



########## wireless info START ##########


Report from: 18 May 2016 15:06 CEST +0200


Booted last: 18 May 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3828]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 004: ID 174f:14ee Syntek 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4fce:fa17:77f:6738/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93160673 (93.1 MB)  TX bytes:5959224 (5.9 MB)


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7a08:3dd:e328:25c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130607267 (130.6 MB)  TX bytes:8214559 (8.2 MB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:"Schumi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Schumi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search localdomain


##### network managers ##################


Installed:


	NetworkManager


Running:


root     10223     1  0 14:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168h-2_0.0.2 02/26/15
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       9c356d06-5f4b-45b2-a27c-573b71ee9483
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9c356d06-5f4b-45b2-a27c-573b71ee9483 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       expiry = 1464179138
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.6
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = localdomain
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 604800
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::4fce:fa17:77f:6738/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               SW_RM.1.1.1-00157-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Schumi
GENERAL.CON-UUID:                       9d88dffe-9e70-41f6-bb05-f574db284123
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9d88dffe-9e70-41f6-bb05-f574db284123 | Schumi
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       expiry = 1464178974
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = localdomain
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 604800
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::7a08:3dd:e328:25c6/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_0C_48_85_92_F4_46
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   13d580d7-dfc9-4ff1-beb9-4a444d98c6d1 | hemulin-mini Network


SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Schumi          <MAC 'Schumi' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 
ITPF            <MAC 'ITPF' [AC7]>  Infra  13    2472 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2      no        
FRITZ!Box 7490  <MAC 'FRITZ!Box 7490' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2      no        
--              <MAC '

```

Could you please suggest more possible solutions to this?

Cheers.

---

### Post by jeremy31 on 2016-05-18
It looks like your firmware is from Kvalo's github and it should work fine from what I see if the ethernet cable is disconnected

---

### Post by hemulin2 on 2016-05-18
Thanks for the quick reply.

Sadly the connection is not very stable. The funny thing is that once every ~2 hours during the whole day I'm disconnecting the LAN cable and nothing happens. After seeing your reply I tried again and viola, now I'm writing this over wifi.

(sigh) I hate inconsistent bugs, is there any log that I should diff against between unsuccessful wifi connections and successful ones like now?

In addition, while being on an "off" period I tried external usb wifi card and it didn't work either (ALFA AWUS...something using RT2870). And now ("on" period) it is working.
All leads to the conclusion that it is not in a specific HW control but in general in the wireless management.

---

### Post by hemulin2 on 2016-05-22
Hi,
So, here is a summary of my symptoms:
[FONT=arial]Lenovo u31-70, Lubuntu 16.04, QCA6164,[/FONT]
[FONT=arial]
[LIST]
[*]First OS installation. No wifi
[*]Installed FW from Kvalo's github, everything works perfectly.
[*]2 days after, wifi shows connected, but no access outside (can't even ping the router).

since then
[*]wifi connection comes and goes randomly, weak connection with many packet loss during ping checks.
[*]when trying to authenticate against a new AP (WPA2), authentication fails.
[*]while the wifi is not working, external wifi card isn't working either (ALFA, RT2870).
[*]airmon-ng and monitor mode are also experiencing problems (kind of oscillating activity, discovering APs around for about 10 seconds, and then losing them for 1 minute).
[*]Accessing open networks (public wifi in a bus) - kind of works, I can def. say that the connection is much more solid.
[*]Tethering over a usb from a smartphone, also very weak with an oscillating connection.
[/LIST]
I've read many posts around the web and tried many workarounds to tackle this issue, targeting different aspects in the pipeline. So far without success.


From my limited understanding, I suspect 

[LIST=1]
[*]FW
[*] NetworkManager or internal OSish manager of the HW
[*]wpa_supplicant because of the authentication problem and perhaps something with key renewal over handshakes because it is, well, "shaky".
[/LIST]

Can anyone confirm this on his machine and / or point towards a solution?
[/FONT]

Cheers.

---

### Post by jeremy31 on 2016-05-22
Run the wireless script again as the previous one was incomplete but it did show that power management was enabled on the wifi

---

### Post by hemulin2 on 2016-05-23
So, here are the results of running the scripts twice.
The **first**, while the connection is **solid and working well**.
The **second**, when there is **no connection and all the symptoms above are occurring**.

```



########## wireless info START ##########


Report from: 22 May 2016 16:35 CEST +0200


Booted last: 22 May 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3828]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 004: ID 174f:14ee Syntek 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 014: ID 1004:61f1 LG Electronics, Inc. Optimus Android Phone [LG Software mode]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
13: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:113553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109188313 (109.1 MB)  TX bytes:10371471 (10.3 MB)


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          inet addr:192.168.179.21  Bcast:192.168.179.255  Mask:255.255.255.0
          inet6 addr: fe80::c590:f994:281a:8836/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48954983 (48.9 MB)  TX bytes:7512887 (7.5 MB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:"Pele Mele Gastzugang"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Pele Mele Gastzugang' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.179.1   0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.179.0   0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fritz.box


##### network managers ##################


Installed:


	NetworkManager


Running:


root       945     1  0 May20 ?        00:00:30 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Pele Mele Gastzugang
GENERAL.CON-UUID:                       5e416ee0-c707-4855-9489-71b7ef716cb9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/11
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{16,15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5e416ee0-c707-4855-9489-71b7ef716cb9 | Pele Mele Gastzugang
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   c20f135f-d8ba-4579-aa46-31fc98f92c0e | Pele Mele
IP4.ADDRESS[1]:                         192.168.179.21/24
IP4.GATEWAY:                            192.168.179.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.179.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.179.1
DHCP4.OPTION[5]:                        ip_address = 192.168.179.21
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.179.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.179.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.179.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1464791651
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.179.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.179.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.179.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::c590:f994:281a:8836/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_0C_48_85_92_F4_46
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{14}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   48ecf48f-4598-4b29-b3db-73569fa7a9aa | hemulin-mini Network


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Pele Mele Gastzugang  <MAC 'Pele Mele Gastzugang' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
Pele Mele             <MAC 'Pele Mele' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
EpicWinning           <MAC 'EpicWinning' [AC5]>  Infra  13    2472 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Pele Mele             <MAC 'Pele Mele' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
ERCOM                 <MAC 'ERCOM' [AC4]>  Infra  9     2452 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        


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
managed=true


##### NetworkManager profiles ###########


Sorry, try again.
[[/etc/NetworkManager/system-connections/hemulinAP]] (600 root)
[connection] id=hemulinAP | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=hemulinAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Schumi]] (600 root)
[connection] id=Schumi | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Schumi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PianoNet]] (600 root)
[connection] id=PianoNet | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=PianoNet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Schumi 1]] (600 root)
[connection] id=Schumi 1 | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Schumi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FLIXmedia]] (600 root)
[connection] id=FLIXmedia | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=FLIXmedia
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Pele Mele]] (600 root)
[connection] id=Pele Mele | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Pele Mele
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WLAN-C69336]] (600 root)
[connection] id=WLAN-C69336 | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=WLAN-C69336
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Pele Mele Gastzugang]] (600 root)
[connection] id=Pele Mele Gastzugang | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Pele Mele Gastzugang
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


wlp3s0    32 channels in total; available frequencies :
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


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'Pele Mele Gastzugang' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Pele Mele Gastzugang"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006613cca19
                    Extra: Last beacon: 120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Pele Mele' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Pele Mele"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b52b155190
                    Extra: Last beacon: 15960ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Pele Mele' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Pele Mele"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006613d6180
                    Extra: Last beacon: 5704ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ERCOM' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ERCOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fd59ed34a
                    Extra: Last beacon: 4980ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'EpicWinning' [AC5]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"EpicWinning"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000053099cefd07
                    Extra: Last beacon: 4472ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N


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


##### modprobe options ##################


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


fstrim /
exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[91676.777487] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)! (repeated 17 times)
[94975.991083] wlp3s0: authenticate with <MAC 'Pele Mele Gastzugang' [AC1]>
[94976.026765] wlp3s0: send auth to <MAC 'Pele Mele Gastzugang' [AC1]> (try 1/3)
[94976.029309] wlp3s0: authenticated
[94976.031433] wlp3s0: associate with <MAC 'Pele Mele Gastzugang' [AC1]> (try 1/3)
[94976.039854] wlp3s0: RX AssocResp from <MAC 'Pele Mele Gastzugang' [AC1]> (capab=0x431 status=0 aid=1)
[94976.042624] wlp3s0: associated
[94976.073400] ath: EEPROM regdomain: 0x8114
[94976.073404] ath: EEPROM indicates we should expect a country code
[94976.073406] ath: doing EEPROM country->regdmn map search
[94976.073407] ath: country maps to regdmn code: 0x37
[94976.073409] ath: Country alpha2 being used: DE
[94976.073410] ath: Regpair used: 0x37
[94976.073415] ath: regdomain 0x8114 dynamically updated by country IE


########## wireless info END ############



```

```



########## wireless info START ##########


Report from: 23 May 2016 14:21 CEST +0200


Booted last: 23 May 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3828]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 004: ID 174f:14ee Syntek 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
14: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:113553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109188313 (109.1 MB)  TX bytes:10371471 (10.3 MB)


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7a08:3dd:e328:25c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:991351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:689985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1322055924 (1.3 GB)  TX bytes:111084349 (111.0 MB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:"Schumi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Schumi' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
46.19.137.115   192.168.1.1     255.255.255.255 UGH   0      0        0 wlp3s0
127.0.0.1       192.168.1.1     255.255.255.255 UGH   0      0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
nameserer 208.67.222.222
nameserver 208.67.220.220


##### network managers ##################


Installed:


	NetworkManager


Running:


root       945     1  0 May20 ?        00:00:46 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Schumi
GENERAL.CON-UUID:                       9d88dffe-9e70-41f6-bb05-f574db284123
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/12
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{8}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9d88dffe-9e70-41f6-bb05-f574db284123 | Schumi
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 46.19.137.115/32, nh = 192.168.1.1, mt = 0
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 127.0.0.1/32, nh = 192.168.1.1, mt = 0
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       expiry = 1464541025
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.2
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = localdomain
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 604800
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::7a08:3dd:e328:25c6/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_0C_48_85_92_F4_46
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{21}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9f1afb12-4249-45e0-8e74-d81c0ca30cd8 | hemulin-mini Network


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Schumi          <MAC 'Schumi' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
FRITZ!Box 7490  <MAC 'FRITZ!Box 7490' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no        
FRITZ!Box 7490  <MAC 'FRITZ!Box 7490' [AC10]>  Infra  36    5180 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no        
ITPF            <MAC 'ITPF' [AC9]>  Infra  13    2472 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no        
frittenbude     <MAC 'frittenbude' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
Apples Home     <MAC 'Apples Home' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
ALICE-WLAN03    <MAC 'ALICE-WLAN03' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
Apples Home     <MAC 'Apples Home' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
EasyBox-A1E950  <MAC 'EasyBox-A1E950' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
Speedlink-412   <MAC 'Speedlink-412' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
Netgear         <MAC 'Netgear' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
NETGEAR28       <MAC 'NETGEAR28' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
--              <MAC '

```


Any insights?

---

### Post by jeremy31 on 2016-05-23
You may have a card that needs different firmware
```
cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo rm *.bin
sudo wget https://github.com/atondwal/ath10k-firmware/blob/master/ath10k/QCA6164/hw2.1/board.bin
sudo wget https://github.com/atondwal/ath10k-firmware/blob/master/ath10k/QCA6164/hw2.1/firmware-5.bin
```

Reboot

---

### Post by hemulin2 on 2016-05-26
Hmm....

I tried with this fw and it kind of messed up the wifi and I can'r revert to the half working solution.

Here is the current state as shown shown in your script:

```



########## wireless info START ##########


Report from: 26 May 2016 08:51 CEST +0200


Booted last: 26 May 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3828]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
	Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
	Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 006: ID 174f:14ee Syntek 
Bus 002 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 004: ID 1004:61f1 LG Electronics, Inc. Optimus Android Phone [LG Software mode]
Bus 002 Device 003: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 002: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
snd_soc_rt286          36864  0
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          inet addr:192.168.0.21  Bcast:192.168.7.255  Mask:255.255.248.0
          inet6 addr: fe80::<IP6 'enp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44230 (44.2 KB)  TX bytes:29561 (29.5 KB)


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.248.0   U     100    0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
nameserer 208.67.222.222
nameserver 208.67.220.220


##### network managers ##################


Installed:


	NetworkManager


Running:


root       918     1  0 08:50 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       5b92171a-4045-46bf-bcfb-4c399f1294b0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5b92171a-4045-46bf-bcfb-4c399f1294b0 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.21/21
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.4.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1464252605
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.21
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = mapegy.local
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.7.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 7200
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.248.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp2s0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_0C_48_85_92_F4_46
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{13}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3891a556-0b55-45c7-83ac-7ccbda8b896d | hemulin-mini Network


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
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/mapegy]] (600 root)
[connection] id=mapegy | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=mapegy
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hemulinAP]] (600 root)
[connection] id=hemulinAP | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=hemulinAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Schumi]] (600 root)
[connection] id=Schumi | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Schumi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PianoNet]] (600 root)
[connection] id=PianoNet | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PianoNet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Schumi 1]] (600 root)
[connection] id=Schumi 1 | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Schumi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FLIXmedia]] (600 root)
[connection] id=FLIXmedia | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FLIXmedia
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Pele Mele]] (600 root)
[connection] id=Pele Mele | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Pele Mele
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WLAN-C69336]] (600 root)
[connection] id=WLAN-C69336 | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WLAN-C69336
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Pele Mele Gastzugang]] (600 root)
[connection] id=Pele Mele Gastzugang | type=wifi | permissions=user:hemulin:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Pele Mele Gastzugang
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


[ath10k_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: Y
uart_print: N


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


##### modprobe options ##################


[/etc/modprobe.d/ath10k.conf]
options ath10k_core skip_otp=y


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


fstrim /
exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    8.401548] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    8.402038] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-5.bin failed with error -2
[    8.402042] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-5.bin': -2
[    8.402053] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-4.bin failed with error -2
[    8.402055] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -2
[    8.402068] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-3.bin failed with error -2
[    8.402070] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -2
[    8.402078] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-2.bin failed with error -2
[    8.402080] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-2.bin': -2
[    8.402088] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware.bin failed with error -2
[    8.402090] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[    8.402093] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    8.402095] ath10k_pci 0000:03:00.0: could not probe fw (-2)
[    8.834751] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    8.850087] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[    8.850166] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   12.768226] r8169 0000:02:00.0 enp2s0: link up
[   12.768237] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


########## wireless info END ############



```

and the result of dmseg:

```

&#9492;&#9472;[~/Documents]&#9472;> dmesg | grep ath10k
[    8.163636] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    8.401548] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    8.402038] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-5.bin failed with error -2
[    8.402042] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-5.bin': -2
[    8.402053] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-4.bin failed with error -2
[    8.402055] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -2
[    8.402068] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-3.bin failed with error -2
[    8.402070] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -2
[    8.402078] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-2.bin failed with error -2
[    8.402080] ath10k_pci 0000:03:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-2.bin': -2
[    8.402088] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware.bin failed with error -2
[    8.402090] ath10k_pci 0000:03:00.0: could not fetch firmware (-2)
[    8.402093] ath10k_pci 0000:03:00.0: could not fetch firmware files (-2)
[    8.402095] ath10k_pci 0000:03:00.0: could not probe fw (-2)

```

Any ideas?

Thank you for all your help. It is much appreciated

---

### Post by jeremy31 on 2016-05-26
Try loading the firmware-5.bin from antondwal again
```
cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo wget https://github.com/atondwal/ath10k-firmware/blob/master/ath10k/QCA6164/hw2.1/firmware-5.bin
```

The dmesg result shows a -2 error which means not found

---

### Post by hemulin2 on 2016-05-26
After messing around with different fw versions, the only solutions that works immediately is the first one you gave on this thread
i.e 
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
sudo rm -r/lib/firmware/ath10k/QCA6174/
git clone [https://github.com/atondwal/ath10k-firmware.git](https://github.com/atondwal/ath10k-firmware.git)
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
cd /lib/firmware/ath10k/QCA6164
sudo cp -r hw2.1/ /lib/firmware/ath10k/QCA6174/
I will keep monitoring both the performance of the fw and connectivity and updates and releases to the repository.
Hopefully this somewhat bugy behavior would decrease with time and with more people having this hw.

Dear Jeremy, thank you for the kind assistance you are offering, me and many others owe our connection to the world to you :)

Cheers

---

### Post by jeremy31 on 2016-05-26
No problem, I have seen the firmware from kvalo's github work with the QCA6164 cards but I am fairly sure it was before the board-2.bin was added.  Before 16.04, the only firmware that worked was from antondwal

---

