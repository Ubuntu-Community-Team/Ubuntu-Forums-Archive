---
title: "Wifi and Ethernet not working after upgrading to 18.04"
date: 2018-09-26
forum: Networking &amp; Wireless
---

### Post by rsmnrr on 2018-09-26
Hello everyone!
Here's the story, i've been using ubuntu 16.04 **casually** for quite a while . i post something before because i have a wireless problem here's the link [https://ubuntuforums.org/showthread.php?t=2330805](https://ubuntuforums.org/showthread.php?t=2330805).
My internet works perfectly fine before upgrading to 18.04 a week ago, after the upgrade finish, it keep saying  "Connection failed: Activation of network connection failed"
i thought it might be my wireless adapter need to recompiled, but it still doesn't work, and when i plug my ethernet cable it keep showing the same message. 
It does this weird thing where the button for airplane mode and bluetooth turn into toggle button when my wifi is off. so if airplane is off the bluetooth is on and vice versa. and the airplane button only appear when my wifi is off(?)

So im thinking since this is an old laptop anyway, and i've been loving working casually with linux, why not try to install another Linux based OS. maybe that would fix the problem and i did.

but the same problem still occurred. 
i've been trying to ask in here, but since my laptop has no connection, i'm afraid it would take me quite some time to gather the necessary info.

so im leaving this old _wireless info script_ from my old post just in case it needed :
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
this is my network adapter connected through USB:
Bus 002 Device 002: ID 0bda:b720 Realtek Semiconductor Corp.

also it shows this message on startup :
"firmware: failed to load rtl_bt/rtl8723b_config.bin (-2) 
see [https://wiki.debian.org/Firmware](https://wiki.debian.org/Firmware) for information about missing firmware"

is it hardware problem?
Please help 
Let me know if you need any necessary info, i would try to get it if i could
(and sorry for my bad english..)

---

### Post by Autodave on 2018-09-26
Rarely have I ever had luck with upgrading.  I always do clean installs: they are easier and usually a lot faster.  Back up everything that you need to an external device FIRST!!  Then download your choice, burn it as an .iso file, and boot the machine to it.  When presented with options, chose: Erase 16.04 and install 18.04.

---

### Post by rsmnrr on 2018-09-26
I'll try reinstalling 18.04 tomorrow, its just kinda weird for me that my network is still not working even after i change OS (especially via ethernet cable). I thought maybe it might be a hardware problem since it is a pretty old laptop, but it works fine before i upgrade (on 16.04)

---

