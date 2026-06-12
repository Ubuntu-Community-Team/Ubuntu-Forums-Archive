---
title: "Activation of network connection failed on Ubuntu 18.04 LTS on HP Pavillon 14 n007la"
date: 2019-06-20
forum: Networking &amp; Wireless
---

### Post by no-cheating on 2019-06-20
2 days ago I installed Ubuntu 18.04 LTS on HP Pavilion 14 n007la and things were working fine, until yesterday night WiFi internet suddenly stopped working (it had been working fine until that moment).

First I lost the connection to my WiFi network. Now every time I try to connect after a minute an error "Activation of network connection failed" is displayed.

The problem is not with this particular WiFi network nor router device, as I tried connecting to 3 different WiFi networks on 3 different devices and got the same error for each one of them

[LIST]
[*] It's also not related to OS configuration, as I tried running fresh copy of Ubuntu 18.04 LTS live from USB and am getting the same errors
[*] Other devices (e.g. my phone) connect to the same WiFi networks without problems
[/LIST]

That makes me think the problem is on hardware level, not OS level.

From system logs I can see that the failure happens at DHCP, with DHCP requests being timed out.

[https://i.imgur.com/OepWIjE.jpg](https://i.imgur.com/OepWIjE.jpg)

The network controller driver in use is rt2800pci:

[https://i.imgur.com/6ZlmBry.jpg](https://i.imgur.com/6ZlmBry.jpg)

Sorry the code is an image and not text, but now I have only internet access on my phone and that's the only way I can capture it.

I've read many other similar questions but none of the solutions posted there worked for me.

What can I do?

---

### Post by garvinrick4 on 2019-06-20
#Give this a try
Run this all should say true. If not run next three
> gedit /var/lib/NetworkManager/NetworkManager.state
> sudo service network-manager stop 
> sudo rm /var/lib/NetworkManager/NetworkManager.state
> sudo service network-manager start

---

### Post by no-cheating on 2019-06-20
> **garvinrick4 said:**
> Run this all should say true. If not run next three

They are all true:

[https://i.imgur.com/16RjKnt.jpg](https://i.imgur.com/16RjKnt.jpg)

---

### Post by garvinrick4 on 2019-06-20
does this have your internet service provider on bottom
> gedit /etc/resolv.conf

---

### Post by no-cheating on 2019-06-20
> **garvinrick4 said:**
> does this have your internet service provider on bottom

It has this:

```
nameserver 127.0.0.53
options edns0
```

---

### Post by garvinrick4 on 2019-06-20
Last post should have internet service provider in a third line.
nameserver 127.0.0.53
options edns0
search hsd1.ca.comcast.net

See if all say no
> rfkill list

---

### Post by no-cheating on 2019-06-20
> **garvinrick4 said:**
> Last post should have internet service provider in a third line.
nameserver 127.0.0.53
options edns0
search hsd1.ca.comcast.net

See if all say no
Do you mean I should add "search hsd1.ca.comcast.netx&#8221; as third line?

```
$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked no
```

---

### Post by garvinrick4 on 2019-06-20
No was showing you my /etc/resolv.conf file, sorry should have stated

Going to give you user who knows more about curing your problem
Rubi1200
Will see if I can get him to look at this thread

---

### Post by no-cheating on 2019-06-20
> **garvinrick4 said:**
> No was showing you my /etc/resolv.conf file, sorry should have stated

Going to give you user who knows more about curing your problem
Rubi1200
Will see if I can get him to look at this thread

I understand. Thanks for your help. I hope he will look.

---

### Post by garvinrick4 on 2019-06-20
Left Rubi1200 a message he will get back to you he is part of staff

---

### Post by no-cheating on 2019-06-20
> **garvinrick4 said:**
> Left Rubi1200 a message he will get back to you he is part of staff

I've already sent him a message. So it seems now I just have to wait.

---

### Post by Rubi1200 on 2019-06-20
Hi,

No longer staff, retired :-)

Not an expert with networking but will try and help if I can.

Let's start with the wireless info script please:
[https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)

Thanks.

---

### Post by no-cheating on 2019-06-21
> **Rubi1200 said:**
> Hi,

No longer staff, retired :-)

Not an expert with networking but will try and help if I can.

Let's start with the wireless info script please:
[https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)

Thanks.

Wasn't easy to download files from GitHub to a laptop without internet, but some copy pasting from GitHub raw files to files on my phone, then transferring those files from my phone to laptop via USB and I've done it :).

Here are the results:


