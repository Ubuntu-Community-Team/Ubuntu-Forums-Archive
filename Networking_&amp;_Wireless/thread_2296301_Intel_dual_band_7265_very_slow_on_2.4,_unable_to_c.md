---
title: "Intel dual band 7265 very slow on 2.4, unable to connect on 5g"
date: 2015-09-24
forum: Networking &amp; Wireless
---

### Post by jwhitene on 2015-09-24
I just got a system76 meerkat running ubuntu 15.04.

It came with Intel® Wireless-AC dual band.  The 5G won't connect at all.  The 2.4 connects, but the speed is very slow, like under 1Mb/s when I do internet speed tests.  A phone and a laptop in the same room connect to either and are very fast.  The router is a new AC1750 Wireless Dual Band Gigabit Router Archer C7.  

After googling a bit, I found the chipset is a [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi) - Intel® Wireless 7265.  In my /lib/firmware directory I see all the ucode files that are provided in this driver iwlwifi-7265-ucode-25.17.12.0.tgz.  So it seems like system76 did install the latest drivers.  I'm not exactly sure if they are active.  I work on linux servers mostly and do not deal with wifi.  Desktop linux / wifi debugging isn't my skillset:)

How do I know which driver it is using?  Does it just use the latest ucode file in the /lib/firmware directory?

Also, after tinkering a bit with the wifi and running some modprobe commands, the bluetooth also stopped working after a restart.  It is toggled off, and the icon in the upper right is gone.  If I go into settings and turn it on, it promptly turns itself off again.

I see lots of issues with 7265 - [https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=intel%207265%20wifi%20ubuntu%20slow](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=intel%207265%20wifi%20ubuntu%20slow)

Should ubuntu 15.04 and intel 7265 work nicely together?  I assume system76 installed everything needed to make all the hardware work well, but I guess not.  

I'll bring the unit into work next week and see how it performs against an enterprise wifi, but given my phone and laptop work perfectly fine, I'm guessing it isn't an issue with my home wifi.

I see this thread on the forums, but it is about the wifi not working at all:  [http://ubuntuforums.org/showthread.php?t=2295720&highlight=7265](http://ubuntuforums.org/showthread.php?t=2295720&highlight=7265)

My kernel is 3.19 btw.

I'll post the info from the wifi script in the stickied thread later (the pc only has an hdmi output and my only hdmi 'monitor' is my tv and we are watching shows right now).  I was just hoping for some general advice for now.

edit: just bought windows 10 home usb.  Delivery date is Saturday.  That is how much time I'm allowing myself to tinker with this new ubuntu system:)

edit2:  running apt-get upgrade && sudo apt-get dist-upgrade .  Wifi is so slow... ugh.  Getting 50kbs.  It'll probably take 30min+.  After that I'll run the wifi info script in the sticky.

edit3:  I just noticed that the bluetooth icon and ability to turn bluetooth on/off re-appeared.  Weird.  Why would bluetooth disappear through 2 reboots and reappear on the third reboot?  Anyways... continue to dist-upgrade.  While I wait, Heroes Reborn is a bit cheesy but OK so far hehe.

---

### Post by jwhitener on 2015-09-25
Ever time I try to put the wireless info.txt file into code/code block, the forum says "You have included a total of 9 images in your message. The maximum number that you may include is 8. Please correct the problem and then continue again. " Hrm.

---

### Post by jwhitener on 2015-09-25
Got it, here is the wireless info

```

########## wireless info START ##########

Report from: 25 Sep 2015 13:10 PDT -0700

Booted last: 25 Sep 2015 00:02 PDT -0700

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid

##### kernel ############################

Linux 3.19.0-28-generic #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-V [8086:15a3] (rev 03)
	Subsystem: Intel Corporation Device [8086:2057]
	Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:9010]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

iwlmvm                278528  0 
mac80211              724992  1 iwlmvm
iwlwifi               196608  1 iwlmvm
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7100000-f7120000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39086845 (39.0 MB)  TX bytes:2296079 (2.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"TP-LINK_2.4GHz_27A49D"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]>   
          Bit Rate=108 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       759     1  0 00:02 ?        00:02:13 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-28-generic
GENERAL.FIRMWARE-VERSION:               25.17.12.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     TP-LINK_2.4GHz_27A49D
GENERAL.CON-UUID:                       9b9a06b4-ce26-4513-bb63-01c8c21993e3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     18 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9b9a06b4-ce26-4513-bb63-01c8c21993e3 | TP-LINK_2.4GHz_27A49D
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.0.7/24, gw = 192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1443218995
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_lease_time = 7200
DHCP4.OPTION[15]:                       ip_address = 192.168.0.7
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_interface_mtu = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_netbios_scope = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.3.2-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TP-LINK_5GHz_27A49C    <MAC 'TP-LINK_5GHz_27A49C' [AC2]>  Infra  157   5785 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
TP-LINK_2.4GHz_27A49D  <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/TP-LINK_2.4GHz_27A49D]] (600 root)
[connection] id=TP-LINK_2.4GHz_27A49D | type=wifi
[wifi] ssid=TP-LINK_2.4GHz_27A49D | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.785 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_2.4GHz_27A49D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000009ea3c28
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_5GHz_27A49C' [AC2]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_5GHz_27A49C"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bd6167856
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     03499C43751395EB809E042
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        99:11:2E:F1:A6:BA:85:BE:99:25:82:E9:FE:F3:A2:3F:1A:88:81:75
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.19.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        99:11:2E:F1:A6:BA:85:BE:99:25:82:E9:FE:F3:A2:3F:1A:88:81:75
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     19A5C735A79087003D53D6A
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        99:11:2E:F1:A6:BA:85:BE:99:25:82:E9:FE:F3:A2:3F:1A:88:81:75
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        99:11:2E:F1:A6:BA:85:BE:99:25:82:E9:FE:F3:A2:3F:1A:88:81:75
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

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
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a3 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x095a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    1.968506] iwlwifi 0000:02:00.0: Unsupported splx structure
[    2.062438] iwlwifi 0000:02:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[    2.089600] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    2.090095] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    2.162206] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.827395] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   96.893176] wlan0: authenticate with <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]>
[   96.901401] wlan0: send auth to <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> (try 1/3)
[   96.903837] wlan0: authenticated
[   96.906582] wlan0: associate with <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> (try 1/3)
[   96.921615] wlan0: RX AssocResp from <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> (capab=0x431 status=0 aid=3)
[   96.923998] wlan0: associated
[47216.118945] wlan0: deauthenticating from <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[47220.459872] wlan0: authenticate with <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]>
[47220.464517] wlan0: send auth to <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> (try 1/3)
[47220.466959] wlan0: authenticated
[47220.470674] wlan0: associate with <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> (try 1/3)
[47220.485599] wlan0: RX AssocResp from <MAC 'TP-LINK_2.4GHz_27A49D' [AC1]> (capab=0x431 status=0 aid=3)
[47220.486930] wlan0: associated

########## wireless info END ############

```

---

### Post by jwhitener on 2015-10-24
This turned out to be a hardware issue.  I got a new unit and everything works perfectly now (except Bluetooth... that is still buggy, so I got a logitech 2.4ghz wireless mouse keyboard combo and that works great).

---

