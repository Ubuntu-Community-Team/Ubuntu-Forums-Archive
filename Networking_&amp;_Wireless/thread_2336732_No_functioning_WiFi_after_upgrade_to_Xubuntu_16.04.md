---
title: "No functioning WiFi after upgrade to Xubuntu 16.04"
date: 2016-09-10
forum: Networking &amp; Wireless
---

### Post by Amanda_L._Moen on 2016-09-10
I'm using a Dell Inspiron 1525, originally running Windows XP service pack 3, but set up for dual boot for about 2 years. I was running Xubuntu 14 just fine, aside from a short period last July where I ran out of space, and ended up with a corrupted upgrade that caused the OS to seem to not recognize the NIC. Thankfully, with the help of this community, I was able to clear a bunch of old, unused items off the partition, and load into an older version of my OS. And was able to get everything up and running again. 

Sadly, this time around, I accidentally deleted the older versions of the OS, plus, I lost my USB boot disk. A friend made a USB boot disk with Xubuntu 16.04 for me to have. I did a clean install, yet the wireless portion has yet to work. If I hardwire in to the network, it works fine.

---

### Post by howefield on 2016-09-10
Thread moved to the "*Networking & Wireless*" forum for a better fit.

Perhaps you could run the wireless script as detailed in this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") so someone who can help has something to work with.

---

### Post by Amanda_L._Moen on 2016-09-10
Can't seem to attach the wireless-info.txt.  Hope that I am doing this right.

Haha, I finally figured it out, and I think I got it to work this time.

