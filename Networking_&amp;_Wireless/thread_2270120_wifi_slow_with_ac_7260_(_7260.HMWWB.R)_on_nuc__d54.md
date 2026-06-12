---
title: "wifi slow with ac 7260 ( 7260.HMWWB.R) on nuc  d54250wyk and ubuntu"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by jankoop2010 on 2015-03-20
Hello everyone, I am new here und use Ubuntu for the first time.....The problem is the wifi. I have searched on different forums but can't find the solution.
Problem: slow wifi with ac 7260
Have a ac router, 

I have already done some work. See below:

  	 	 	 	   ucintel@nucintel-desktop:~$ sudo lshw -C network  
 [sudo] password for nucintel:  
   *-network                
        description: Ethernet interface  
        product: Ethernet Connection I218-V  
        vendor: Intel Corporation  
        physical id: 19  
        bus info: pci@0000:00:19.0  
        logical name: eth0  
        version: 04  
        serial: c0:3f:d5:66:28:99  
        size: 1Gbit/s 
        capacity: 1Gbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.6-4 ip=192.168.178.23 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s  
        resources: irq:60 memory:f7d00000-f7d1ffff memory:f7d3c000-f7d3cfff ioport:f080(size=32)  
   *-network  
        description: Wireless interface  
        product: Wireless 7260  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: bb  
        serial: d8:fc:93:51:14:a4  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-31-generic firmware=25.228.9.0 ip=192.168.178.21 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn  
        resources: irq:62 memory:f7c00000-f7c01fff  
 nucintel@nucintel-desktop:~$ rfkill list  
 0: hci0: Bluetooth  
 	Soft blocked: no  
 	Hard blocked: no  
 1: phy0: Wireless LAN  
 	Soft blocked: no  
 	Hard blocked: no  
 nucintel@nucintel-desktop:~$ lspci -nn | grep -i network  
 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)  
 nucintel@nucintel-desktop:~$ 

 

 nucintel@nucintel-desktop:~$ ls -al /lib/firmware | grep 7260  
 -rw-r--r--  1 root root  683236 nov 24 16:42 iwlwifi-7260-7.ucode  
 -rw-r--r--  1 root root  679780 dec  1 16:16 iwlwifi-7260-8.ucode  
 -rw-r--r--  1 root root  680508 dec  1 21:45 iwlwifi-7260-9.ucode  
 nucintel@nucintel-desktop:~$ lspci -nn | grep 0280  
 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)  
 nucintel@nucintel-desktop:~$ dmesg | grep iwl  
 [    3.039482] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)  
 [    3.039614] iwlwifi 0000:02:00.0: irq 63 for MSI/MSI-X  
 [    3.053373] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm  
 [    3.087633] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144  
 [    3.087690] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 [    3.087913] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 [    3.309947] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'  
 [  367.757654] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 [  367.757882] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 nucintel@nucintel-desktop:~$ dmesg | grep iwl  
 [    3.039482] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)  
 [    3.039614] iwlwifi 0000:02:00.0: irq 63 for MSI/MSI-X  
 [    3.053373] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm  
 [    3.087633] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144  
 [    3.087690] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 [    3.087913] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 [    3.309947] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'  
 [  367.757654] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 [  367.757882] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled  
 nucintel@nucintel-desktop:~$ lspci -nn | grep 0280  
 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)  
 nucintel@nucintel-desktop:~$ 
 

 nucintel@nucintel-desktop:~$ modinfo iwlwifi  
 filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
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
 firmware:       iwlwifi-7265-9.ucode  
 firmware:       iwlwifi-3160-9.ucode  
 firmware:       iwlwifi-7260-9.ucode  
 firmware:       iwlwifi-8000-8.ucode  
 srcversion:     7F17406EFFE91762CB15EEE  
 alias:          pci:v00008086d000024F4sv*sd00000030bc*sc*i*  
 alias:          pci:v00008086d000024F3sv*sd00000010bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*  
 alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*  
 alias:          pci:v00008086d0000095Bsv*sd00009200bc*sc*i*  
 alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*  

