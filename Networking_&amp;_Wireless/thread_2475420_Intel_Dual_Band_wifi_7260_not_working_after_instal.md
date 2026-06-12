---
title: "Intel Dual Band wifi 7260 not working after install"
date: 2022-05-26
forum: Networking &amp; Wireless
---

### Post by mylo9000 on 2022-05-26
I've been scouring the web for an answer tho this issue, but nothing seems to help.

I downloaded a new iso for Ubuntu in a last ditch effort to get this working.

Back story. I have an Acer Aspire 7750z i inherited after my dad passed. In short order the stock wifi card stopped working so i purchased an Intel Dual Band wifi 7260 with Bluetooth 4 as a replacement. its what i could get in short order.
I've gone through several distros trying to see if this issue is limited to a specific kernel.

Seems the Wifi and Bluetooth work flawlessly in a live environment. but as soon as i install the OS and reboot, wifi is hard locked. but there isn't a physical switch on this laptop.
I was able to get it working at one point in POP_OS, not really sure how, but then the bluetooth stopped working.

I reinstalled Ubuntu and tried to replicate that which got the wifi working previously but no joy on that. (essentially downloaded the firmware file from intel and blacklisted the asus_iwm module)

I can't seem to figure out how to get this wifi card to work, its functions perfectly, both wifi and bluetooth when booted into a live usb and in a windows PE live environment so i know the card is good.

I've done a fresh install of Ubuntu to try and get this going again, and hope that someone has a solution that i may have missed.

I'm so tired of this frustration so i really hope i can get a solution.

Here is the out put of a wifi-info script i found while troubleshooting.

```

########## wireless info START ##########

Report from: 25 May 2022 20:47 EDT -0400

Booted last: 25 May 2022 00:00 EDT -0400

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy

##### kernel ############################

Linux 5.15.0-33-generic #34-Ubuntu SMP Wed May 18 13:34:26 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Acer Incorporated [ALI] AR8151 v2.0 Gigabit Ethernet [1025:050e]
	Kernel driver in use: atl1c

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
Bus 001 Device 004: ID 058f:b002 Alcor Micro Corp. Acer Integrated Webcam
Bus 001 Device 003: ID 8087:07dc Intel Corp. Bluetooth wireless interface
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

##### secure boot #######################

EFI variables are not supported on this system

##### lsmod #############################

iwlmvm                561152  0
mac80211             1228800  1 iwlmvm
libarc4                16384  1 mac80211
acer_wmi               28672  0
wmi_bmof               16384  0
sparse_keymap          16384  1 acer_wmi
iwlwifi               446464  1 iwlmvm
cfg80211              958464  3 iwlmvm,iwlwifi,mac80211
wmi                    32768  2 acer_wmi,wmi_bmof
video                  53248  2 acer_wmi,i915

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.2.32/24 brd 192.168.2.255 scope global dynamic noprefixroute enp2s0
       valid_lft 257951sec preferred_lft 257951sec
    inet6 fe80::7cf2:67:6562:d345/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp3s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.2.1 dev enp2s0 proto dhcp metric 100 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.2.0/24 dev enp2s0 proto kernel scope link src 192.168.2.32 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search home

##### network managers ##################

Installed:

	NetworkManager

Running:

root         590       1  0 20:26 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8151 v2.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 5.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
GENERAL.PATH:                           pci-0000:02:00.0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       9ea81368-cafd-3b3a-9eb5-2bcff2dc42fe
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.2.32/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 192.168.2.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 0.0.0.0/0, nh = 192.168.2.1, mt = 100
IP4.DNS[1]:                             192.168.2.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        broadcast_address = 192.168.2.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 259200
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.2.1
DHCP4.OPTION[4]:                        domain_name = home
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.2.1
DHCP4.OPTION[6]:                        expiry = 1653784021
DHCP4.OPTION[7]:                        ip_address = 192.168.2.32
DHCP4.OPTION[8]:                        requested_broadcast_address = 1
DHCP4.OPTION[9]:                        requested_domain_name = 1
DHCP4.OPTION[10]:                       requested_domain_name_servers = 1
DHCP4.OPTION[11]:                       requested_domain_search = 1
DHCP4.OPTION[12]:                       requested_host_name = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[15]:                       requested_nis_domain = 1
DHCP4.OPTION[16]:                       requested_nis_servers = 1
DHCP4.OPTION[17]:                       requested_ntp_servers = 1
DHCP4.OPTION[18]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[19]:                       requested_root_path = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       requested_static_routes = 1
DHCP4.OPTION[22]:                       requested_subnet_mask = 1
DHCP4.OPTION[23]:                       requested_time_offset = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       routers = 192.168.2.1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::7cf2:67:6562:d345/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9ea81368-cafd-3b3a-9eb5-2bcff2dc42fe | Wired connection 1

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 5.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               17.3216344376.0 7260-17.ucode
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.PATH:                           pci-0000:03:00.0
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
INTERFACE-FLAGS.UP:                     no
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               yes
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com./

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/DasBase.nmconnection]] (600 root)
[connection] id=DasBase | type=wifi
[wifi] ssid=DasBase
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

wlp3s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/5.15.0-33-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
description:    The new Intel(R) wireless AGN driver for Linux
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       5.15.0-33-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/5.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.15.0-33-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/5.15.0-33-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
description:    Intel(R) Wireless WiFi driver for Linux
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.15.0-33-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for AX210 devices, 4K for other devices 1:4K 2:8K 3:12K (16K buffers) 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: true (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/5.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.15.0-33-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
amsdu_size: 0
bt_coex_active: Y
disable_11ac: N
disable_11ax: N
enable_ini: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3

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

[    7.347749] iwlwifi 0000:03:00.0: loaded firmware version 17.3216344376.0 7260-17.ucode op_mode iwlmvm
[    7.435429] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    7.443724] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    7.450030] iwlwifi 0000:03:00.0: reporting RF_KILL (radio disabled)
[    7.450058] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[    7.462629] iwlwifi 0000:03:00.0: base HW address: <MAC 'wlp3s0' [IF2]>
[    7.480822] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    7.839291] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   10.641820] atl1c 0000:02:00.0: atl1c: enp2s0 NIC Link is Up<1000 Mbps Full Duplex>

########## wireless info END ############

```

