---
title: "No WIFI HW found after fresh install 19.04"
date: 2019-06-06
forum: Networking &amp; Wireless
---

### Post by mrmike-me on 2019-06-06
Background:
I installed 19.04 today. The system was 18.04 and everything worked  great. I am a [COLOR=#1A1A1B][FONT=&quot]glutton[/FONT][/COLOR] for punishment so I formatted the drive and  installed disco. Ever since the WIFI card is not found. Ubuntu is acting  like it is not installed. Again it worked perfect in 18.04 just a  couple hours ago.
Currently I am USB tethered to my Moto x4 as I am on a floor of my house with no Ethernet.

Hardware:
Lenovo Ideacenter Desktop w/ AMD® Ryzen 5 1400 quad-core processor × 8
Onboard WIFI

Commands run so far:
Turned off secure boot
```
sudo apt-get install --reinstall bcmwl-kernel-source

sudo apt update
sudo apt dist-upgrade
sudo apt install pastebinit
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Output:

```
########## wireless info START ##########

Report from: 06 Jun 2019 20:51 CDT -0500

Booted last: 06 Jun 2019 00:00 CDT -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

##### kernel ############################

Linux 5.0.0-16-generic #17-Ubuntu SMP Wed May 15 10:52:21 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3100]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 22b8:2e25 Motorola PCS 
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0461:4e8d Primax Electronics, Ltd 
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 008: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 1a2c:4324 China Resource Semico Co., Ltd 
Bus 001 Device 004: ID 2109:2817 VIA Labs, Inc. 
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

wmi_bmof               16384  0
wmi                    28672  1 wmi_bmof

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
2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
3: enp17s0f3u3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp17s0f3u3' [IF2]> brd <MAC address>
    inet 192.168.42.251/24 brd 192.168.42.255 scope global dynamic noprefixroute enp17s0f3u3
       valid_lft 3483sec preferred_lft 3483sec
    inet6 fe80::498d:b94f:3416:c4d1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp17s0f3u3  no wireless extensions.

enp1s0    no wireless extensions.

##### route #############################

default via 192.168.42.129 dev enp17s0f3u3 proto dhcp metric 100 
169.254.0.0/16 dev enp17s0f3u3 scope link metric 1000 
192.168.42.0/24 dev enp17s0f3u3 proto kernel scope link src 192.168.42.251 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       871     1  0 20:48 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp17s0f3u3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Motorola PCS
GENERAL.PRODUCT:                        moto x4
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp17s0f3u3' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.1/0000:11:00.3/usb1/1-3/1-3:1.0/net/enp17s0f3u3
GENERAL.IP-IFACE:                       enp17s0f3u3
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       a8b7ea6b-6dfb-36db-9723-1a86bf9fcaad
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.251/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[2]:                        dad_wait_time = 0
DHCP4.OPTION[3]:                        dhcp_lease_time = 3600
DHCP4.OPTION[4]:                        dhcp_message_type = 5
DHCP4.OPTION[5]:                        dhcp_rebinding_time = 3150
DHCP4.OPTION[6]:                        dhcp_renewal_time = 1800
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[9]:                        expiry = 1559875779
DHCP4.OPTION[10]:                       host_name = shea
DHCP4.OPTION[11]:                       ip_address = 192.168.42.251
DHCP4.OPTION[12]:                       network_number = 192.168.42.0
DHCP4.OPTION[13]:                       next_server = 192.168.42.129
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       requested_domain_search = 1
DHCP4.OPTION[18]:                       requested_host_name = 1
DHCP4.OPTION[19]:                       requested_interface_mtu = 1
DHCP4.OPTION[20]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_root_path = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_static_routes = 1
DHCP4.OPTION[28]:                       requested_subnet_mask = 1
DHCP4.OPTION[29]:                       requested_time_offset = 1
DHCP4.OPTION[30]:                       requested_wpad = 1
DHCP4.OPTION[31]:                       routers = 192.168.42.129
DHCP4.OPTION[32]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[33]:                       vendor_encapsulated_options = ANDROID_METERED
IP6.ADDRESS[1]:                         fe80::498d:b94f:3416:c4d1/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/3
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a8b7ea6b-6dfb-36db-9723-1a86bf9fcaad | Wired connection 2

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               3 (limited)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.1/0000:01:00.0/net/enp1s0
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
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp17s0f3u3  no frequency information.

enp1s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp17s0f3u3  Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[   19.349388] r8169 0000:01:00.0 enp1s0: Link is Down
[   79.730819] rndis_host 1-3:1.0 enp17s0f3u3: renamed from usb0

########## wireless info END ############


```

---

### Post by mrmike-me on 2019-06-07
More info: I found out the card in this machine is a RealTek 8821AE PCI-E

---

### Post by praseodym on 2019-06-08
Please check
```

dkms status
```

---

### Post by mrmike-me on 2019-06-08
> **praseodym said:**
> Please check
```

dkms status
```

No output.

---

### Post by jeremy31 on 2019-06-08
The simplest fix is the obvious one.  You could install Uubntu 18.04 alongside 19.04 and file a bug report at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) and see if it can be fixed in the 5.0 kernel in 19.04.  Another thing you could do is install the 5.0 kernel in 18.04 and see if you lose wifi.

You could go into UEFI/BIOS and reset to defaults and also check to see if WLAN is enabled in those settings, if I disable WLAN in the UEFI on my Lenovo, no OS can find it

---

### Post by aughey on 2019-06-10
Has the download a Rubbish Bin or does it say Trashcan. I accidently downloaded 19.04 which turned out to be a USA version (Trashcan). No matter what I tried I could not get my Wi fi working. I realised the error and downloaded a UK version instead. At the bit where it asks if you want to download 3rd party software I declined as I had previous problems with 19.04 dropping Wi Fi connections and this was the way to cure that issue. My laptop is dual boot with 50/50 Windows 10 pro on one half and 19.04 on the other. The Windows connection remained solid while the original 19.04 kept dropping.

---