```


########## wireless info START ##########

Report from: 10 Sep 2016 14:28 PDT -0700

Booted last: 10 Sep 2016 00:00 PDT -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell 88E8040 PCI-E Fast Ethernet Controller [1028:022f]
    Kernel driver in use: sky2

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   401408  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            24576  0
bcma                   49152  1 b43
mac80211              659456  1 b43
dcdbas                 16384  1 dell_laptop
cfg80211              499712  2 b43,mac80211
ssb_hcd                16384  0
ssb                    57344  2 b43,ssb_hcd
wmi                    20480  1 dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF1]>  
          inet addr:10.77.153.116  Bcast:10.77.159.255  Mask:255.255.240.0
          inet6 addr: fe80::6565:d3a9:fa59:d48c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129261337 (129.2 MB)  TX bytes:4168275 (4.1 MB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15172 (15.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Master  Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.77.144.1     0.0.0.0         UG    100    0        0 enp9s0
10.42.0.0       0.0.0.0         255.255.255.0   U     600    0        0 wlan0
10.77.144.0     0.0.0.0         255.255.240.0   U     100    0        0 enp9s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp9s0

##### resolv.conf #######################

nameserver 127.0.1.1
search corp.porch.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       611     1  0 10:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8040 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:09:00.0/net/enp9s0
GENERAL.IP-IFACE:                       enp9s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c3dcd9b7-613f-4df6-8497-0586ca87fa5f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c3dcd9b7-613f-4df6-8497-0586ca87fa5f | Wired connection 1
IP4.ADDRESS[1]:                         10.77.153.116/20
IP4.GATEWAY:                            10.77.144.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.77.144.8
IP4.DNS[2]:                             10.77.144.14
IP4.DOMAIN[1]:                          corp.porch.com
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1473570223
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.77.144.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.77.153.116
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = corp.porch.com
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.77.159.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 28800
DHCP4.OPTION[23]:                       domain_name_servers = 10.77.144.8 10.77.144.14
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.240.0
DHCP4.OPTION[26]:                       network_number = 10.77.144.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.77.144.1
IP6.ADDRESS[1]:                         fe80::6565:d3a9:fa59:d48c/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4321 802.11a/b/g/n (Wireless 1500 Draft 802.11n WLAN Mini-card)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     BlackBerry Classic - Amanda
GENERAL.CON-UUID:                       e9c65696-0c10-4bbb-a10d-c88dacc9e0a7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   845c6767-15b8-4c98-9e6c-9597ea43961c | Frontier_9550
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   e9c65696-0c10-4bbb-a10d-c88dacc9e0a7 | BlackBerry Classic - Amanda
IP4.ADDRESS[1]:                         10.42.0.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF2]>/64
IP6.GATEWAY:                            

SSID                         BSSID              MODE   CHAN  FREQ      RATE      SIGNAL  BARS  SECURITY   ACTIVE  * 
BlackBerry Classic - Amanda  <MAC 'wlan0' [IF2]>  Infra  1     2412 MHz  0 Mbit/s  0       ____  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/BlackBerry Classic - Amanda]] (600 root)
[connection] id=BlackBerry Classic - Amanda | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=BlackBerry Classic - Amanda
[ipv4] method=shared
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Frontier_9550]] (600 root)
[connection] id=Frontier_9550 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Frontier_9550
[ipv4] method=shared
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

lo        no frequency information.

enp9s0    no frequency information.

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Operation not supported

lo        Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 
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
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 

[ssb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[12296.448307]  r592 snd_seq_device dell_smm_hwmon snd_timer irqbypass r852 memstick ssb_hcd sm_common joydev input_leds nand nand_ecc serio_raw nand_bch snd soundcore bch nand_ids mtd shpchp lpc_ich mac_hid parport_pc ppdev lp parport autofs4 ahci libahci psmouse firewire_ohci firewire_core sdhci_pci i915 pata_acpi sdhci ssb crc_itu_t sky2 i2c_algo_bit wmi drm_kms_helper fjes syscopyarea sysfillrect video sysimgblt fb_sys_fops drm
[12981.475897] sky2 0000:09:00.0 enp9s0: Link is up at 100 Mbps, full duplex, flow control rx
[12981.476736] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-09-10
Hello, you actually posted the script we need to see the file it created it is in your home folder.

---

### Post by Amanda_L._Moen on 2016-09-10
Okay, I think I have this right this time.  I edited the earlier post, and put the results in the Code tags.

---

### Post by wildmanne39 on 2016-09-10
Disable your wired connection then while you are in network manager change IPV4 setting to Automatic (DHCP) for your wireless connection then save and close.

If it does not connect run the script again and post the file you can just use this command:
```
./wireless-info
```
Thanks

---

### Post by Amanda_L._Moen on 2016-09-10
There in may lay my problem.  I can't seem to get to the "Network Manager". I can get to "Network Settings", but it looks like a very compact version of what it is supposed to look like, at least according to the image shown when you open up the Help file for Network Settings.

---

### Post by wildmanne39 on 2016-09-10
Please attach a screenshot of what you see.

---

### Post by Amanda_L._Moen on 2016-09-10
If I open the Network Administration dialog box via the terminal I get this response from the terminal:
>  Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

Couldn't figure out the whole attachment thing.  (I swear, I used to be really good at using forums.)

[URL="http://i.imgur.com/ixgZNZl.png"]
  [IMG]http://imgur.com/ixgZNZll.png[/IMG]
[/URL]

---

### Post by wildmanne39 on 2016-09-10
There should be two arrows in the top right corner of the screen click on it and make sure enable networking and enable wireless is checked then click on wireless connection and while you are in network manager change IPV4 setting to Automatic (DHCP) for your wireless connection then save and close. Then network manager should find your connection.

---

### Post by Amanda_L._Moen on 2016-09-10
> **Wild Man said:**
> There should be two arrows in the top right corner of the screen click on it and make sure enable networking and enable wireless is checked then click on wireless connection and while you are in network manager change IPV4 setting to Automatic (DHCP) for your wireless connection then save and close. Then network manager should find your connection.

Enable Networking and Enable Wi-Fi are both checked.  I am not seeing 'wireless connection' as an option to select.

Here's a list of what shows up when I click on the two arrows in the top right corner:
Ethernet Network (which is shaded out, can't select)
Wired Connection 1
Disconnect

Wi-Fi Network (shaded out, can't select)
BlackBerry Classic - Amanda (not connected)
Disconnect

Connect to Hidden Wi-Fi Network...
Create New Wi-Fi Network...

VPN Connections (with a dropdown menu)

Enable Networking (check mark in front)
Enable Wi-Fi (check mark in front)

Connection Information
Edit Connections...

---

### Post by wildmanne39 on 2016-09-10
Click on Edit Connections and you should see your wifi just click on it and you should be able to change the IPV4 setting like I asked in the other posts.

---

### Post by Amanda_L._Moen on 2016-09-10
I wasn't being intentionally obtuse, I just needed clarification.  I didn't want to give you the wrong information.
```

