---
title: "Ubuntu 16.04 LTS - Wifi connected but not working"
date: 2016-05-08
forum: Networking &amp; Wireless
---

### Post by guillermo20 on 2016-05-08
[COLOR=#000000]I'm running ubuntu 16.04 lts[/COLOR]

[COLOR=#000000]I've got a [/COLOR]acer aspire 5735Z

[COLOR=#000000]Wired connections work fine, but the wifi doesn't.[/COLOR]

[COLOR=#000000]However, I can view the dhcp table on the router and see that it has a connection for the laptop and has an IP addressed assigned to it, and I can also view the IP address on ubuntu under the network connection.[/COLOR]

[COLOR=#000000]Any ideas?[/COLOR]

---

### Post by guillermo20 on 2016-05-15
Ple[COLOR=#000000]ase, see the results of use the comm[/COLOR][SIZE=3][COLOR=#000000][FONT=Ubuntu Mono]and[/FONT][/COLOR][/SIZE][COLOR=#000000]:[/COLOR]
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
```

guillermo@guillermo-Aspire-5735:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
Linux guillermo-Aspire-5735 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:52:40 UTC 2016 i686 i686 i686 GNU/Linux
guillermo@guillermo-Aspire-5735:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
    Subsystem: Acer Incorporated [ALI] 88E8071 PCI-E Gigabit Ethernet Controller [1025:013f]
    Kernel driver in use: sky2
    Kernel modules: sky2
03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k
guillermo@guillermo-Aspire-5735:~$ iwconfig
lo        no wireless extensions.


enp2s0    no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"INFINITUMx2re"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D4:40:F0:91:1D:50   
          Bit Rate=11 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


guillermo@guillermo-Aspire-5735:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
guillermo@guillermo-Aspire-5735:~$ lsmod
Module                  Size  Used by
drbg                   28672  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    73728  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
arc4                   16384  2
snd_hda_intel          36864  3
snd_hda_codec         118784  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           61440  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
uvcvideo               77824  0
snd_hwdep              16384  1 snd_hda_codec
videobuf2_vmalloc      16384  1 uvcvideo
snd_pcm                94208  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
ath9k                 135168  0
videobuf2_memops       16384  1 videobuf2_vmalloc
ath9k_common           36864  1 ath9k
videobuf2_v4l2         28672  1 uvcvideo
ath9k_hw              458752  2 ath9k_common,ath9k
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              155648  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_seq_midi           16384  0
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi_event     16384  1 snd_seq_midi
mac80211              659456  1 ath9k
media                  24576  2 uvcvideo,videodev
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
coretemp               16384  0
snd                    69632  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
input_leds             16384  0
soundcore              16384  1 snd
joydev                 20480  0
serio_raw              16384  0
lpc_ich                20480  0
shpchp                 32768  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2
ums_realtek            20480  0
uas                    20480  0
usb_storage            57344  2 uas,ums_realtek
i915                 1130496  5
mxm_wmi                16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        131072  1 i915
syscopyarea            16384  1 drm_kms_helper
psmouse               118784  0
ahci                   36864  1
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
libahci                32768  1 ahci
fb_sys_fops            16384  1 drm_kms_helper
drm                   311296  7 i915,drm_kms_helper
sky2                   53248  0
wmi                    20480  1 mxm_wmi
video                  36864  1 i915
fjes                   28672  0

```

---

### Post by cyrano_de_bergerac on 2016-05-27
> **cyrano_de_bergerac said:**
> Hi,

i have the sam issues, after upgrade to 16.04 LTS, the wired connections works fine but wireless doesn't work.
The same controler chip as guillermo 
Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

i get the ip from router and the route was set , but no entry in the resolv.conf.
i cannot ping [www.google.com]("http://www.google.com"),  8.8.8.8 or my own dhcp-router

```

cat wireless-info.txt 

########## wireless info START ##########

Report from: 27 May 2016 15:59 CEST +0200

Booted last: 27 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
    Subsystem: ASUSTeK Computer Inc. 191 Gigabit Ethernet Adapter [1043:1815]
    Kernel driver in use: sis190

02:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: AzureWave AW-NE771 802.11bgn Wireless Mini PCIe Card [AR9281] [1a3b:1067]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. RTS5116 Card Reader Controller
Bus 001 Device 002: ID 064e:a111 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s4    Link encap:Ethernet  HWaddr <MAC 'enp0s4' [IF]>  
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::335c:a165:700b:c2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3515241 (3.5 MB)  TX bytes:270376 (270.3 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39893 (39.8 KB)  TX bytes:10286 (10.2 KB)

##### iwconfig ##########################

enp0s4    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"poolix"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'poolix' [AC1]>   
          Bit Rate=11 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp0s4
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s4
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       649     1  0 15:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s4
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Silicon Integrated Systems [SiS]
GENERAL.PRODUCT:                        191 Gigabit Ethernet Adapter
GENERAL.DRIVER:                         sis190
GENERAL.DRIVER-VERSION:                 1.4
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s4' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/net/enp0s4
GENERAL.IP-IFACE:                       enp0s4
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kabelnetzwerkverbindung 1
GENERAL.CON-UUID:                       56e75ca1-bae1-4bb8-85cb-0bd8c8e93ed9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   56e75ca1-bae1-4bb8-85cb-0bd8c8e93ed9 | Kabelnetzwerkverbindung 1
IP4.ADDRESS[1]:                         192.168.0.119/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1464962115
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 604800
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.119
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::335c:a165:700b:c2e/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR928X Wireless Network Adapter (PCI-Express) (AW-NE771 802.11bgn Wireless Mini PCIe Card [AR9281])
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     poolix
GENERAL.CON-UUID:                       2e018e13-ec8b-4394-8c49-186d47b8212a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     11 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2e018e13-ec8b-4394-8c49-186d47b8212a | poolix
IP4.ADDRESS[1]:                         192.168.0.110/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1464962111
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 604800
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.110
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                    <MAC '' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
poolix                <MAC 'poolix' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
dlink                 <MAC 'dlink' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WEP        no        
UPC2388170            <MAC 'UPC2388170' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Moepper               <MAC 'Moepper' [AC7]>  Infra  9     2452 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
FRITZ!Box 6490 Cable  <MAC 'FRITZ!Box 6490 Cable' [AC4]>  Infra  4     2427 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
WLAN-717E67           <MAC 'WLAN-717E67' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
WLAN-510708           <MAC 'WLAN-510708' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
SME_Gast              <MAC 'SME_Gast' [AN9]>  Infra  2     2417 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/poolix-2e018e13-ec8b-4394-8c49-186d47b8212a]] (600 root)
[connection] id=poolix | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=poolix
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/poolix]] (600 root)
[connection] id=poolix | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=poolix
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp0s4    no frequency information.

lo        no frequency information.

wlp2s0    13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

enp0s4    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'poolix' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"poolix"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c4414e0d66
                    Extra: Last beacon: 16ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC2388170' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"UPC2388170"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015538791a4c
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003c4415743ca
                    Extra: Last beacon: 168ms ago
          Cell 04 - Address: <MAC 'FRITZ!Box 6490 Cable' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 6490 Cable"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000049bc93db4c3
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'dlink' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000281dd033505
                    Extra: Last beacon: 16ms ago
          Cell 06 - Address: <MAC 'WLAN-717E67' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"WLAN-717E67"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001176c2d8004
                    Extra: Last beacon: 1184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Moepper' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Moepper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001553874240c
                    Extra: Last beacon: 1024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7E3AF932B15681132EA595
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0151AF8061D8EE7CE15E1A9
depends:        ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

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

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   16.973938] ath: EEPROM regdomain: 0x60
[   16.973944] ath: EEPROM indicates we should expect a direct regpair map
[   16.973948] ath: Country alpha2 being used: 00
[   16.973949] ath: Regpair used: 0x60
[   17.302093] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   32.245191] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   32.270290] IPv6: ADDRCONF(NETDEV_UP): enp0s4: link is not ready (repeated 2 times)
[   32.793058] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   33.894252] wlp2s0: authenticate with <MAC 'poolix' [AC1]>
[   33.908874] wlp2s0: send auth to <MAC 'poolix' [AC1]> (try 1/3)
[   33.978952] wlp2s0: authenticated
[   33.980136] wlp2s0: associate with <MAC 'poolix' [AC1]> (try 1/3)
[   34.019494] wlp2s0: RX AssocResp from <MAC 'poolix' [AC1]> (capab=0xc11 status=0 aid=4)
[   34.019613] wlp2s0: associated
[   34.019696] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   34.068862] ath: EEPROM regdomain: 0x833a
[   34.068867] ath: EEPROM indicates we should expect a country code
[   34.068869] ath: doing EEPROM country->regdmn map search
[   34.068871] ath: country maps to regdmn code: 0x37
[   34.068873] ath: Country alpha2 being used: GB
[   34.068874] ath: Regpair used: 0x37
[   34.068877] ath: regdomain 0x833a dynamically updated by country IE
[   42.332027] sis190 0000:00:04.0 enp0s4: mii ext = 0000
[   42.360026] sis190 0000:00:04.0 enp0s4: mii lpa=45e1 adv=01e1 exp=0007
[   42.360032] sis190 0000:00:04.0 enp0s4: link on 100 Mbps Full Duplex mode
[   42.360055] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s4: link becomes ready

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-05-27
Does it work correctly is you change the router's encryption settings to WPA2-PSK or WPA2 only?  The access point "poolix" currently has TKIP enabled and linux in general doesn't work well with it enabled and TKIP is less secure

---

### Post by cyrano_de_bergerac on 2016-05-28
I have change the settings on the Router to only aes , but i have the same issue.
With the old 14.04 live image, wireless connections runs

---

### Post by jeremy31 on 2016-05-28
I wonder if it is caused by the bug in gnome network manager, see if ```
systemctl restart NetworkManager.service
``` Makes it work

---

### Post by cyrano_de_bergerac on 2016-05-29
No change. No connect.
How to lift the logs in the debug level or which logs can still be looked at ? A little bit crazy. Thx

---

### Post by jeremy31 on 2016-05-29
There are a couple logs that may be useful /var/log/syslog and /var/log/kern.log
I would also look at the router log, if it has one

---

### Post by cyrano_de_bergerac on 2016-05-29
The problem occurs since version 15.04 , I have tested all live-images since 14.04. 14.04 works fine the others not. the actually suse image works fine, too

---

### Post by jeremy31 on 2016-05-29
You should file a bug report if that is the case, a [guide to bug reports](http://ubuntuforums.org/showthread.php?t=1011078)
Was the 14.04 actually 14.04 or 14.04.3 or 14.04.4 as that would eliminate it being a kernel issue.  You may want to try WICD as a network manager and see if that works for you

---

### Post by cyrano_de_bergerac on 2016-05-29
RP requests works fine, tcp requests faileds. I will test with WICD

---

### Post by cyrano_de_bergerac on 2016-05-29
With wicd the same issue. Your hint with 14.04 is correct. 14.04.4 do not work but 14.04.3 works fine

---