etc.
  	 	 	 	   
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*  
 alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*  
 alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*  
 depends:        cfg80211  
 intree:         Y  
 vermagic:       3.16.0-31-generic SMP mod_unload modversions  
 signer:         Magrathea: Glacier signing key  
 sig_key:        6A:63:E8:EF:0C:63:AB:DB:14:5F:D1:7C:AA:A9:7B:8C:69:73:45:84  
 sig_hashalgo:   sha512  
 parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)  
 parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)  
 parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)  
 parm:           fw_restart:restart firmware in case of error (default true) (bool)  
 parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int) 
 parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)  
 parm:           nvm_file:NVM file name (charp)  
 parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)  
 parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)  
 parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)  
 parm:           power_save:enable WiFi power management (default: disable) (bool)  
 parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)  
 parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)  
 nucintel@nucintel-desktop:~$ 
  
What could be the solution?


Thanks,

---

### Post by jeremy31 on 2015-03-20
Run the wireless script in the sticky post "before posting in Networking and Wireless" and post the results as there might be other issues other than the most common one for 7260 cards

---

### Post by jankoop2010 on 2015-03-21
[> quote]

hello, here is the file.
########## wireless info start ##########

report from: 21 mar 2015 09:41 cet +0100

booted last: 21 mar 2015 09:37 cet +0100

script from: 20 sep 2014 23:04 utc +0000

##### release ###########################

distributor id:    Ubuntu
description:    Ubuntu 14.04.2 lt

release:    14.04
codename:    Trusty

##### kernel ############################

linux 3.16.0-31-generic #43~14.04.1-ubuntu smp tue mar 10 20:13:38 utc 2015 x86_64 x86_64 x86_64 gnu/linux

parameters: Ro, quiet, splash, vt.handoff=7

##### desktop ###########################

ubuntu

##### lspci #############################

00:19.0 ethernet controller [0200]: Intel corporation ethernet connection i218-v [8086:1559] (rev 04)
    subsystem: Intel corporation device [8086:2054]
    kernel driver in use: E1000e

02:00.0 network controller [0280]: Intel corporation wireless 7260 [8086:08b1] (rev bb)
    subsystem: Intel corporation dual band wireless-ac 7260 [8086:4070]
    kernel driver in use: Iwlwifi

##### lsusb #############################

bus 001 device 002: Id 8087:8000 intel corp. 
Bus 001 device 001: Id 1d6b:0002 linux foundation 2.0 root hub
bus 003 device 001: Id 1d6b:0003 linux foundation 3.0 root hub
bus 002 device 003: Id 8087:07dc intel corp. 
Bus 002 device 002: Id 046d:c52b logitech, inc. Unifying receiver
bus 002 device 001: Id 1d6b:0002 linux foundation 2.0 root hub

##### pcmcia card info ##################

##### rfkill ############################

0: Hci0: Bluetooth
    soft blocked: No
    hard blocked: No
1: Phy0: Wireless lan
    soft blocked: No
    hard blocked: No

##### lsmod #############################

iwlmvm                217686  0 
mac80211              652718  1 iwlmvm
iwlwifi               179412  1 iwlmvm
cfg80211              494330  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7  snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      link encap:ethernet  hwaddr <mac 'eth0' [if]>  
          inet addr:192.168.178.23  bcast:192.168.178.255  mask:255.255.255.0
          inet6 addr: 2001:980:ad92:1:c23f:d5ff:fe66:2899/64 scope:global
          inet6 addr: Fd00::c23f:d5ff:fe66:2899/64 scope:global
          inet6 addr: Fe80::c23f:d5ff:fe66:2899/64 scope:link
          inet6 addr: 2001:980:ad92:1:140c:ae4d:1004:90cc/64 scope:global
          up broadcast running multicast  mtu:1500  metric:1
          rx packets:561 errors:0 dropped:0 overruns:0 frame:0
          tx packets:575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          rx bytes:130800 (130.8 kb)  tx bytes:58016 (58.0 kb)
          interrupt:20 memory:f7d00000-f7d20000 

wlan0     link encap:ethernet  hwaddr <mac 'wlan0' [if]>  
          inet addr:192.168.178.21  bcast:192.168.178.255  mask:255.255.255.0
          inet6 addr: 2001:980:ad92:1:dafc:93ff:fe51:14a4/64 scope:global
          inet6 addr: Fd00::dafc:93ff:fe51:14a4/64 scope:global
          inet6 addr: 2001:980:ad92:1:c93a:2b58:2df4:7709/64 scope:global
          inet6 addr: Fe80::dafc:93ff:fe51:14a4/64 scope:link
          up broadcast running multicast  mtu:1500  metric:1
          rx packets:44202 errors:0 dropped:0 overruns:0 frame:0
          tx packets:32471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          rx bytes:41846207 (41.8 mb)  tx bytes:39060144 (39.0 mb)