```

########## wireless info START ##########

Report from: 20 Jun 2019 23:00 CDT -0500

Booted last: 20 Jun 2019 00:00 CDT -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.18.0-22-generic #23~18.04.1-Ubuntu SMP Thu Jun 6 08:37:25 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
	Kernel driver in use: rt2800pci

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:216d]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 18d1:4ee2 Google Inc. Nexus 4 (debug)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
mac80211              802816  3 rt2x00pci,rt2x00lib,rt2800lib
cfg80211              667648  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    24576  2 hp_wmi,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
3: wlo1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlo1' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

	NetworkManager

Running:

root      4182     1  0 20:42 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.18.0-22-generic
GENERAL.FIRMWARE-VERSION:               0.37
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0/net/wlo1
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1cb93872-5e83-4973-8d73-853b4658c9dd | Koshi's Internet

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:05:00.0/net/eno1
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID              BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Koshi's Internet  <MAC 'Koshi's Internet' [AN1]>  Infra  2     2417 MHz  130 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
IZZI-24B3         <MAC 'IZZI-24B3' [AN2]>  Infra  6     2437 MHz  405 Mbit/s  24      &#9602;___  WPA2       no             

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Koshi's Internet]] (600 root)
[connection] id=Koshi's Internet | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=Koshi's Internet
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/robert-phone]] (600 root)
[connection] id=robert-phone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=robert-phone
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone]] (600 root)
[connection] id=iPhone | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=iPhone
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Mexico_City (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eno1      no frequency information.

wlo1      14 channels in total; available frequencies :
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

wlo1      Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.18.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     99E7C626D61A874D884E3A2
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.18.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BB8B8955B8B201DFEB6191F
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2800lib]
filename:       /lib/modules/4.18.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     966CF51FCABF548A597F127
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00pci]
filename:       /lib/modules/4.18.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C5A0354349252C4888D0842
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00mmio]
filename:       /lib/modules/4.18.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4E56E599A263E22755195FD
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00lib]
filename:       /lib/modules/4.18.0-22-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9726B139222EDB02105054
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.18.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.18.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     9388DCE7F64620803B0EC6E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[39007.022680] r8169 0000:05:00.0 eno1: link down
[39009.980262] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[39010.185722] r8169 0000:05:00.0 eno1: link down
[39010.185889] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[39010.188840] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 3 times)

########## wireless info END ############
```

---

### Post by Rubi1200 on 2019-06-21
Thanks for posting the script.

Have you tried booting an older kernel and trying connecting to wireless from there?

Your current kernel is 4.18.0-22.

I would give it a try via advanced options at GRUB startup and let's see what happens.

---

### Post by wildmanne39 on 2019-06-21
Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Thanks

---

### Post by no-cheating on 2019-06-21
> **Rubi1200 said:**
> Thanks for posting the script.

Have you tried booting an older kernel and trying connecting to wireless from there?

Your current kernel is 4.18.0-22.

I would give it a try via advanced options at GRUB startup and let's see what happens.

I hadn't tried booting other kernels before, but now I've given it a try. I booted 4.18.0-15-generic, while normally I was using 4.18.0-22-generic. Unfortunately the issue is present on the older kernel also - I cannot connect to WiFi network.

Also note that the issue didn't start to appear after a kernel upgrade. WiFi was working fine for 2 days and then suddenly, in the middle of using the system (not after a restart), it stopped.

---

### Post by no-cheating on 2019-06-21
> **wildmanne39 said:**
> Please use the attachment facility by clicking on the paperclip or use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Thanks

Okay, will do that if I ever again need to capture the screen. I just thought this is important content and had no other way to present it than as an image. But I'll stick to attachments from now on.

---

### Post by wildmanne39 on 2019-06-21
There are a few things I see that need adjusting, I am about to get off for the night so just a couple real quick, please do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
then:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot, does it connect now?

---

### Post by no-cheating on 2019-06-21
> **wildmanne39 said:**
> There are a few things I see that need adjusting, I am about to get off for the night so just a couple real quick, please do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
then:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot, does it connect now?

It fixed it! Thanks a lot. I've been struggling without internet access for a day and finally you've fixed it :). Or actually all 3 of you guys who helped me here, getting to the solution step by step.

Can you describe me what was the problem, so that I understand what happened? Especially that it stopped working suddenly, after working for 2 days.

---

### Post by Rubi1200 on 2019-06-21
Big thanks owed to wildmanne39 for jumping in and helping sort this out, kudos.

---

### Post by no-cheating on 2019-06-21
> **Rubi1200 said:**
> Big thanks owed to wildmanne39 for jumping in and helping sort this out, kudos.

Thabks to all 3 of you: garvinrick4, Rubi1200 and wildmanne39. I guess it was kind of a team work ;).

---

### Post by wildmanne39 on 2019-06-21
> **no-cheating said:**
> It fixed it! Thanks a lot. I've been struggling without internet access for a day and finally you've fixed it :).

Can you describe me what was the problem, so that I understand what happened? Especially that it stopped working suddenly, after working for 2 days.
This device has trouble using hardware for encryption and the first command switched encryption to software, the second command turned power management off, when it is on all wifi devices have issues, sometime they will connect but not well and sometimes not at all.

You are very welcome, I do not have the time to help out much with wifi issues anymore and I am rusty so it helped me as well.

Enjoy!

---

### Post by no-cheating on 2019-06-21
> **wildmanne39 said:**
> This device has trouble using hardware for encryption and the first command switched encryption to software, the second command turned power management off, when it is on all wifi devices have issues, sometime they will connect but not well and sometimes not at all.

You are very welcome, I do not have the time to help out much with wifi issues anymore and I am rusty so it helped me as well.

Enjoy!

Thanks for the explanation. Makes it much clearer now. Have a good night!

---

### Post by garvinrick4 on 2019-06-21
Any new user who needs help notice it was solved because "no-cheating" gave info asked for and
his problem was then solved by a user with knowledge on topic. Good example of how forum
should be used.

---

### Post by no-cheating on 2019-06-21
> **garvinrick4 said:**
> No cheating tell us what solved your networking problem so users know. Thank you.

I think it was clear from the messages in the thread, which one solved it, but I can clarify it again, no problem. This is the solution:

> **wildmanne39 said:**
> ```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
then:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Reboot

And this is the explanation:

> **wildmanne39 said:**
> This device has trouble using hardware for  encryption and the first command switched encryption to software, the  second command turned power management off, when it is on all wifi  devices have issues, sometime they will connect but not well and  sometimes not at all.
Enjoy!

---