---

### Post by Yellow Pasque on 2022-05-26
Try pressing the Fn + F3 keys together. It looks like that serves as the wireless switch on that laptop.

---

### Post by mylo9000 on 2022-05-26
That option just toggles airplane mode.
when i turn off airplane mode, the wifi shows as Hardware disabled and unavailable.

its crazy that when i boot into a live usb, it works with out issue. but after install wifi is hard locked.

---

### Post by Yellow Pasque on 2022-05-26
Other than playing around with rfkill, I don't know what to tell you. Hopefully, someone more knowledgeable will know what the issue is..

---

### Post by #&amp;thj^% on 2022-05-26
This should of been fixed in newer kernels, but you could try this old workaround:
```
sudo tee /etc/modprobe.d/blacklist-acer.conf <<< "blacklist acer_wmi"
```
Reboot
If still a no go, post this, or look at:
```
sudo dmesg | grep iwl

```

---

### Post by mylo9000 on 2022-05-26
ok, so blacklisting the acer_wmi module seems to have allowed the wifi to work again but, as it has before, blocked bluetooth.
The bluetooth isn't even detected on the system any more.

There is something about the acer_wmi module that kills bluetooth when its blacklisted.

here is the new output from dmesg as requested:
```
[    5.585473] iwlwifi 0000:03:00.0: loaded firmware version 17.3216344376.0 7260-17.ucode op_mode iwlmvm
[    5.689341] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.695695] iwlwifi 0000:03:00.0: reporting RF_KILL (radio disabled)
[    5.695724] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[    5.709710] iwlwifi 0000:03:00.0: base HW address: 48:51:b7:16:f2:33
[    5.728332] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.954286] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[  985.903070] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  985.903076] iwlwifi 0000:03:00.0: reporting RF_KILL (radio enabled)
[  986.791028] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  986.791035] iwlwifi 0000:03:00.0: reporting RF_KILL (radio disabled)
[  986.828420] WARNING: CPU: 1 PID: 3588 at drivers/net/wireless/intel/iwlwifi/pcie/trans.c:2054 __iwl_trans_pcie_grab_nic_access.part.0+0x1f8/0x230 [iwlwifi]
[  986.828453] Modules linked in: snd_hda_codec_hdmi nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core snd_hwdep intel_rapl_msr mei_hdcp snd_pcm uvcvideo snd_seq_midi videobuf2_vmalloc intel_rapl_common snd_seq_midi_event videobuf2_memops x86_pkg_temp_thermal intel_powerclamp coretemp snd_rawmidi videobuf2_v4l2 crct10dif_pclmul videobuf2_common snd_seq ghash_clmulni_intel cryptd videodev iwlmvm rapl mac80211 intel_cstate libarc4 i915 mc snd_seq_device input_leds iwlwifi snd_timer serio_raw ttm drm_kms_helper cfg80211 cec at24 rc_core i2c_algo_bit fb_sys_fops syscopyarea sysfillrect snd sysimgblt mei_me mei soundcore wmi_bmof joydev mac_hid sch_fq_codel ipmi_devintf ipmi_msghandler msr parport_pc ppdev lp parport drm ip_tables x_tables autofs4 ums_realtek uas usb_storage crc32_pclmul ahci libahci i2c_i801 psmouse i2c_smbus lpc_ich atl1c video wmi
[  986.828581] RIP: 0010:__iwl_trans_pcie_grab_nic_access.part.0+0x1f8/0x230 [iwlwifi]
[  986.828635]  iwl_trans_pcie_grab_nic_access+0x45/0x80 [iwlwifi]
[  986.828657]  iwl_set_bits_prph+0x25/0x60 [iwlwifi]
[  986.828675]  iwl_fw_dbg_stop_restart_recording.part.0+0x253/0x270 [iwlwifi]
[  986.828703]  iwl_fw_dbg_stop_sync+0x46/0x50 [iwlwifi]
[  986.828728]  iwl_mvm_stop_device+0x3b/0x80 [iwlmvm]
[  986.828749]  __iwl_mvm_mac_stop+0x69/0x170 [iwlmvm]
[  986.828767]  iwl_mvm_mac_stop+0x77/0x90 [iwlmvm]
[  986.829128] iwlwifi 0000:03:00.0: iwlwifi transaction failed, dumping registers
[  986.829133] iwlwifi 0000:03:00.0: iwlwifi device config registers:
[  986.829910] iwlwifi 0000:03:00.0: 00000000: 08b18086 00100406 02800073 00000010 c0400004 00000000 00000000 00000000
[  986.829915] iwlwifi 0000:03:00.0: 00000020: 00000000 00000000 00000000 44708086 00000000 000000c8 00000000 00000107
[  986.829919] iwlwifi 0000:03:00.0: 00000040: 00020010 10008ec0 00190c10 0006ec11 10110142 00000000 00000000 00000000
[  986.829922] iwlwifi 0000:03:00.0: 00000060: 00000000 00080812 00000005 00000000 00010001 00000000 00000000 00000000
[  986.829925] iwlwifi 0000:03:00.0: 00000080: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.829928] iwlwifi 0000:03:00.0: 000000a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.829931] iwlwifi 0000:03:00.0: 000000c0: 00000000 00000000 c823d001 0d000000 00814005 fee02004 00000000 00000026
[  986.829934] iwlwifi 0000:03:00.0: 000000e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.829937] iwlwifi 0000:03:00.0: 00000100: 14010001 00000000 00000000 00462031 00002000 00002000 00000000 00000000
[  986.829940] iwlwifi 0000:03:00.0: 00000120: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.829943] iwlwifi 0000:03:00.0: 00000140: 14c10003 ff16f233 4851b7ff 15410018 00000000 0001000b 0141cafe 00f01e1f
[  986.829945] iwlwifi 0000:03:00.0: iwlwifi device memory mapped registers:
[  986.830010] iwlwifi 0000:03:00.0: 00000000: 40000000 80000000 00000080 00000000 00000000 00000000 00000000 00000000
[  986.830013] iwlwifi 0000:03:00.0: 00000020: 00000001 000403d8 00000144 00000000 80000000 803a0000 80008040 00080042
[  986.830028] iwlwifi 0000:03:00.0: iwlwifi device AER capability structure:
[  986.830071] iwlwifi 0000:03:00.0: 00000000: 14010001 00000000 00000000 00462031 00002000 00002000 00000000 00000000
[  986.830073] iwlwifi 0000:03:00.0: 00000020: 00000000 00000000 00000000
[  986.830076] iwlwifi 0000:03:00.0: iwlwifi parent port (0000:00:1c.1) config registers:
[  986.830323] iwlwifi 0000:00:1c.1: 00000000: 1c128086 00100007 060400b4 00810010 00000000 00000000 00030300 200000f0
[  986.830327] iwlwifi 0000:00:1c.1: 00000020: c040c040 0001fff1 00000000 00000000 00000000 00000040 00000000 000202ff
[  986.830330] iwlwifi 0000:00:1c.1: 00000040: 01428010 00008000 00100000 02123c12 70110042 000cb200 01400000 00000000
[  986.830333] iwlwifi 0000:00:1c.1: 00000060: 00000000 00000016 00000000 00000000 00010002 00000000 00000000 00000000
[  986.830336] iwlwifi 0000:00:1c.1: 00000080: 00009005 00000000 00000000 00000000 0000a00d 050e1025 00000000 00000000
[  986.830339] iwlwifi 0000:00:1c.1: 000000a0: c8020001 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830342] iwlwifi 0000:00:1c.1: 000000c0: 00000000 00000000 00000000 00000000 01000000 00000b02 81118000 00000000
[  986.830346] iwlwifi 0000:00:1c.1: 000000e0: 00000300 00000000 00000001 00000000 00000000 00000000 08050f87 00000000
[  986.830349] iwlwifi 0000:00:1c.1: 00000100: 00000000 00000000 00000000 00060011 00000000 00002000 00000000 00000000
[  986.830352] iwlwifi 0000:00:1c.1: 00000120: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830355] iwlwifi 0000:00:1c.1: 00000140: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830358] iwlwifi 0000:00:1c.1: 00000160: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830361] iwlwifi 0000:00:1c.1: 00000180: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830364] iwlwifi 0000:00:1c.1: 000001a0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830366] iwlwifi 0000:00:1c.1: 000001c0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830369] iwlwifi 0000:00:1c.1: 000001e0: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[  986.830372] iwlwifi 0000:00:1c.1: 00000200: 00000000 00000000 00000000
[  987.683032] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  987.683039] iwlwifi 0000:03:00.0: reporting RF_KILL (radio enabled)

```

