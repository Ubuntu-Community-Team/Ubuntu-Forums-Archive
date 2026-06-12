---
title: "Why does my wireless adapter does not recognized in ubuntu 16.04??"
date: 2016-07-15
forum: Networking &amp; Wireless
---

### Post by rsmnrr on 2016-07-15
Hello!!

so i just installed ubuntu 16.04 recently, my wifi is working on the previous OS which is windows 8, but not in this one...
it looks like the wireless adapter is not even there for some reason, there's no broadcom drivers in additional drivers, 
rfkill list all : 
```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```
lspci :
```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
02:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)

```
the Fn+F4 that i usually used for turning my wifi on/off, now works on bluetooth instead... i don't even remember that i have a bluetooth in this laptop back when i still use windows 8
does this mean my wireless adapter doesnt compatible with ubuntu or something??

i seen a lot of threads and follow a lot of instruction, but still get nothing, PLS HELP....
(sorry for my bad english btw)

---

### Post by howefield on 2016-07-15
Thread moved to the "*Networking & Wireless*" forum as requested.

---

### Post by slickymaster on 2016-07-15
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by rsmnrr on 2016-07-15
```
 
########## wireless info START ##########

Report from: 15 Jul 2016 22:02 WIB +0700

Booted last: 15 Jul 2016 00:00 WIB +0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Device [1d05:1017]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1e4e:0110 Cubeternet 
Bus 002 Device 002: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0f1  Link encap:Ethernet  HWaddr <MAC 'enp2s0f1' [IF1]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8665:817c:26f0:e8da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4350601 (4.3 MB)  TX bytes:417754 (417.7 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0f1  no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0f1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       718     1  0 21:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.1/net/enp2s0f1
GENERAL.IP-IFACE:                       enp2s0f1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7ede5e66-59df-4d71-bf53-f8f8420ca4be
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7ede5e66-59df-4d71-bf53-f8f8420ca4be | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = TP-LINK
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.3
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 226800
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 129600
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1468853871
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::8665:817c:26f0:e8da/64
IP6.GATEWAY:                            

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

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

enp2s0f1  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0f1  Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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
blacklist wmi
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

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/owfs-common.conf]
blacklist ds9490r
blacklist ds2490
blacklist wire

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   14.596185] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   14.596190] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   29.170641] IPv6: ADDRCONF(NETDEV_UP): enp2s0f1: link is not ready
[   29.352431] r8169 0000:02:00.1 enp2s0f1: link down
[   29.352496] IPv6: ADDRCONF(NETDEV_UP): enp2s0f1: link is not ready
[   81.591869] r8169 0000:02:00.1 enp2s0f1: link up
[   81.591882] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0f1: link becomes ready

########## wireless info END ############


```

---

### Post by rsmnrr on 2016-07-15
> **howefield said:**
> Thread moved to the "*Networking & Wireless*" forum as requested.

thank you ^^

---

### Post by wildmanne39 on 2016-07-15
There is no card showing at all, go into the bios and make sure wifi is enabled if there is that option, make sure that it is enabled in windows before you boot ubuntu.

Disable secure boot and see if it shows up that is an issue with broadcom cards.

Also you have network manager and wicd installed I recommend you uninstall wicd they can not be installed at the same time.
Thanks

---

### Post by rsmnrr on 2016-07-15
> **Wild Man said:**
> There is no card showing at all, go into the bios and make sure wifi is enabled if there is that option, make sure that it is enabled in windows before you boot ubuntu.

Disable secure boot and see if it shows up that is an issue with broadcom cards.

Also you have network manager and wicd installed I recommend you uninstall wicd they can not be installed at the same time.
Thanks
Hmmm... I don't see any option related to wifi in bios, i disable the secure boot and uninstall wicd, 
it works fine in windows 8
is it possible that my wireless card doesn't compatible with this OS??

---

### Post by jeremy31 on 2016-07-15
Post ```
cat /sys/bus/sdio; cat /sys/bus/sdio/devices
```

I do think you have a Realtek wifi card since your lsusb results show a realtek bluetooth device

---

### Post by praseodym on 2016-07-15
```
Bus 002 Device 002: ID 0bda:b720 Realtek Semiconductor Corp. 
```
There it is, it is connected via USB (wireless/BT combo), please check

```
usb-devices
```

But so far the driver needs to be installed additionally, module name is **8723bu**:
```

sudo apt-get install --reinstall git build-essential linux-headers-generic linux-headers-$(uname -r)
git clone https://github.com/lwfinger/rtl8723bu
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu
```
Do not remove the driver folder, it needs to be recompiled after a kernel upgrade via
```

cd rtl8723bu
make clean
make
sudo make uninstall
sudo make install
```

Driver info:
```

modinfo 8723bu
filename:       /lib/modules/3.16.0-77-generic/kernel/drivers/net/wireless/8723bu.ko
version:        v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     F8398CEA8ECCBC1A2BDFA5B
alias:          usb:v0BDApB720d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
vermagic:       3.16.0-77-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_btcoex_enable:Enable BT co-existence mechanism (int)
parm:           rtw_ant_num:Antenna number setting (int)
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_special_rf_path:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable, 2:auto (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
```

---

### Post by rsmnrr on 2016-07-15
ITS WORKS, i follow mr. @praseodym instruction, and it works...
 Thank you so much everyone
the legend are true, this website are full of wizard

---

### Post by slickymaster on 2016-07-15
> **rsmnrr said:**
> ITS WORKS, i follow mr. @praseodym instruction, and it works...
 Thank you so much everyone
the legend are true, this website are full of wizard

It's great you got it working. Please mark the thread as SOLVED so other people searching the forums know that it provides a working solution for the problem.

---