##### iwconfig ##########################

eth0      no wireless extensions.

Lo        no wireless extensions.

Wlan0     ieee 802.11abgn  essid:"tapis"  
          mode:managed  frequency:5.18 ghz  access point: <mac 'tapis' [ac1]>   
          bit rate=6 mb/s   tx-power=20 dbm   
          retry short limit:7   rts thr:eek:ff   fragment thr:eek:ff
          power management:eek:n
          link quality=48/70  signal level=-62 dbm  
          rx invalid nwid:0  rx invalid crypt:0  rx invalid frag:0
          tx excessive retries:0  invalid misc:111   missed beacon:0

##### route #############################

kernel ip routing table
destination     gateway         genmask         flags metric ref    use iface
0.0.0.0         192.168.178.1   0.0.0.0         ug    0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   u     1      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   u     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### nm-tool ###########################

networkmanager tool

state: Connected (global)

- device: Wlan0  [tapis] -------------------------------------------------------
  type:              802.11 wifi
  driver:            Iwlwifi
  state:             Connected
  default:           No
  hw address:        <mac 'wlan0' [if]>

  capabilities:
    Speed:           6 mb/s

  wireless properties
    wep encryption:  Yes
    wpa encryption:  Yes
    wpa2 encryption: Yes

  wireless access points (* = current ap)
    kikker:          Infra, <mac 'kikker' [ac4]>, freq 2412 mhz, rate 54 mb/s, strength 72 wpa2
    korakk:          Infra, <mac 'korakk' [ac5]>, freq 2437 mhz, rate 54 mb/s, strength 72 wpa wpa2
    direct-tdscx-3400: Infra, <mac 'direct-tdscx-3400' [ac2]>, freq 2412 mhz, rate 54 mb/s, strength 57 wpa2
    korakka:         Infra, <mac 'korakka' [ac7]>, freq 5220 mhz, rate 54 mb/s, strength 39 wpa wpa2
    korakk-guest:    Infra, <mac 'korakk-guest' [ac6]>, freq 2437 mhz, rate 54 mb/s, strength 69
    *tapis:          Infra, <mac 'tapis' [ac1]>, freq 5180 mhz, rate 54 mb/s, strength 58 wpa2
    pinquin:         Infra, <mac 'pinquin' [ac3]>, freq 2412 mhz, rate 54 mb/s, strength 74 wpa2

  ipv4 settings:
    Address:         192.168.178.21
    prefix:          24 (255.255.255.0)
    gateway:         192.168.178.1

    dns:             192.168.178.1

  ipv6 settings:
    Address:         Fd00::dafc:93ff:fe51:14a4
    prefix:          64
    gateway:         ::

    Address:         2001:980:ad92:1:c93a:2b58:2df4:7709
    prefix:          64
    gateway:         ::

    Address:         2001:980:ad92:1:dafc:93ff:fe51:14a4
    prefix:          64
    gateway:         ::

    Address:         Fe80::dafc:93ff:fe51:14a4
    prefix:          64
    gateway:         ::

    Dns:             Fd00::3631:c4ff:fe8a:a610

- device: Eth0  [wired connection 1] -------------------------------------------
  type:              Wired
  driver:            E1000e
  state:             Connected
  default:           Yes
  hw address:        <mac 'eth0' [if]>

  capabilities:
    Carrier detect:  Yes
    speed:           1000 mb/s

  wired properties
    carrier:         On

  ipv4 settings:
    Address:         192.168.178.23
    prefix:          24 (255.255.255.0)
    gateway:         192.168.178.1

    dns:             192.168.178.1

  ipv6 settings:
    Address:         Fd00::c23f:d5ff:fe66:2899
    prefix:          64
    gateway:         ::

    Address:         2001:980:ad92:1:140c:ae4d:1004:90cc
    prefix:          64
    gateway:         ::

    Address:         2001:980:ad92:1:c23f:d5ff:fe66:2899
    prefix:          64
    gateway:         ::

    Address:         Fe80::c23f:d5ff:fe66:2899
    prefix:          64
    gateway:         ::

    Dns:             Fd00::3631:c4ff:fe8a:a610

