---
title: "upgrade 17.04 to 17.10 but no internet."
date: 2017-10-20
forum: Networking &amp; Wireless
---

### Post by Kris_M on 2017-10-20
Now that it's the 19th I thought I'd try again.

results of script:
```


########## wireless info START ##########


Report from: 19 Oct 2017 23:50 EDT -0400


Booted last: 19 Oct 2017 00:00 EDT -0400


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful


##### kernel ############################


Linux 4.10.0-37-generic #41-Ubuntu SMP Fri Oct 6 20:20:37 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, nomodeset, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu on Xorg


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b]
	Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection I217-V [1458:e000]
	Kernel driver in use: e1000e


05:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
	Subsystem: Intel Corporation Gigabit CT Desktop Adapter [8086:a01f]
	Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


mxm_wmi                16384  0
snd_soc_rt5640        118784  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          233472  2 snd_soc_ssm4567,snd_soc_rt5640
snd_pcm               102400  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
wmi                    16384  1 mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.41  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::b32:a277:7be:3102  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2  bytes 425 (425.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 106  bytes 12951 (12.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7900000-f7920000  


enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf78c0000-f78e0000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 826  bytes 61588 (61.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 826  bytes 61588 (61.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


enp5s0    no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    20100  0        0 eno1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       926     1  0 23:46 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       cfc6b2e5-1f76-3fc5-8aa2-914e35fb7dde
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cfc6b2e5-1f76-3fc5-8aa2-914e35fb7dde | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.41/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 8.8.8.8 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.41
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1508557616
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = kris-Z97X-UD3H
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::b32:a277:7be:3102/64
IP6.GATEWAY:                            --


GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82574L Gigabit Network Connection (Gigabit CT Desktop Adapter)
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               1.8-0
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:05:00.0/net/enp5s0
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


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: America/New_York (based on set time zone)


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


eno1      no frequency information.


enp5s0    no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


enp5s0    Interface doesn't support scanning.


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


ethtool -s eno1 wol d
exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############



```

---

### Post by dino99 on 2017-10-20
I've seen somewhere a similar complain, and a dev said it is solved by the next coming kernel; so wait a bit

---

### Post by zika on 2017-10-20
Check: [https://www.phoronix.com/scan.php?page=news_item&px=AppArmor-Linux-4.14](https://www.phoronix.com/scan.php?page=news_item&px=AppArmor-Linux-4.14)
Try turning AppArmor off (several ways to do that, the simplest one to me is via kernel boot command line)...

---

### Post by zika on 2017-10-20
> **dino99 said:**
> I've seen somewhere a similar complain, and a dev said it is solved by the next coming kernel; so wait a bit[https://ubuntuforums.org/showthread.php?t=2373368](https://ubuntuforums.org/showthread.php?t=2373368)

---

### Post by wildmanne39 on 2017-10-20
*Thread moved to **Networking & Wireless for better a better fit **.*

---

### Post by Kris_M on 2017-10-20
credit beameup:

> **beameup said:**
> Fixed! This link
```
https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04/622493#622493
```

These commands
```


sudo dpkg-reconfigure resolvconf

Say yes to "prepare /etc/resolve.conf for dynamic updates?"

sudo reboot


```

Thanks!
execute those lines one at a time
I added 
sudo service network-manager restart

---

### Post by Irihapeti on 2017-10-20
Duplicate thread - closed.

---