---

### Post by #&amp;thj^% on 2022-05-26
This should be filed as bug again. :)
Seems they are pushing out undercooked kernels again. ;(
will the bluetooth set to On with rfkill?
BTW if you are kind enough to file that bug, include:
```
sudo dmidecode | grep -E "(Manufacturer|Product)"

```
just for good measure.

---

### Post by mylo9000 on 2022-05-26
no, unfortunately. 

The device ceased to exist. so there's nothing to rfkill. :|

---

### Post by #&amp;thj^% on 2022-05-26
my bad, I did see that in your post.

---

### Post by mylo9000 on 2022-05-26
no worries, it happens to us all.

---

### Post by #&amp;thj^% on 2022-05-26
> **mylo9000 said:**
> no worries, it happens to us all.

;)
Just talked with kernel guy, seems they don't have access to your hardware anymore.
you may have to help them with some leg work.
Good Luck

---

### Post by mylo9000 on 2022-05-27
I'm not sure how i can help.

I think i'm going to have to find a more Linux compatible wifi card that works in this laptop.

Either way, i got some work to do.

---

### Post by #&amp;thj^% on 2022-05-27
> **mylo9000 said:**
> I'm not sure how i can help.


They will guide you after they review the Bug report, it's a little time consuming for sure, and they may ask you to implement some patch's.
> **mylo9000 said:**
> 
I think i'm going to have to find a more Linux compatible wifi card that works in this laptop.

Either way, i got some work to do.
Makes perfect sense, but the problem will remain for your factory WiFi adapter.
I've learned in over a decade of testing>> the squeaky wheel dose get greased, more often than not. ;)
I tend to steer clear of most of the newer RealTek's, FWIW Intel makes some nice WiFi Dongles.
Good Luck

---

### Post by mylo9000 on 2022-05-27
thanks, i appreciate your feedback.

---