##### networkmanager.state ##############

[main]
networkingenabled=true
wirelessenabled=true
wwanenabled=true
wimaxenabled=true

##### networkmanager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### networkmanager profiles ###########

[[/etc/networkmanager/system-connections/pinquin]] (600 root)
[connection] id=pinquin | type=802-11-wireless
[802-11-wireless] ssid=pinquin | mac-address=<mac 'wlan0' [if]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/networkmanager/system-connections/tapis]] (600 root)
[connection] id=tapis | type=802-11-wireless
[802-11-wireless] ssid=tapis | mac-address=<mac 'wlan0' [if]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

region: Europe/amsterdam (based on set time zone)

country de:
    (2400 - 2483 @ 40), (n/a, 20)
    (5150 - 5250 @ 40), (n/a, 20), no-outdoor
    (5250 - 5350 @ 40), (n/a, 20), no-outdoor, dfs
    (5470 - 5725 @ 40), (n/a, 26), dfs
    (57240 - 65880 @ 2160), (n/a, 40), no-outdoor

##### iwlist channels ###################

eth0      no frequency information.

Lo        no frequency information.

Wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 ghz
          channel 02 : 2.417 ghz
          channel 03 : 2.422 ghz
          channel 04 : 2.427 ghz
          channel 05 : 2.432 ghz
          channel 06 : 2.437 ghz
          channel 07 : 2.442 ghz
          channel 08 : 2.447 ghz
          channel 09 : 2.452 ghz
          channel 10 : 2.457 ghz
          channel 11 : 2.462 ghz
          channel 12 : 2.467 ghz
          channel 13 : 2.472 ghz
          channel 36 : 5.18 ghz
          channel 40 : 5.2 ghz
          channel 44 : 5.22 ghz
          channel 48 : 5.24 ghz
          channel 52 : 5.26 ghz
          channel 56 : 5.28 ghz
          channel 60 : 5.3 ghz
          channel 64 : 5.32 ghz
          channel 100 : 5.5 ghz
          channel 104 : 5.52 ghz
          channel 108 : 5.54 ghz
          channel 112 : 5.56 ghz
          channel 116 : 5.58 ghz
          channel 120 : 5.6 ghz
          channel 124 : 5.62 ghz
          channel 128 : 5.64 ghz
          channel 132 : 5.66 ghz
          channel 136 : 5.68 ghz
          channel 140 : 5.7 ghz
          current frequency:5.18 ghz (channel 36)

##### iwlist scan #######################

channel occupancy:

      3   aps on   frequency:2.412 ghz (channel 1)
      2   aps on   frequency:2.437 ghz (channel 6)
      1   aps on   frequency:5.18 ghz (channel 36)
      1   aps on   frequency:5.22 ghz (channel 44)

eth0      interface doesn't support scanning.