########## wireless info START ##########

Report from: 10 Sep 2016 16:58 PDT -0700

Booted last: 10 Sep 2016 00:00 PDT -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:00:59 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell 88E8040 PCI-E Fast Ethernet Controller [1028:022f]
    Kernel driver in use: sky2

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   401408  0
dell_laptop            24576  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
bcma                   49152  1 b43
dcdbas                 16384  1 dell_laptop
mac80211              659456  1 b43
cfg80211              499712  2 b43,mac80211
ssb_hcd                16384  0
ssb                    57344  2 b43,ssb_hcd
wmi                    20480  1 dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:45037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30443955 (30.4 MB)  TX bytes:3240650 (3.2 MB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:16247 (16.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

wlan0     IEEE 802.11abg  Mode:Master  Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.0.0       0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       587     1  0 16:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4321 802.11a/b/g/n (Wireless 1500 Draft 802.11n WLAN Mini-card)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     BlackBerry Classic - Amanda
GENERAL.CON-UUID:                       e9c65696-0c10-4bbb-a10d-c88dacc9e0a7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e9c65696-0c10-4bbb-a10d-c88dacc9e0a7 | BlackBerry Classic - Amanda
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   845c6767-15b8-4c98-9e6c-9597ea43961c | Frontier_9550
IP4.ADDRESS[1]:                         10.42.0.1/24
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan0' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8040 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:09:00.0/net/enp9s0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                         BSSID              MODE   CHAN  FREQ      RATE      SIGNAL  BARS  SECURITY   ACTIVE  * 
BlackBerry Classic - Amanda  <MAC 'wlan0' [IF2]>  Infra  1     2412 MHz  0 Mbit/s  0       ____  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/BlackBerry Classic - Amanda]] (600 root)
[connection] id=BlackBerry Classic - Amanda | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=BlackBerry Classic - Amanda
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Frontier_9550]] (600 root)
[connection] id=Frontier_9550 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Frontier_9550
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

lo        no frequency information.

enp9s0    no frequency information.

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Operation not supported

lo        Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 

[ssb]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[   14.590727] b43-phy0: Broadcom 4321 WLAN found (core revision 12)
[   14.624064] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 2
[   14.624093] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2055, Revision 4, Version 0
[   28.011923] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[   28.014621] sky2 0000:09:00.0 enp9s0: enabling interface
[   28.014756] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[   28.038206] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.216080] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   28.348558] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   31.450676] sky2 0000:09:00.0 enp9s0: Link is up at 100 Mbps, full duplex, flow control rx
[   31.450697] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready
[   37.184074] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   37.304231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.360215] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  558.136309] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  558.317128] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  566.564268] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  566.692368] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  566.716650] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2210.240248] sky2 0000:09:00.0 enp9s0: Link is down

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-09-10
The information looks better,  did you name the wifi wlan0 because in 16.04 that is not what it should be called.

Go into network manager and change master mode to infrastructure if you have that setting if not client.

---

### Post by Amanda_L._Moen on 2016-09-14
No, I did not name the wifi wlan0.  

