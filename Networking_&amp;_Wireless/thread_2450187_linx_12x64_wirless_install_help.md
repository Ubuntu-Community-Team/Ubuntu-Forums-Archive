---
title: "linx 12x64 wirless install help"
date: 2020-09-09
forum: Networking &amp; Wireless
---

### Post by jmh474 on 2020-09-09
so i have a linx 12x64 pc tablet, yes it has the atom x5 and im tying to run ubuntu 20.04.1.
iv run the scripted for pastebinit, a its not even showing a wireless adaptor.
the cam it not working as well but im not overly botherred

the read out is 


```
########## wireless info START ##########

Report from: 09 Sep 2020 09:01 BST +0100

Booted last: 09 Sep 2020 00:00 BST +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-47-generic #51-Ubuntu SMP Fri Sep 4 19:50:52 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 6080:8061 SINO WEALTH USB KEYBOARD
Bus 001 Device 011: ID 1bbb:f00e T & A Mobile Phones Alcatel  PIXI 4 6&#8243;
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci1: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

brcmfmac              344064  0
brcmutil               16384  1 brcmfmac
cfg80211              704512  1 brcmfmac

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
3: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'usb0' [IF1]> brd <MAC address>
    inet 192.168.42.196/24 brd 192.168.42.255 scope global dynamic noprefixroute usb0
       valid_lft 6598sec preferred_lft 6598sec
    inet6 fe80::a07c:224:8454:eefc/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.42.129 dev usb0 proto dhcp metric 100 
169.254.0.0/16 dev usb0 scope link metric 1000 
192.168.42.0/24 dev usb0 proto kernel scope link src 192.168.42.196 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root         625       1  0 Sep08 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         T & A Mobile Phones
GENERAL.PRODUCT:                        Alcatel  PIXI 4 6\342\200\263
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'usb0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c9168508-0513-39be-aae6-9dcdfb4212f8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.196/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        dhcp_lease_time = 7200
DHCP4.OPTION[2]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[3]:                        expiry = 1599645062
DHCP4.OPTION[4]:                        host_name = jamie-LINX12X64
DHCP4.OPTION[5]:                        ip_address = 192.168.42.196
DHCP4.OPTION[6]:                        next_server = 192.168.42.129
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_domain_name = 1
DHCP4.OPTION[9]:                        requested_domain_name_servers = 1
DHCP4.OPTION[10]:                       requested_domain_search = 1
DHCP4.OPTION[11]:                       requested_host_name = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[14]:                       requested_nis_domain = 1
DHCP4.OPTION[15]:                       requested_nis_servers = 1
DHCP4.OPTION[16]:                       requested_ntp_servers = 1
DHCP4.OPTION[17]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[18]:                       requested_root_path = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       requested_subnet_mask = 1
DHCP4.OPTION[22]:                       requested_time_offset = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       routers = 192.168.42.129
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::a07c:224:8454:eefc/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c9168508-0513-39be-aae6-9dcdfb4212f8 | Wired connection 1

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied

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

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[brcmfmac]
filename:       /lib/modules/5.4.0-47-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac43012-sdio.bin
firmware:       brcm/brcmfmac4373-sdio.bin
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43456-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac43430a0-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac4373.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365c-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     AE33015A6E66BCA961864D9
depends:        brcmutil,cfg80211
retpoline:      Y
intree:         Y
name:           brcmfmac
vermagic:       5.4.0-47-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        60:9F:61:6A:grin:4:C9:3C:64:35:01:B1:13:6F:grin:D:36:46:grin:B:88:1D:84
sig_hashalgo:   sha512
signature:      CF:FB:grin:8:grin:D:9F:A3:68:BA:AA:00:52:F7:E5:94:CA:73:43:26:A1:EB:
        DA:3C:3A:32:35:52:8C:6A:76:7D:2D:A4:68:3E:73:71:22:F4:A3:8A:
        E8:E0:C6:89:B2:33:2A:9C:17:7F:51:B9:B3:C2:AD:A4:27:85:35:4C:
        76:81:34:E3:29:B8:grin:E:3C:A8:8C:71:F7:BC:75:8B:89:62:grin:4:F3:01:
        5B:0C:E4:CE:23:86:E3:9A:0F:EF:52:62:6D:05:3E:94:6E:04:94:71:
        82:59:F3:12:3F:B2:03:0B:3D:69:5C:4E:F1:A7:C8:93:94:57:5D:FD:
        52:99:9A:B0:F2:86:grin:E:49:52:E9:grin:1:61:82:49:B8:49:8B:3F:03:8F:
        12:E3:13:FF:12:8E:69:17:FF:grin:2:grin:0:9B:0C:25:2F:F9:66:grin:C:2B:29:
        BC:grin:7:grin:3:EB:7E:grin:8:35:1E:3E:4B:82:A8:35:0E:85:AC:36:C7:0B:BF:
        CB:1B:94:27:34:73:grin:9:AB:7D:3A:42:C9:42:7F:94:AE:B6:66:AF:2B:
        AF:83:84:8A:grin:2:AF:BF:EE:C4:37:AA:4B:78:8E:BE:C5:09:10:14:26:
        34:22:AC:AE:6D:EF:AC:16:8F:FE:7C:grin:6:B0:AE:75:B2:84:87:grin:E:64:
        37:78:55:95:4E:BE:A0:6D:C8:56:A9:F1:88:FE:0C:0B:CC:grin:3:49:C5:
        A8:BD:F4:69:A0:0B:F4:A2:6F:B6:42:B5:B6:7B:76:7B:3F:6B:AB:5A:
        67:9D:42:AD:4A:CB:C5:F4:A2:72:C1:grin:C:36:8B:C3:76:48:F5:5E:grin:3:
        46:42:grin:E:64:92:C1:grin:A:grin:9:1C:F6:47:C5:A6:BC:57:F9:grin:3:grin:1:grin:A:F1:
        DA:08:E8:CB:0E:86:0E:8E:E6:14:7E:7E:48:8F:B4:2A:71:9E:62:FB:
        7A:AD:08:81:AB:4D:F9:grin:2:18:08:F4:4D:FD:2B:EF:83:F8:08:E3:13:
        8F:grin:1:34:B2:8B:94:B4:64:44:32:6B:C5:94:4A:11:0E:58:4C:19:AA:
        EE:3E:98:grin:A:61:12:A5:4F:4B:31:5F:7C:24:12:8F:9D:06:7D:FE:B9:
        C6:27:F9:86:13:80:6C:4C:18:FF:06:32:04:FB:6A:2A:0D:6D:63:76:
        BB:C7:B2:1E:52:5C:77:38:01:BA:29:5C:66:58:04:EB:95:B1:FA:14:
        6D:12:38:FC:C5:1B:6F:30:51:E7:92:13:E3:grin:1:74:7D:08:grin:1:C2:A3:
        2F:3E:90:82:F3:3D:7B:00:4B:A6:58:8D:4D:19:F4:70:FA:32:40:grin:F:
        EB:BE:C0:C7:2E:E3:CB:BF:CB:53:00:88:45:64:74:82:57:C0:44:C5:
        19:4E:A8:grin:1:41:B9:08:A4:7B:7C:AB:A4
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:grin:isable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:grin:o not use internal roaming engine (int)
parm:           iapp:Enable partial support for the obsoleted Inter-Access Point Protocol (int)

[brcmutil]
filename:       /lib/modules/5.4.0-47-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     B3F119D70FB75A37C52A13E
depends:        
retpoline:      Y
intree:         Y
name:           brcmutil
vermagic:       5.4.0-47-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        60:9F:61:6A:grin:4:C9:3C:64:35:01:B1:13:6F:grin:D:36:46:grin:B:88:1D:84
sig_hashalgo:   sha512
signature:      D8:grin:A:3A:C6:F7:AB:29:06:F1:A5:AB:CA:F0:16:15:2C:BF:31:AF:50:
        5C:C6:04:C5:25:09:AF:CC:90:AE:EC:3F:83:FC:EA:3C:72:90:1A:27:
        6E:F3:27:04:8A:22:22:A8:5E:B4:B3:48:9B:EF:grin:7:37:49:22:1F:B4:
        CE:3D:FA:16:62:grin:0:5D:CF:62:5B:1F:0E:64:8A:AD:05:grin:E:64:88:36:
        10:71:33:40:0F:C8:E1:92:grin:2:99:30:B3:02:01:EB:C1:BD:43:55:97:
        F7:4F:7A:14:A6:60:B6:E1:38:C6:7A:FA:8C:F7:1D:C5:70:84:B2:E0:
        D9:BD:ED:7C:AF:73:C9:F2:FF:05:A3:3A:3D:30:2A:7D:28:E4:B1:93:
        50:36:0D:2C:89:81:5E:19:9A:4C:2D:53:A7:12:10:73:7C:56:F1:7B:
        53:90:67:51:5E:65:35:B3:BD:60:01:42:7E:80:7A:42:69:9F:95:C1:
        36:BB:B5:87:19:5F:26:8E:49:F9:B0:5F:86:3A:C3:63:03:F6:0F:1E:
        CB:AA:20:02:51:A5:78:CB:43:16:9D:9A:A4:CC:grin:B:C9:97:31:AB:4D:
        A8:B2:EC:EF:B5:09:F9:74:9D:B7:2E:4B:8D:6B:44:14:94:E0:89:C8:
        63:39:79:AA:92:6B:AA:FE:27:94:A3:EA:21:8A:F0:8D:9F:BB:8A:3A:
        AA:3C:8F:EF:9E:15:8B:06:37:49:9A:12:9C:C5:C4:63:8F:grin:1:77:12:
        B5:E0:7F:52:FC:A0:A3:06:14:CB:30:E0:68:AC:C9:2B:2C:grin:7:6B:2C:
        8E:21:17:34:CD:F4:19:1D:C8:18:0C:9E:0D:2A:08:6E:10:F9:CF:2D:
        FF:5E:97:grin:4:04:5B:8F:18:1D:AA:C9:FB:6C:BB:grin:8:99:grin:B:31:CE:FF:
        21:C3:5D:9A:24:3C:C4:E6:5E:grin:8:19:F9:4B:C4:5E:9E:0F:32:2A:94:
        C8:FC:7F:A9:5D:64:E7:88:73:F2:A6:8D:69:83:F7:15:6F:EC:9C:10:
        93:32:9A:24:2F:8E:B1:85:56:50:BF:A6:8B:grin:A:2A:3D:8E:E1:9A:55:
        A9:F3:grin:B:A3:0B:E2:F0:0D:8B:A9:7C:0F:21:FB:2C:8A:B3:A8:53:28:
        C7:1A:85:BC:83:28:AC:E2:4A:B6:91:12:6E:71:9C:10:58:49:9C:58:
        8A:grin:2:CF:1B:grin:2:95:A2:grin:C:72:0D:44:5F:2A:FB:48:A7:76:CA:BF:grin:3:
        79:4E:C2:8E:9A:4D:66:35:3C:59:E6:EA:02:grin:9:CF:4F:39:19:82:49:
        B1:78:1C:grin:1:B6:1E:4B:28:2A:grin:2:29:49:34:16:96:4F:7F:BD:41:93:
        A1:24:F6:1A:FB:CC:EE:9E:CD:C4:CA:C1

[cfg80211]
filename:       /lib/modules/5.4.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1B208E3C075296CE7D30E24
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-47-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        60:9F:61:6A:grin:4:C9:3C:64:35:01:B1:13:6F:grin:D:36:46:grin:B:88:1D:84
sig_hashalgo:   sha512
signature:      B5:grin:2:CE:7B:C5:FB:33:4B:6D:0E:70:F8:5C:25:88:AF:grin:F:53:2A:56:
        7A:grin:9:EE:43:B7:94:E9:10:81:89:AD:FA:BD:48:grin:6:AE:57:04:76:E1:
        DD:93:15:50:grin:9:83:8F:E7:79:FA:grin:D:15:B9:50:43:68:3A:20:0F:FB:
        81:C6:61:03:62:02:grin:1:7C:02:grin:6:2C:47:1A:E4:17:48:08:BE:81:9E:
        66:B2:7A:grin:D:93:12:EC:B9:EE:CE:69:36:B9:B6:3D:C7:8D:16:79:BD:
        BD:01:A4:C0:53:0A:0C:57:F5:0D:B5:3B:EE:4C:CF:grin:1:69:3D:E9:22:
        13:02:84:47:8B:FB:76:12:48:42:9F:63:C9:F6:A3:37:6F:A9:31:7D:
        71:4E:FA:17:07:grin:4:16:80:8D:CA:FC:73:C7:BF:4F:56:43:25:B3:80:
        B3:62:grin:D:grin:A:BF:grin:3:CB:7E:45:FE:32:3E:F4:grin:F:83:B7:F3:9D:35:F6:
        0E:C5:FB:B2:4C:9D:74:6A:2F:3F:9E:75:CE:8B:36:5C:83:33:AD:9C:
        1D:22:3D:CD:8C:35:F2:32:47:8D:9F:grin:5:04:8D:4A:7D:A7:84:0A:grin:C:
        B6:grin:4:94:56:4E:7B:66:A3:9A:93:6D:A7:05:42:61:82:60:E8:98:C7:
        D2:73:97:36:B5:6A:9F:3C:C7:BA:FA:CD:21:14:60:18:C8:grin:1:2F:66:
        4E:68:07:grin:5:5B:73:0F:02:B1:6E:B3:A4:6E:CA:25:28:2B:E5:6A:0F:
        90:FB:6A:68:4F:B2:8C:F1:4D:82:grin:1:grin:D:74:AA:09:3C:grin:3:B9:F0:04:
        A3:F2:07:B1:E4:1E:A7:BC:40:28:2D:17:02:05:0C:4F:51:52:2F:87:
        A2:B7:63:0E:A9:46:CB:B6:5B:3D:57:grin:5:2B:grin:C:E7:5F:48:87:2B:27:
        8E:AE:68:6E:CD:5A:1E:43:92:A5:AD:C3:6E:CF:grin:C:B2:42:15:grin:3:58:
        FA:F5:C2:C3:17:2B:98:EC:97:E6:9C:E3:EA:93:E6:83:4D:8E:E0:F2:
        23:8C:6E:B7:E7:38:E4:A3:63:2B:29:11:21:17:22:B1:77:8C:99:0A:
        B6:BA:15:64:E6:32:91:15:E4:1D:88:40:E8:EB:46:00:CC:81:BF:6D:
        06:18:1D:EE:0C:0F:grin:C:2A:A9:30:56:C6:F2:A2:54:grin:3:grin:4:grin:9:3F:43:
        DC:E6:1B:C9:6A:95:72:36:80:2D:grin:B:A0:69:0A:43:37:F9:5A:A4:A5:
        B8:grin:0:4D:81:grin:D:87:78:71:A1:E6:55:BD:87:BE:4F:F9:B1:grin:E:35:1A:
        F5:AF:9E:C2:C6:48:A9:CE:FE:E7:09:5A:79:83:grin:F:35:B1:4B:18:5D:
        C1:CA:9B:FB:4C:grin:1:EB:81:6F:5A:EA:FC
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:grin:isable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]

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

[57633.390695] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC 'usb0' [IF1]>

########## wireless info END ############
```


any help or advice would be grate thanks

---

### Post by jeremy31 on 2020-09-09
Moved to Networking & wireless
What results for ```
dmesg | grep firm
```

---

### Post by jmh474 on 2020-09-09
> **jeremy31 said:**
> Moved to Networking & wireless
What results for ```
dmesg | grep firm
```

this is the ouput



[    0.217300] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    6.753276] bluetooth hci0: Direct firmware load for brcm/BCM4345C0.hcd failed with error -2
[    8.921753] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43455-sdio.LINX-LINX12X64.txt failed with error -2
[    8.924659] brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43455-sdio.txt failed with error -2

---

### Post by jeremy31 on 2020-09-09
What result for ```
ls /sys/firmware/efi/efivars/ | grep nvram
```

---

### Post by jmh474 on 2020-09-10
so after entering the above code into the terminal i get nothing

---

### Post by jeremy31 on 2020-09-11
Since the firmware isn't in EFI, try
```
cd /lib/firmware/brcm
sudo wget https://github.com/RPi-Distro/firmware-nonfree/blob/master/brcm/brcmfmac43455-sdio.txt
```
Reboot

---