Wlan0     scan completed :
          Cell 01 - address: <mac 'tapis' [ac1]>
                    channel:36
                    frequency:5.18 ghz (channel 36)
                    quality=43/70  signal level=-67 dbm  
                    encryption key:eek:n
                    essid:"tapis"
                    bit rates:6 mb/s; 9 mb/s; 12 mb/s; 18 mb/s; 24 mb/s
                              36 mb/s; 48 mb/s; 54 mb/s
                    mode:master
                    extra:tsf=0000021ec0bad8a6
                    extra: Last beacon: 84ms ago
                    ie: Ieee 802.11i/wpa2 version 1
                        group cipher : Ccmp
                        pairwise ciphers (1) : Ccmp
                        authentication suites (1) : Psk
          cell 02 - address: <mac 'direct-tdscx-3400' [ac2]>
                    channel:1
                    frequency:2.412 ghz (channel 1)
                    quality=40/70  signal level=-70 dbm  
                    encryption key:eek:n
                    essid:"direct-tdscx-3400"
                    bit rates:6 mb/s; 9 mb/s; 12 mb/s; 18 mb/s; 24 mb/s
                              36 mb/s; 48 mb/s; 54 mb/s
                    mode:master
                    extra:tsf=000000108f77c35b
                    extra: Last beacon: 84ms ago
                    ie: Ieee 802.11i/wpa2 version 1
                        group cipher : Ccmp
                        pairwise ciphers (1) : Ccmp
                        authentication suites (1) : Psk
          cell 03 - address: <mac 'pinquin' [ac3]>
                    channel:1
                    frequency:2.412 ghz (channel 1)
                    quality=46/70  signal level=-64 dbm  
                    encryption key:eek:n
                    essid:"pinquin"
                    bit rates:1 mb/s; 2 mb/s; 5.5 mb/s; 11 mb/s; 6 mb/s
                              9 mb/s; 12 mb/s; 18 mb/s
                    bit rates:24 mb/s; 36 mb/s; 48 mb/s; 54 mb/s
                    mode:master
                    extra:tsf=0000001026993be8
                    extra: Last beacon: 84ms ago
                    ie: Ieee 802.11i/wpa2 version 1
                        group cipher : Ccmp
                        pairwise ciphers (1) : Ccmp
                        authentication suites (1) : Psk
          cell 04 - address: <mac 'kikker' [ac4]>
                    channel:1
                    frequency:2.412 ghz (channel 1)
                    quality=47/70  signal level=-63 dbm  
                    encryption key:eek:n
                    essid:"kikker"
                    bit rates:1 mb/s; 2 mb/s; 5.5 mb/s; 11 mb/s; 6 mb/s
                              9 mb/s; 12 mb/s; 18 mb/s
                    bit rates:24 mb/s; 36 mb/s; 48 mb/s; 54 mb/s
                    mode:master
                    extra:tsf=0000001026992a79
                    extra: Last beacon: 84ms ago
                    ie: Ieee 802.11i/wpa2 version 1
                        group cipher : Ccmp
                        pairwise ciphers (1) : Ccmp
                        authentication suites (1) : Psk
          cell 05 - address: <mac 'korakk' [ac5]>
                    channel:6
                    frequency:2.437 ghz (channel 6)
                    quality=56/70  signal level=-54 dbm  
                    encryption key:eek:n
                    essid:"korakk"
                    bit rates:1 mb/s; 2 mb/s; 5.5 mb/s; 11 mb/s; 18 mb/s
                              24 mb/s; 36 mb/s; 54 mb/s
                    bit rates:6 mb/s; 9 mb/s; 12 mb/s; 48 mb/s
                    mode:master
                    extra:tsf=000001510dcb5252
                    extra: Last beacon: 84ms ago
                    ie: Ieee 802.11i/wpa2 version 1
                        group cipher : Tkip
                        pairwise ciphers (2) : Ccmp tkip
                        authentication suites (1) : Psk
                    ie: Wpa version 1
                        group cipher : Tkip
                        pairwise ciphers (2) : Ccmp tkip
                        authentication suites (1) : Psk