Okay, I changed Mode to Client.  Things seem to actually be working now.  When I select the network/wireless manager in the upper right corner it is finally showing me all of the wireless networks available that the wifi can see.  Before, I couldn't see any available networks.

Thank you.
```


########## wireless info START ##########

Report from: 14 Sep 2016 12:45 PDT -0700

Booted last: 14 Sep 2016 00:00 PDT -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:00:59 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell 88E8040 PCI-E Fast Ethernet Controller [1028:022f]
    Kernel driver in use: sky2

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card [1028:000a]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   401408  0
dell_laptop            24576  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
bcma                   49152  1 b43
dcdbas                 16384  1 dell_laptop
mac80211              659456  1 b43
cfg80211              499712  2 b43,mac80211
ssb_hcd                16384  0
ssb                    57344  2 b43,ssb_hcd
wmi                    20480  1 dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:53784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35169495 (35.1 MB)  TX bytes:4261338 (4.2 MB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.254.4  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::3ddc:bf73:be50:564a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:471865 (471.8 KB)  TX bytes:160879 (160.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp9s0    no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Frontier_9550"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Frontier_9550' [AN1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:164  Invalid misc:84   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.254.0   0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       587     1  0 Sep10 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4321 802.11a/b/g/n (Wireless 1500 Draft 802.11n WLAN Mini-card)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Frontier_9550 1
GENERAL.CON-UUID:                       221e12d5-e055-48df-a56c-0d66d6fde0d1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   221e12d5-e055-48df-a56c-0d66d6fde0d1 | Frontier_9550 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   845c6767-15b8-4c98-9e6c-9597ea43961c | Frontier_9550
IP4.ADDRESS[1]:                         192.168.254.4/24
IP4.GATEWAY:                            192.168.254.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.254.254
IP4.DNS[2]:                             74.40.74.41
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1473895911
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.254.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.254.4
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.254.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 14400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.254.254 74.40.74.41
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.254.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.254.254
IP6.ADDRESS[1]:                         fe80::3ddc:bf73:be50:564a/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8040 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:09:00.0/net/enp9s0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Frontier_9550  <MAC 'Frontier_9550' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 
NG             <MAC 'NG' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --        no        
--             <MAC '--' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  14      &#9602;___  WPA2      no        

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

[[/etc/NetworkManager/system-connections/Frontier_9550 1]] (600 root)
[connection] id=Frontier_9550 1 | type=wifi | permissions=user:amandalmoen:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Frontier_9550
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BlackBerry Classic - Amanda]] (600 root)
[connection] id=BlackBerry Classic - Amanda | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=BlackBerry Classic - Amanda
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Frontier_9550]] (600 root)
[connection] id=Frontier_9550 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Frontier_9550
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp9s0    no frequency information.

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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

wlan0     Failed to read scan data : Resource temporarily unavailable

lo        Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 

[ssb]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[ 2802.494757] sky2 0000:09:00.0 enp9s0: Link is up at 100 Mbps, full duplex, flow control both
[ 2802.494801] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready
[ 3105.579750] sky2 0000:09:00.0 enp9s0: Link is down
[ 3476.477038] wlan0: authenticate with <MAC 'Frontier_9550' [AN1]>
[ 3476.580545] wlan0: send auth to <MAC 'Frontier_9550' [AN1]> (try 1/3)
[ 3476.784249] wlan0: send auth to <MAC 'Frontier_9550' [AN1]> (try 2/3)
[ 3476.787054] wlan0: authenticated
[ 3476.788587] wlan0: associate with <MAC 'Frontier_9550' [AN1]> (try 1/3)
[ 3476.792319] wlan0: RX AssocResp from <MAC 'Frontier_9550' [AN1]> (capab=0x411 status=0 aid=6)
[ 3476.792614] wlan0: associated
[ 3476.793542] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-09-14
You do have wireless internet connection that works now correct? Also you will have better connectivity if you change your wireless settings in network manager to match the screen shots.
Thanks

---

