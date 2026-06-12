---
title: "Wireless LAN 802.11a/b/g/n/ac (1x1) adaptor not compatible with Ubuntu"
date: 2018-11-18
forum: Networking &amp; Wireless
---

### Post by lj-fin on 2018-11-18
I have a new HP Pavilion 590-p0060d Desktop PC  with bionic beaver Ubuntu dual boot the when in windows 10 it connects to my NBN (Australian national broadband network) constantly fast but when in Ubuntu it can't use it's internal adaptor 
here is the wireless-info:
```
########## wireless info START ##########
Report from: 19 Nov 2018 11:22 AEDT +1100
Booted last: 19 Nov 2018 00:00 AEDT +1100
Script from: 22 Oct 2018 03:34 UTC +0000
##### release ###########################
Distributor ID:    UbuntuDescription:    Ubuntu 18.04.1 LTSRelease:    18.04Codename:    bionic
##### kernel ############################
Linux 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=1
##### desktop ###########################
Ubuntu
##### lspci #############################
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]    Subsystem: Hewlett-Packard Company Device [103c:831b]    Kernel modules: r8822be
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:843b]    Kernel driver in use: r8169
##### lsusb #############################
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 001 Device 005: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02Bus 001 Device 004: ID 0000:0538  Bus 001 Device 003: ID 046d:0a37 Logitech, Inc. USB Headset H540Bus 001 Device 008: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6Bus 001 Device 006: ID 0bda:b00b Realtek Semiconductor Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
##### PCMCIA card info ##################
##### rfkill ############################
0: hci0: Bluetooth    Soft blocked: no    Hard blocked: no
##### secure boot #######################
SecureBoot enabled
##### lsmod #############################
mac80211              778240  0hp_wmi                 16384  0sparse_keymap          16384  1 hp_wmiwmi_bmof               16384  0cfg80211              622592  1 mac80211mxm_wmi                16384  1 nouveauwmi                    24576  4 wmi_bmof,mxm_wmi,nouveau,hp_wmi
##### interfaces ########################
[/etc/network/interfaces]auto loiface lo inet loopback
##### ifconfig ##########################
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000    link/loopback <MAC address> brd <MAC address>    inet 127.0.0.1/8 scope host lo       valid_lft forever preferred_lft forever    inet6 ::1/128 scope host        valid_lft forever preferred_lft forever2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>4: enp0s20f0u2c4i2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000    link/ether <MAC 'enp0s20f0u2c4i2' [IF2]> brd <MAC address>    inet 172.20.10.2/28 brd 172.20.10.15 scope global dynamic noprefixroute enp0s20f0u2c4i2       valid_lft 85288sec preferred_lft 85288sec    inet6 fe80::9142:621c:e141:191/64 scope link noprefixroute        valid_lft forever preferred_lft forever
##### iwconfig ##########################
enp0s20f0u2c4i2  no wireless extensions.
lo        no wireless extensions.
enp3s0    no wireless extensions.
##### route #############################
default via 172.20.10.1 dev enp0s20f0u2c4i2 proto dhcp metric 100 169.254.0.0/16 dev enp0s20f0u2c4i2 scope link metric 1000 172.20.10.0/28 dev enp0s20f0u2c4i2 proto kernel scope link src 172.20.10.2 metric 100 
##### resolv.conf #######################
[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']
nameserver 127.0.0.53
##### network managers ##################
Installed:
    NetworkManager
Running:
root       737     1  0 11:02 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
##### NetworkManager info ###############
GENERAL.DEVICE:                         enp0s20f0u2c4i2GENERAL.TYPE:                           ethernetGENERAL.NM-TYPE:                        NMDeviceEthernetGENERAL.VENDOR:                         Apple Inc.GENERAL.PRODUCT:                        iPhoneGENERAL.DRIVER:                         iphethGENERAL.DRIVER-VERSION:                 --GENERAL.FIRMWARE-VERSION:               --GENERAL.HWADDR:                         <MAC 'enp0s20f0u2c4i2' [IF2]>GENERAL.MTU:                            1500GENERAL.STATE:                          100 (connected)GENERAL.REASON:                         0 (No reason given)GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:4.2/net/enp0s20f0u2c4i2GENERAL.IP-IFACE:                       enp0s20f0u2c4i2GENERAL.IS-SOFTWARE:                    noGENERAL.NM-MANAGED:                     yesGENERAL.AUTOCONNECT:                    yesGENERAL.FIRMWARE-MISSING:               noGENERAL.NM-PLUGIN-MISSING:              noGENERAL.PHYS-PORT-ID:                   --GENERAL.CONNECTION:                     Wired connection 2GENERAL.CON-UUID:                       230aedfe-26e8-392a-807a-a47b20d5d68dGENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2GENERAL.METERED:                        no (guessed)CAPABILITIES.CARRIER-DETECT:            yesCAPABILITIES.SPEED:                     unknownCAPABILITIES.IS-SOFTWARE:               noCAPABILITIES.SRIOV:                     noWIRED-PROPERTIES.CARRIER:               onIP4.ADDRESS[1]:                         172.20.10.2/28IP4.GATEWAY:                            172.20.10.1IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.20.10.1, mt = 100IP4.ROUTE[2]:                           dst = 172.20.10.0/28, nh = 0.0.0.0, mt = 100IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000IP4.DNS[1]:                             172.20.10.1DHCP4.OPTION[1]:                        requested_host_name = 1DHCP4.OPTION[2]:                        requested_domain_search = 1DHCP4.OPTION[3]:                        server_name = ImarksDHCP4.OPTION[4]:                        requested_time_offset = 1DHCP4.OPTION[5]:                        requested_domain_name = 1DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1DHCP4.OPTION[7]:                        requested_broadcast_address = 1DHCP4.OPTION[8]:                        dhcp_message_type = 5DHCP4.OPTION[9]:                        expiry = 1542672226DHCP4.OPTION[10]:                       requested_netbios_scope = 1DHCP4.OPTION[11]:                       next_server = 172.20.10.1DHCP4.OPTION[12]:                       requested_wpad = 1DHCP4.OPTION[13]:                       requested_interface_mtu = 1DHCP4.OPTION[14]:                       requested_subnet_mask = 1DHCP4.OPTION[15]:                       dhcp_lease_time = 85536DHCP4.OPTION[16]:                       routers = 172.20.10.1DHCP4.OPTION[17]:                       ip_address = 172.20.10.2DHCP4.OPTION[18]:                       broadcast_address = 172.20.10.15DHCP4.OPTION[19]:                       requested_domain_name_servers = 1DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.240DHCP4.OPTION[21]:                       requested_routers = 1DHCP4.OPTION[22]:                       domain_name_servers = 172.20.10.1DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1DHCP4.OPTION[25]:                       requested_ntp_servers = 1DHCP4.OPTION[26]:                       requested_static_routes = 1DHCP4.OPTION[27]:                       network_number = 172.20.10.0DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.20.10.1IP6.ADDRESS[1]:                         fe80::9142:621c:e141:191/64IP6.GATEWAY:                            --IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   230aedfe-26e8-392a-807a-a47b20d5d68d | Wired connection 2
GENERAL.DEVICE:                         <MAC address>GENERAL.TYPE:                           btGENERAL.NM-TYPE:                        NMDeviceBtGENERAL.VENDOR:                         --GENERAL.PRODUCT:                        --GENERAL.DRIVER:                         bluezGENERAL.DRIVER-VERSION:                 --GENERAL.FIRMWARE-VERSION:               --GENERAL.HWADDR:                         <MAC address>GENERAL.MTU:                            0GENERAL.STATE:                          30 (disconnected)GENERAL.REASON:                         0 (No reason given)GENERAL.UDI:                            /org/bluez/hci0/dev_8C_1A_BF_A7_A9_31GENERAL.IP-IFACE:                       --GENERAL.IS-SOFTWARE:                    noGENERAL.NM-MANAGED:                     yesGENERAL.AUTOCONNECT:                    yesGENERAL.FIRMWARE-MISSING:               noGENERAL.NM-PLUGIN-MISSING:              noGENERAL.PHYS-PORT-ID:                   --GENERAL.CONNECTION:                     --GENERAL.CON-UUID:                       --GENERAL.CON-PATH:                       --GENERAL.METERED:                        unknownCAPABILITIES.CARRIER-DETECT:            noCAPABILITIES.SPEED:                     unknownCAPABILITIES.IS-SOFTWARE:               noCAPABILITIES.SRIOV:                     noBLUETOOTH.CAPABILITIES:                 NAPCONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ac11c723-b170-40dc-8e2a-635833860872 | Nat's S7 edge  Network
GENERAL.DEVICE:                         enp3s0GENERAL.TYPE:                           ethernetGENERAL.NM-TYPE:                        NMDeviceEthernetGENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet ControllerGENERAL.DRIVER:                         r8169GENERAL.DRIVER-VERSION:                 2.3LK-NAPIGENERAL.FIRMWARE-VERSION:               --GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>GENERAL.MTU:                            1500GENERAL.STATE:                          20 (unavailable)GENERAL.REASON:                         2 (Device is now managed)GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:03:00.0/net/enp3s0GENERAL.IP-IFACE:                       --GENERAL.IS-SOFTWARE:                    noGENERAL.NM-MANAGED:                     yesGENERAL.AUTOCONNECT:                    yesGENERAL.FIRMWARE-MISSING:               noGENERAL.NM-PLUGIN-MISSING:              noGENERAL.PHYS-PORT-ID:                   --GENERAL.CONNECTION:                     --GENERAL.CON-UUID:                       --GENERAL.CON-PATH:                       --GENERAL.METERED:                        unknownCAPABILITIES.CARRIER-DETECT:            yesCAPABILITIES.SPEED:                     unknownCAPABILITIES.IS-SOFTWARE:               noCAPABILITIES.SRIOV:                     noWIRED-PROPERTIES.CARRIER:               offCONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
##### NetworkManager.state ##############
[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnabled=true
##### NetworkManager config #############
[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]][connection]wifi.powersave = 3
[[/etc/NetworkManager/NetworkManager.conf]][main]plugins=ifupdown,keyfile[ifupdown]managed=false[device]wifi.scan-rand-mac-address=no
[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]][main]dns=systemd-resolved
[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]][keyfile]unmanaged-devices=*,except:type:wifi,except:type:wwan
[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]][connectivity]uri=http://connectivity-check.ubuntu.com/
[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]][device-mac-addr-change-wifi]match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wlwifi.scan-rand-mac-address=nowifi.cloned-mac-address=preserveethernet.cloned-mac-address=preserve
##### NetworkManager profiles ###########
##### Netplan config ####################
[/etc/netplan/01-network-manager-all.yaml]network:  version: 2  renderer: NetworkManager
##### iw reg get ########################
Region: Australia/Hobart (based on set time zone)
globalcountry 00: DFS-UNSET    (2402 - 2472 @ 40), (N/A, 20), (N/A)    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
##### iwlist channels ###################
enp0s20f0u2c4i2  no frequency information.
lo        no frequency information.
enp3s0    no frequency information.
##### iwlist scan #######################
enp0s20f0u2c4i2  Interface doesn't support scanning.
lo        Interface doesn't support scanning.
enp3s0    Interface doesn't support scanning.
##### module infos ######################
[mac80211]filename:       /lib/modules/4.15.0-29-generic/kernel/net/mac80211/mac80211.kolicense:        GPLdescription:    IEEE 802.11 subsystemsrcversion:     1CEA5CF286EDB289C1D0BF8depends:        cfg80211retpoline:      Yintree:         Yname:           mac80211vermagic:       4.15.0-29-generic SMP mod_unload signat:         PKCS#7signer:         sig_key:        sig_hashalgo:   md4parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
[cfg80211]filename:       /lib/modules/4.15.0-29-generic/kernel/net/wireless/cfg80211.kodescription:    wireless configuration supportlicense:        GPLauthor:         Johannes Bergsrcversion:     D5B0789D4C423C81CCFB437depends:        retpoline:      Yintree:         Yname:           cfg80211vermagic:       4.15.0-29-generic SMP mod_unload signat:         PKCS#7signer:         sig_key:        sig_hashalgo:   md4parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
##### module parameters #################
[mac80211]beacon_loss_count: 7ieee80211_default_rc_algo: minstrel_htmax_nullfunc_tries: 2max_probe_tries: 5minstrel_vht_only: Yprobe_wait_ms: 500
[cfg80211]bss_entries_limit: 1000cfg80211_disable_40mhz_24ghz: Nieee80211_regdom: 00
##### /etc/modules ######################
##### modprobe options ##################
[/etc/modprobe.d/amd64-microcode-blacklist.conf]blacklist microcode
[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci
[/etc/modprobe.d/blacklist.conf]blacklist evbugblacklist usbmouseblacklist usbkbdblacklist eepro100blacklist de4x5blacklist eth1394blacklist snd_intel8x0mblacklist snd_aw2blacklist prism54blacklist bcm43xxblacklist garmin_gpsblacklist asus_acpiblacklist snd_pcspblacklist pcspkrblacklist amd76x_edac
[/etc/modprobe.d/blacklist-rare-network.conf]alias net-pf-3 offalias net-pf-6 offalias net-pf-9 offalias net-pf-11 offalias net-pf-12 offalias net-pf-19 offalias net-pf-21 offalias net-pf-36 off
[/etc/modprobe.d/intel-microcode-blacklist.conf]blacklist microcode
[/etc/modprobe.d/iwlwifi.conf]remove iwlwifi \(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \&& /sbin/modprobe -r mac80211
##### rc.local ##########################
grep: /etc/rc.local: No such file or directory
##### pm-utils ##########################
##### udev rules ########################
##### dmesg #############################
[   22.349559] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready[   22.387199] r8169 0000:03:00.0 enp3s0: link down[   22.387310] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready[   88.131036] ipheth 1-2:4.2 enp0s20f0u2c4i2: renamed from eth0[   88.152441] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2c4i2: link is not ready (repeated 2 times)[   98.780312] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s20f0u2c4i2: link becomes ready[  966.123546] ipheth 1-2:4.2 enp0s20f0u2c4i2: renamed from eth0[  966.180113] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2c4i2: link is not ready (repeated 2 times)[  967.793483] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s20f0u2c4i2: link becomes ready
########## wireless info END ############
```

---

### Post by chili555 on 2018-11-18
What is the exact response to the terminal command:```
sudo modprobe r8822be
```

---

### Post by wildmanne39 on 2018-11-18
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by lj-fin on 2018-11-18
```
modprobe: ERROR: could not insert 'r8822be': Required key not available 
```

---

### Post by chili555 on 2018-11-18
[https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

Disable secure boot and you should be all set.

---