800003a4000027a4000042435e0062322f00
          cell 06 - address: <mac 'korakk-guest' [ac6]>
                    channel:6
                    frequency:2.437 ghz (channel 6)
                    quality=55/70  signal level=-55 dbm  
                    encryption key:eek:ff
                    essid:"korakk-guest"
                    bit rates:1 mb/s; 2 mb/s; 5.5 mb/s; 11 mb/s; 18 mb/s
                              24 mb/s; 36 mb/s; 54 mb/s
                    bit rates:6 mb/s; 9 mb/s; 12 mb/s; 48 mb/s
                    mode:master
                    extra:tsf=000001510dcb6014
                    extra: Last beacon: 84ms ago
          cell 07 - address: <mac 'korakka' [ac7]>
                    channel:44
                    frequency:5.22 ghz (channel 44)
                    quality=33/70  signal level=-77 dbm  
                    encryption key:eek:n
                    essid:"korakka"
                    bit rates:6 mb/s; 9 mb/s; 12 mb/s; 18 mb/s; 24 mb/s
                              36 mb/s; 48 mb/s; 54 mb/s
                    mode:master
                    extra:tsf=000001510dd8c850
                    extra: Last beacon: 84ms ago
                    ie: Ieee 802.11i/wpa2 version 1
                        group cipher : Tkip
                        pairwise ciphers (2) : Ccmp tkip
                        authentication suites (1) : Psk
                    ie: Wpa version 1
                        group cipher : Tkip
                        pairwise ciphers (2) : Ccmp tkip
                        authentication suites (1) : Psk

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        Gpl
author:         Copyright(c) 2003- 2014 intel corporation <ilw@linux.intel.com>
version:        In-tree:
Description:    The new intel(r) wireless agn driver for linux
srcversion:     67a588094ae9cdecb593782
depends:        Iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-31-generic smp mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6a:63:e8:ef:0c:63:ab:grin:b:14:5f:grin:1:7c:aa:a9:7b:8c:69:73:45:84
sig_hashalgo:   Sha512
parm:           Init_dbg:set to true to debug an assert in init fw (default: False (bool)
parm:           Power_scheme:razz:ower management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        Gpl
description:    Ieee 802.11 subsystem
srcversion:     D0cbadabd6f74a53b0be7cc
depends:        Cfg80211
intree:         Y
vermagic:       3.16.0-31-generic smp mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6a:63:e8:ef:0c:63:ab:grin:b:14:5f:grin:1:7c:aa:a9:7b:8c:69:73:45:84
sig_hashalgo:   Sha512
parm:           Max_nullfunc_tries:maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           Max_probe_tries:maximum probe tries before disconnecting (reason 4). (int)
parm:           Beacon_loss_count:number of beacon intervals before we decide beacon was lost. (int)
parm:           Probe_wait_ms:maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           Ieee80211_default_rc_algo:grin:efault rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        Gpl
author:         Copyright(c) 2003- 2014 intel corporation <ilw@linux.intel.com>
version:        In-tree:
Description:    Intel(r) wireless wifi driver for linux
firmware:       Iwlwifi-100-5.ucode
firmware:       Iwlwifi-1000-5.ucode
firmware:       Iwlwifi-135-6.ucode
firmware:       Iwlwifi-105-6.ucode
firmware:       Iwlwifi-2030-6.ucode
firmware:       Iwlwifi-2000-6.ucode
firmware:       Iwlwifi-5150-2.ucode
firmware:       Iwlwifi-5000-5.ucode
firmware:       Iwlwifi-6000g2b-6.ucode
firmware:       Iwlwifi-6000g2a-5.ucode
firmware:       Iwlwifi-6050-5.ucode
firmware:       Iwlwifi-6000-4.ucode
firmware:       Iwlwifi-7265-9.ucode
firmware:       Iwlwifi-3160-9.ucode
firmware:       Iwlwifi-7260-9.ucode
firmware:       Iwlwifi-8000-8.ucode
srcversion:     7f17406effe91762cb15eee
depends:        Cfg80211
intree:         Y
vermagic:       3.16.0-31-generic smp mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6a:63:e8:ef:0c:63:ab:grin:b:14:5f:grin:1:7c:aa:a9:7b:8c:69:73:45:84
sig_hashalgo:   Sha512
parm:           Swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: Full,  2: Disable agg tx, 4: Disable agg rx, 8 enable agg tx (uint)
parm:           Amsdu_size_8k:enable 8k amsdu size (default 0) (int)
parm:           Fw_restart:restart firmware in case of error (default true) (bool)
parm:           Antenna_coupling:specify antenna coupling in db (defualt: 0 db) (int)
parm:           Wd_disable:grin:isable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           Nvm_file:nvm file name (charp)
parm:           Uapsd_disable:disable u-apsd functionality (default: Y) (bool)
parm:           Bt_coex_active:enable wifi/bt co-exist (default: Enable) (bool)
parm:           Led_mode:0=system default, 1=on(rf on)/off(rf off), 2=blinking, 3=off (default: 0) (int)
parm:           Power_save:enable wifi power management (default: Disable) (bool)
parm:           Power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           Fw_monitor:firmware monitor - to debug fw (default: False - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    Wireless configuration support
license:        Gpl
author:         Johannes berg
srcversion:     88153da7841870e4f2012ee
depends:        
Intree:         Y
vermagic:       3.16.0-31-generic smp mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6a:63:e8:ef:0c:63:ab:grin:b:14:5f:grin:1:7c:aa:a9:7b:8c:69:73:45:84
sig_hashalgo:   Sha512
parm:           Ieee80211_regdom:ieee 802.11 regulatory domain code (charp)
parm:           Cfg80211_disable_40mhz_24ghz:grin:isable 40mhz support in the 2.4ghz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: Minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8k: 0
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: Mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# pci device 0x8086:0x1559 (e1000e)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="<mac  'eth0' [if]>", attr{dev_id}=="0x0", attr{type}=="1", kernel=="eth*",  name="eth0"
# pci device 0x8086:0x08b1 (iwlwifi)
subsystem=="net", action=="add", drivers=="?*", attr{address}=="<mac  'wlan0' [if]>", attr{dev_id}=="0x0", attr{type}=="1",  kernel=="wlan*", name="wlan0"

##### dmesg #############################

[    2.771600] iwlwifi 0000:02:00.0: Enabling device (0000 -> 0002)
[    2.772771] iwlwifi 0000:02:00.0: Irq 63 for msi/msi-x
[    2.801857] iwlwifi 0000:02:00.0: Loaded firmware version 25.228.9.0 op_mode iwlmvm
[    2.841057] iwlwifi 0000:02:00.0: Detected intel(r) dual band wireless ac 7260, rev=0x144
[    2.841111] iwlwifi 0000:02:00.0: L1 disabled - ltr enabled (repeated 2 times)
[    3.050453] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.436650] iwlwifi 0000:02:00.0: L1 disabled - ltr enabled (repeated 2 times)
[    3.448087] ipv6: Addrconf(netdev_up): Wlan0: Link is not ready
[    7.050073] wlan0: Authenticate with <mac 'tapis' [ac1]>
[    7.053062] wlan0: Direct probe to <mac 'tapis' [ac1]> (try 1/3)
[    7.254199] wlan0: Direct probe to <mac 'tapis' [ac1]> (try 2/3)
[    7.458404] wlan0: Send auth to <mac 'tapis' [ac1]> (try 3/3)
[    7.468619] wlan0: Authenticated
[    7.469122] wlan0: Associate with <mac 'tapis' [ac1]> (try 1/3)
[    7.536248] wlan0: Rx assocresp from <mac 'tapis' [ac1]> (capab=0x411 status=0 aid=1)
[    7.537611] wlan0: Associated
[    7.537648] ipv6: Addrconf(netdev_change): Wlan0: Link becomes ready
[    7.641495] wlan0: Limiting tx power to 20 (23 - 3) dbm as advertised by <mac 'tapis' [ac1]>

########## wireless info end ############[/quote]

---

### Post by jeremy31 on 2015-03-21
What normally helps is ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```  Note that this doesn't disable anything, it enables agg TX which usually helps with slow speed

---

### Post by jankoop2010 on 2015-03-21
Thanks. I have used your code but it does not  help. 2.4 Ghz:ping 5 ms, down  16 Mbps, Up 28, 5 Ghz: ping 6 ms,down 12 Mbps, Up 12.
Normally should it be about 50/50

---

### Post by jeremy31 on 2015-03-21
> **jankoop2010 said:**
> Thanks. I have used your code but it does not  help. 2.4 Ghz:ping 5 ms, down  16 Mbps, Up 28, 5 Ghz: ping 6 ms,down 12 Mbps, Up 12.
Normally should it be about 50/50

Did you reboot after the code, I forgot that part

---

### Post by jankoop2010 on 2015-03-21
yes, I have reboot. But the speed is still very slow! I compared it with the wifi on the same place with another computer and there is a remarkeble difference. Is it possible and has it sense  to take another driver version, eg 10.ucode? And yes, how can I install this code to replace 9.ucode?

---

### Post by jeremy31 on 2015-03-21
Once you have the 10.ucode you could use the cp command to copy it to /lib/firmware/ with it renamed as the 9.ucode ```
sudo cp iwlwifi-7260-10.ucode /lib/firmware/iwlwifi-7260-9.ucode
```

---

### Post by jankoop2010 on 2015-03-22
Thanks. When I download the 10.ucode, in which map should it be to use the code descibed above? And when this 10.ucode does not function how can I return to the 9.ucode?

---

### Post by jeremy31 on 2015-03-22
> **jankoop2010 said:**
> Thanks. When I download the 10.ucode, in which map should it be to use the code descibed above? And when this 10.ucode does not function how can I return to the 9.ucode?

You can either copy the 9 code somewhere to back it up ```
sudo cp /lib/firmware/iwlwifi-7260-9.ucode /lib/firmware/iwlwifi-7260-9.ucode.bak
```
Should work or you could just download a new copy or reinstall linux-firmware

Do you have IPv6 disabled in Network Manager for your connection, as it might help speed it up also

---

