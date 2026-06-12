---
title: "Lubuntu 15.10 Atheros AR2413/AR2414 Wireless disconected and dimmed out"
date: 2016-01-17
forum: Networking &amp; Wireless
---

### Post by roger60 on 2016-01-17
Acer Aspire 3500
Just fresh installed Lubuntu 15.10

Now I have to fix the wireless that is not working.
Using [http://ubuntuforums.org/showthread.php?t=2249263](http://ubuntuforums.org/showthread.php?t=2249263) I got the hardware switch turned back on by removing the battery.
But the wireless still does not work.

I have read a lot of forum posts regarding this kind of issue but nothing worked for me.
Please help.

```

########## wireless info START ##########

Report from: 17 Jan 2016 23:14 AEDT +1100

Booted last: 17 Jan 2016 00:00 AEDT +1100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:48:35 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
    Subsystem: Acer Incorporated [ALI] Device [1025:0082]
    Kernel driver in use: sis900

00:0b.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 139264  0
ath                    24576  1 ath5k
mac80211              659456  1 ath5k
cfg80211              483328  3 ath,ath5k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s4    Link encap:Ethernet  HWaddr <MAC 'enp0s4' [IF]>  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp0s4' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1272523 (1.2 MB)  TX bytes:155657 (155.6 KB)

wlp0s11   Link encap:Ethernet  HWaddr <MAC 'wlp0s11' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp0s4    no wireless extensions.

lo        no wireless extensions.

wlp0s11   IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp0s4
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s4

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       530     1  0 22:57 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s4
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Silicon Integrated Systems [SiS]
GENERAL.PRODUCT:                        SiS900 PCI Fast Ethernet
GENERAL.DRIVER:                         sis900
GENERAL.DRIVER-VERSION:                 v1.08.10 Apr. 2 2006
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
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       52132f73-7cb6-4acd-ac40-ea92f36d6628
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   52132f73-7cb6-4acd-ac40-ea92f36d6628 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.12/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1453118241
DHCP4.OPTION[9]:                        domain_name = Home
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.0.12
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp0s4' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp0s11
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
GENERAL.DRIVER:                         ath5k
GENERAL.DRIVER-VERSION:                 4.2.0-23-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp0s11' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0b.0/net/wlp0s11
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3c85fef2-3e8f-4d1e-bdba-b3aee1c73ce8 | OPTUS_E2DE45

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/OPTUS_E2DE45]] (600 root)
[connection] id=OPTUS_E2DE45 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp0s11' [IF]> | mac-address-blacklist= | ssid=OPTUS_E2DE45
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Australia/Sydney (based on set time zone)

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

enp0s4    no frequency information.

lo        no frequency information.

wlp0s11   13 channels in total; available frequencies :
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

##### iwlist scan #######################

enp0s4    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp0s11   No scan results

##### module infos ######################

[ath5k]
filename:       /lib/modules/4.2.0-23-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     771FA960E4882771F544E8B
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.2.0-23-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        75:24:D3:30:E7:EF:0D:0B:90:4A:C8:67:13:83:30:E3:A4:58:CB:F9
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/4.2.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-23-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        75:24:D3:30:E7:EF:0D:0B:90:4A:C8:67:13:83:30:E3:A4:58:CB:F9
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-23-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        75:24:D3:30:E7:EF:0D:0B:90:4A:C8:67:13:83:30:E3:A4:58:CB:F9
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-23-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-23-generic SMP mod_unload modversions 686 
signer:         Build time autogenerated kernel key
sig_key:        75:24:D3:30:E7:EF:0D:0B:90:4A:C8:67:13:83:30:E3:A4:58:CB:F9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   14.685483] ath5k 0000:00:0b.0: enabling device (0010 -> 0012)
[   14.685764] ath5k 0000:00:0b.0: registered as 'phy0'
[   15.441924] ath: EEPROM regdomain: 0x63
[   15.441932] ath: EEPROM indicates we should expect a direct regpair map
[   15.441937] ath: Country alpha2 being used: 00
[   15.441939] ath: Regpair used: 0x63
[   15.699298] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   15.813846] ath5k 0000:00:0b.0 wlp0s11: renamed from wlan0
[   29.074623] IPv6: ADDRCONF(NETDEV_UP): enp0s4: link is not ready
[   29.089397] IPv6: ADDRCONF(NETDEV_UP): wlp0s11: link is not ready (repeated 3 times)
[   30.072356] enp0s4: Media Link Off
[   35.090344] enp0s4: Media Link On 100mbps full-duplex

########## wireless info END ############


```

---

### Post by Hadaka on 2016-01-17
Hi, from a working wired connection please copy and paste..
```
sudo iw reg set AU
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
```
then do..
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rf ath5k
sudo modprobe -vv ath5k
```
remove wired connection and test wireless
Also Verify:
```

Click leftside launcher cogwheel/System Settings >>Network >> Wireless -  Airplane Mode/OFF - Wifi/ON
Click network icon..upper right..Enable Wireless/Checked
Check BIOS verify Wifi enabled
```

---

### Post by roger60 on 2016-01-17
```
rperrett@acer-Aspire-3500:~$ sudo iw reg set AU
[sudo] password for rperrett: 
rperrett@acer-Aspire-3500:~$ sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
rperrett@acer-Aspire-3500:~$ echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
options ath5k nohwcrypt=1
rperrett@acer-Aspire-3500:~$ sudo modprobe -rf ath5k
rperrett@acer-Aspire-3500:~$ sudo modprobe -vv ath5k
modprobe: INFO: ../libkmod/libkmod.c:356 kmod_set_log_fn() custom logging function 0x800cb1f0 registered
insmod /lib/modules/4.2.0-23-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.2.0-23-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.2.0-23-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/4.2.0-23-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1 
modprobe: INFO: ../libkmod/libkmod.c:323 kmod_unref() context 0x809b2100 released
rperrett@acer-Aspire-3500:~$ 

```

> remove wired connection and test wireless
Still not working

> Click leftside launcher cogwheel/System Settings >>Network >> Wireless -  Airplane Mode/OFF - Wifi/ON
Sorry I'm confused. I don't have a "launcher cogwheel". If you mean go to the Lubuntu menu, then I went to that.
"System Settings" - I don't have this either. I have "System Tools" so I clicked on that.
"Network" I have.
It gives me a dialog box called "Network Settings". It has three tabs called, "General", "DNS" and "Hosts".
"Wireless" I don't have - so I couldn't do anything regarding Airplane Mode (unless it is somewhere else that I don't know of).


> Click network icon..upper right..Enable Wireless/Checked
My network icon is on the bottom right in lubuntu. "Enable Wifi" is dimmed out.
"Enable Networking" is checked - but I have found that if I uncheck it then rfkill shows hardblocked as "No".

> Check BIOS verify Wifi enabled
I could not find a setting in the BIOS for Wifi.


I looked up the user manual for the Aspire 3500 and Acer says that there is a hardware button on the front which also shows a light.
This button does nothing if I press it. It shows an orange light.

---

### Post by Hadaka on 2016-01-17
Here is a link with some information on your soft and hard keys for wifi
[http://www.nmbgeek.com/blog/how-to-turn-laptop-wireless-on.html](http://www.nmbgeek.com/blog/how-to-turn-laptop-wireless-on.html)
hope this helps

---

### Post by roger60 on 2016-01-17
Thanks for that link. Looks quite useful.
> Aspire 3500 - Wifi switch is in the group of buttons to the left of the  power-on button. It's the third button from the left with the planet on  it. There is a wifi indicator under the trackpad, it’s the led with the  satellite on it.
For me, this button simply opens an LX terminal window.
After trying it however, my laptop now says
> Wi-Fi is disabled by hardware switch

Enable Wi-Fi" is grayed out.

---

### Post by roger60 on 2016-01-17
Turned off. Pulled out battery. Waited. Put back in. Turn on again.
"Enable Wi-Fi" is checked and not grayed out.
It no longer says that Wi-Fi is disabled by a hardware switch.

But WiFi still does not work.

---

