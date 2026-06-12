---
title: "Ubuntu 16.04; No wifi"
date: 2018-08-19
forum: Networking &amp; Wireless
---

### Post by jellman2 on 2018-08-19
Hello All, 

I hope someone can help me out; I have very basic knowledge of Ubuntu.

I have a HP Pavilion 20 All-In-One and very recently updated to Ubuntu 16.04. 

I only recently updated to 16.04 because when I previously installed updates in 14.02 (a few years back now) I lost wifi capability (so I did a factory reset and used the machine without ever adding updates). Anyway, so I put off installing until the lack of updates effected performance, so I finally installed the updates a few days ago and then updated to 16.04. Everything was working fine; I should have stop with the updates at this point.

However I then started to get a problem installing other updates which seemed to relate to the realtek wifi car; I searched the forum and found some instructions which seemed similar to my problem. But whatever I entered into the terminal has lost wifi capability. Now I'm not sure what to do; wifi doesn't work at all. Can anyone give me any help ?

I know I haven't included any technical information (but if you can tell me what you want; and the commands to get it) I'll respond.

At the moment I've moved the computer near the router and connected by cable; but it's not practicle to leave it in that location; I would greatly appreciate any help you can provided (and I'll thank you in advance for you patience).

John

---

### Post by jeremy31 on 2018-08-19
See the wireless script link in my signature and post results

---

### Post by jellman2 on 2018-08-19
Thanks for the response. The output of the Wireless Script instructions is below. Hope this is added in the correct format. let me know if not. And thanks for looking at this.



```
########## wireless info START ##########

Report from: 19 Aug 2018 13:31 BST +0100

Booted last: 19 Aug 2018 00:00 BST +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.5 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 3.2.0-126-generic #169-Ubuntu SMP Fri Mar 31 14:15:21 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, i915.modeset=1, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2af0]
	Kernel driver in use: r8169

04:00.0 Network controller [0280]: Ralink corp. RT5390R 802.11bgn PCIe Wireless Network Adapter [1814:539b]
	Subsystem: Hewlett-Packard Company RT5390R 802.11bgn PCIe Wireless Network Adapter [103c:18ed]

05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b34a Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 003 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF1]>  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26176906 (26.1 MB)  TX bytes:3010402 (3.0 MB)
          Interrupt:48 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97489 (97.4 KB)  TX bytes:97489 (97.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth1      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       747     1  0 12:40 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'eth1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0/net/eth1
GENERAL.IP-IFACE:                       eth1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       3a55103a-f195-478e-817f-e853d11c5102
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3a55103a-f195-478e-817f-e853d11c5102 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.30/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             194.168.4.100
IP4.DNS[2]:                             194.168.8.100
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = theresa-20-b101ea
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       expiry = 1535542807
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 864000
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.30
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 194.168.4.100 194.168.8.100
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'eth1' [IF1]>/64
IP6.GATEWAY:                            

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

[[/etc/NetworkManager/system-connections/VM0914916 1]] (600 root)
[connection] id=VM0914916 1 | type=802-11-wireless
[802-11-wireless] ssid=VM0914916 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM0914916]] (600 root)
[connection] id=VM0914916 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=VM0914916 | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=ignore

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

eth1      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
lp

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

[/etc/modprobe.d/blacklist-opensource-graphics.conf]
blacklist nouveau
blacklist radeon 
blacklist lbm-nouveau
blacklist lbm-radeon 
alias radeon off
alias lbm-radeon off

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

[/etc/modprobe.d/iwlwifi-opt.conf]
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

echo 0 > /sys/module/video/parameters/brightness_switch_enabled
exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:15.0/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:15.1/0000:04:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    6.932925] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   24.849096] r8169 0000:03:00.0: eth1: unable to load firmware patch rtl_nic/rtl8105e-1.fw (-2)
[   24.971372] r8169 0000:03:00.0: eth1: link down (repeated 2 times)
[   24.972589] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   26.570149] r8169 0000:03:00.0: eth1: link up
[   26.571162] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

########## wireless info END ############
```

---

### Post by praseodym on 2018-08-19
Hi, kernel 3.2 doesn't ship the driver, it needs to be installed by hand:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/34/30/3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3
wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA 
```
Reboot.

---

### Post by jellman2 on 2018-08-19
Thanks for this. Sorry  to ask what I assume is going to be a stupid question, but... Do I paste the whole things into terminal or do I past each line seperatley then press return ? (If I paste all text at once, I only seem to see part of the text in the terminal and it doesn't seem to work but when I do it line by the line it seems to come up with errors). I'm clearly doing something wrong can you give me some guidance. Sorry about this.

---

### Post by jellman2 on 2018-08-20
Update; I managed to install 18.04 via the Terminal (as it wasn't offering  the update in software updater). This has reinstated wifi (although I still have another problem which if I can't resolve I'll ask in a different thread).

Anyway thanks to those that responded.

Issue Resolved.

---

