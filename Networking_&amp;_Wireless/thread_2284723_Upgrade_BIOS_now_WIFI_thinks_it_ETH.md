---
title: "Upgrade BIOS now WIFI thinks it ETH"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by l6griffin on 2015-07-01
I have a HP2000 laptop that I update the BIOS on a few days ago. Now  when I boot up it says it has an Ethernet connection not possible no cable and is intermittent.  When I go into system settings - Network wireless is turned off and  won't turn on. There are two wired connection one with a disconnect  cable and the other with the IP addresses and the WIFI is working. How  do I clean this up delete config files, re-install WIFI?

I've upgrade from 14.04 LTS to 14.10 no help.

Here is the output from the;


```
##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
rt2800pci              13630  0 
rt2800mmio             20938  1 rt2800pci
rt2800lib              93180  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55170  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              660651  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              510218  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
wmi                    19193  1 hp_wmi

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

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7021:d7ff:fee0:8ab7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:69081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49211916 (49.2 MB)  TX bytes:13976798 (13.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 usb0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       862     1  0 18:44 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: usb0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

no-auto-default=<MAC 'eth0' [IF]>,<MAC 'usb0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=larry-HP-2000 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

usb0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     E643C8F6A545F357EEB41AF
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     4F1D9212CBFF4F4BE09171A
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     EDDCA794C9E4C3981037918
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     7856EF56F97508465F566A2
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     37A76810C0FE9E4E11476DA
depends:        rt2x00lib
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     71EFA3CA86D02D0528C49EE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:EF:C3:C3:2E:24:9C:CF:A9:2C:E6:65:30:46:B5:36:8C:8A:5B:0B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

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

loop
lp

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.1/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############
```

---

### Post by oldfred on 2015-07-01
Please use code tags on long text or terminal output.

And BIOS update, resets all BIOS settings to defaults. You may want to review your BIOS settings.
New UEFI systems save some settings, but not all.

Do you have a BIOS setting or keyboard setting to control Wireless. My very old laptop had a physical switch. Newer systems seem to have keyboard f-key setting.

---

### Post by l6griffin on 2015-07-01
Code tags (?) i.e. tinyurl?

There was an option at the end of the script, didn't understand what it was for, first time I've run the script.

I doubled checked the BIOS no sign that is UEFI. The was a setting under Boot Options to enable networking(?) on boot changed that no help. I do have a switch on the keyboard for WIFI but it is always orange can't change it.

---

### Post by oldfred on 2015-07-01
Code tags
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)

I do not know wireless issues. But it looks like it is using a USB connection for Internet? Is that correct?

---

### Post by l6griffin on 2015-07-01
I've always used WIFI hotspot for internet. I'm in a motorhome and have no land line.

---

