---
title: "Incorrect IP address, gateway; where is it getting this address?"
date: 2019-11-08
forum: Networking &amp; Wireless
---

### Post by rafe101 on 2019-11-08
Can anyone help me solve a network problem?

For years and years my media /web server has had the same local ip address and over those years that ip (192.168.1.100) got really entrenched. Now, I've had to change its address because I moved and the only way to get something even approaching usable internet speeds was to use a hybrid cell/DSL router from the telecom. That router wouldn't let me use 192.168.1.xxx; the closest I could set it to was 192.168.2.xxx. So, I changed the 1 to a 2 everywhere i could find it, but still couldn't get on the internet. I tried setting network manager to use automatic dhcp, but still couldn't get online. The correct (new) ip showed up when I queried it and was in the gui info, but still nothing: "no route to host".

What I stumbled on is that when I pinged there was the old ip:

htpc@htpc:~$ ping -c5 198.252.206.24
PING 198.252.206.24 (198.252.206.24) 56(84) bytes of data. From 192.168.1.100 icmp_seq=1 Destination Host Unreachable From 192.168.1.100 icmp_seq=2 Destination Host Unreachable From 192.168.1.100 icmp_seq=3 Destination Host Unreachable From 192.168.1.100 icmp_seq=4 Destination Host Unreachable From 192.168.1.100 icmp_seq=5 Destination Host Unreachable
--- 198.252.206.24 ping statistics --- 5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4098ms pipe 4

[but then if I do this...] 
htpc@htpc:~$ sudo ip route add default via 192.168.2.1
[presto] 
htpc@htpc:~$ ping -c5 198.252.206.24
PING 198.252.206.24 (198.252.206.24) 56(84) bytes of data. 64 bytes from 198.252.206.24: icmp_seq=1 ttl=54 time=115 ms 64 bytes from 198.252.206.24: icmp_seq=2 ttl=54 time=116 ms 64 bytes from 198.252.206.24: icmp_seq=3 ttl=54 time=116 ms 64 bytes from 198.252.206.24: icmp_seq=4 ttl=54 time=114 ms 64 bytes from 198.252.206.24: icmp_seq=5 ttl=54 time=116 ms
--- 198.252.206.24 ping statistics --- 5 packets transmitted, 5 received, 0% packet loss, time 4005ms rtt min/avg/max/mdev = 114.835/115.828/116.216/0.663 ms

I know the output is old, but I have tried clearing the ARP table since then, but this is still ongoing.
I've now tried to install Bubbleupnp and though i go to the correct address to get the web interface, it's listening on the old, nonexistent address

---

### Post by The Cog on 2019-11-08
Are these command being run on the media server, or on another PC on the local LAN?

192.168.1.100 is clearly still there on the network. It needs reconfiguring. If configuring by editing a config file then it may need restarting to get it to use the new settings.

---

### Post by johnarnold on 2019-11-08
I'm assuming these are from the media server. Could you run an 'ifconfig' so we can see the config of the interfaces on this machine? 
The fact you can add a default gateway using a 192.168.2.x address suggests the server does have an IP on this range.

---

### Post by rafe101 on 2019-11-10
The new router will not assign addresses in the 192.168.1.xxx range. I assume it's because it's a hybrid cellular /DSL and is using that range for something already. In any case, it won't let me set that range, so i had to use 192.168.2.xxx for the new network.

The below is after manually setting the gateway as in original post. 

Last login: Fri Nov  8 00:22:05 2019 from 192.168.2.201
htpc@htpc:~$ ifconfig
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.100  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 2003:d3:5f0e:ce73:7de0:a7c8:8744:19cb  prefixlen 64  scopeid
0x0<global>
        inet6 fe80::fd3d:365c:693f:35f4  prefixlen 64  scopeid 0x20<link>
        inet6 2003:d3:5f0e:ce73:b1e0:c0c7:42a6:216e  prefixlen 64  scopeid
0x0<global>
        ether 4c:cc:6a:fe:c3:10  txqueuelen 1000  (Ethernet)
        RX packets 344363235  bytes 469995627085 (469.9 GB)
        RX errors 124  dropped 1215  overruns 0  frame 62
        TX packets 139573320  bytes 24143025864 (24.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdf600000-df620000

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 30778835  bytes 268887676229 (268.8 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 30778835  bytes 268887676229 (268.8 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by johnarnold on 2019-11-11
So the .100 is the box that you are pinging from? I don't think this IP is still in use if that's the case. As the setup works with the default gateway set can you not do this permanently?

---

### Post by rafe101 on 2019-11-11
That's the question. Why can't i permanently get rid of 192.168.1.100. Where is it getting that from and how to get rid of it so i don't have to set the gateway manually

---

### Post by jetsam on 2019-11-11
It seems it must be in some system or network cache somewhere...  could even be a browser cache...

Are you familiar with wireshark?  If you could packet-sniff the dns request that returns the bad old ip addy, it would answer a lot of questions and probably point to the solution.

---

### Post by jeremy31 on 2019-11-11
See the wireless script link in my signature and post results
It might find where the issue is

---

### Post by rafe101 on 2019-11-11
Replying to both: does it matter that this is wired and not wifi?

---

### Post by jeremy31 on 2019-11-11
It doesn't matter that it is ethernet for what we are looking for

---

### Post by rafe101 on 2019-11-15
I'm running the upgrades as your link suggests. I was hoping to stay on an LTS, but...whatever---if you can fix this...
I'm sort of thinking that somehow an old pihole is complicating things

---

### Post by rafe101 on 2019-11-15
What I got back:
```
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
htpc@htpc:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2019-11-15 12:45:50--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 140.82.118.4
Connecting to github.com (github.com)|140.82.118.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2019-11-15 12:45:51--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.12.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.12.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info                             100%[====================================================================================>]  17,04K  --.-KB/s    in 0,04s   

Last-modified header missing -- time-stamps turned off.
2019-11-15 12:45:51 (422 KB/s) - &#8216;wireless-info&#8217; saved [17452/17452]


Results saved in "/home/htpc/wireless-info.txt".

htpc@htpc:~$
```

---

### Post by rafe101 on 2019-11-15
So, I guess this is what you need:

```

########## wireless info START ##########

Report from: 15 Nov 2019 12:45 CET +0100

Booted last: 15 Nov 2019 00:00 CET +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-66-generic #75-Ubuntu SMP Tue Oct 1 05:24:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

MATE (from ~/.dmrc)

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Ethernet Connection (2) I219-V [1462:7a72]
	Kernel driver in use: e1000e

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 15c2:0036 SoundGraph Inc. LC16M VFD Display/IR Receiver
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 002: ID 0b38:0003 Gear Head Keyboard
Bus 001 Device 007: ID 1997:2433  
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 011: ID 20a0:0001 Clay Logic 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

cfg80211              622592  0
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback
gateway 192.168.2.1

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.2.100/24 brd 192.168.2.255 scope global noprefixroute enp0s31f6
       valid_lft forever preferred_lft forever
    inet 192.168.1.100/24 brd 192.168.1.255 scope global enp0s31f6
       valid_lft forever preferred_lft forever
    inet6 2003:d3:5f1c:44c2:49d9:7ec2:4f3b:19d1/64 scope global dynamic noprefixroute 
       valid_lft 604773sec preferred_lft 86373sec
    inet6 2003:d3:5f1c:44c2:5439:4904:77fe:a33d/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 604773sec preferred_lft 86373sec
    inet6 2003:d3:5f0e:ce73:b1e0:c0c7:42a6:216e/64 scope global dynamic noprefixroute 
       valid_lft 596278sec preferred_lft 77878sec
    inet6 2003:d3:5f0e:ce73:7de0:a7c8:8744:19cb/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 596278sec preferred_lft 77878sec
    inet6 fe80::fd3d:365c:693f:35f4/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.2.1 dev enp0s31f6 
default via 192.168.1.1 dev enp0s31f6 src 192.168.1.100 metric 202 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
192.168.1.0/24 dev enp0s31f6 proto kernel scope link src 192.168.1.100 metric 100 
192.168.1.0/24 dev enp0s31f6 proto kernel scope link src 192.168.1.100 metric 202 
192.168.2.0/24 dev enp0s31f6 proto kernel scope link src 192.168.2.100 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

nameserver 127.0.0.1
search speedport speedport.ip

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1184     1  0 Oct28 ?        00:00:58 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.8-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       695322d0-b2ab-4080-bd22-9b2e03dd393b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.2.100/24
IP4.ADDRESS[2]:                         192.168.1.100/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 192.168.2.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 202
IP4.ROUTE[4]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 202
IP4.ROUTE[5]:                           dst = 0.0.0.0/0, nh = 192.168.2.1, mt = 0
IP4.ROUTE[6]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.2.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             8.8.4.4
IP4.DOMAIN[1]:                          speedport.ip
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.2.0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 1814400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.2.100
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       routers = 192.168.2.1
DHCP4.OPTION[20]:                       domain_name = speedport.ip
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_domain_name_servers = 1
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       expiry = 1575579951
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         2003:d3:5f0e:ce73:b1e0:c0c7:42a6:216e/64
IP6.ADDRESS[2]:                         2003:d3:5f1c:44c2:49d9:7ec2:4f3b:19d1/64
IP6.ADDRESS[3]:                         2003:d3:5f0e:ce73:7de0:a7c8:8744:19cb/64
IP6.ADDRESS[4]:                         2003:d3:5f1c:44c2:5439:4904:77fe:a33d/64
IP6.ADDRESS[5]:                         fe80::fd3d:365c:693f:35f4/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = 2003:d3:5f1c:44c2::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = 2003:d3:5f0e:ce73::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ::/0, nh = fe80::1, mt = 100
IP6.ROUTE[4]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[6]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[7]:                           dst = 2003:d3:5f0e:ce73::/64, nh = ::, mt = 202
IP6.ROUTE[8]:                           dst = 2003:d3:5f1c:44c2::/64, nh = ::, mt = 202
IP6.ROUTE[9]:                           dst = ::/0, nh = fe80::1, mt = 202
IP6.ROUTE[10]:                          dst = ::/0, nh = ::, mt = 202
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:9b:b2:4:da:20:53:b8:73:b7:60:84:3d:61:ab:44:26
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_domain_search = speedport.
DHCP6.OPTION[7]:                        dhcp6_preference = 255
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:18:74:e4:2d:b8:66:85:93:ff:40
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   695322d0-b2ab-4080-bd22-9b2e03dd393b | Ethernet connection 1

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

Region: Europe/Berlin (based on set time zone)

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

enp0s31f6  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s31f6  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-66-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5EE775D8EACA80C712223E1
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-66-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############
```

---

### Post by jetsam on 2019-11-15
Oof.  That's a lot to go through.  

Searching for your bad ip address reveals several hits.  

I think I'd look first at network manager.  It's been a source of tricky behavior for so long, it's like an old friend in a way... I used to routinely delete it when I first installed a release.

Some edited excerpts:

##### NetworkManager info ###############
...
IP4.ADDRESS[2]: 192.168.1.100/24
...

This is the net block definition.  Do we want it to be there?  We want that first ip to never get returned by any name service.

Let's see.  You have several name services going, and any one of them or something else could be the culprit.
There's something on your loacalhost: [**a hosts file at least.  Have you looked at your hosts file?**]:
There's netbios: [Microsoft's network name service from some iteration of Samba]
There's a dhcp server somewhere: [This assigns ip addresses to newly attached network device assuming the above two don't do the trick]
There's normal dns: [This is how the internet trades names.  Once a dns server is assigned, firefox or another relevant client will send name requests to that dns server.  I believe it should have priority before netbios, but not before the hosts file on your local machine.]

Definitely look for a hosts file or a spare one somewhere in your config files.  Failing that, I'd still recommend packet sniffing an actual bad dns request.  That's the most direct way to find out where the bad address is being returned from, and what service is asking for it.

Edited to add:
Additional complication comes from caching.  Both locally (in the browser, on the desktop machine, somewhere in the networking stack) programs and services can and do have caches that could be returning the address.  All the network services may be configured to have caches as well, and those caches would be located somewhere in their working directories or simply residing in memory.  We're chasing ghosts sometimes.

---

### Post by rafe101 on 2019-12-08
Sorry about the long break in contact. My network has changed again. I'm back to my old router so (almost) everything is working as it likes.
Only thing is that bubbleupnp is somehow stuck on the previous address : 19.168.2.100.
Really weird thing is when it was supposed to be that address, it only knew the 1.100 one.

---

### Post by lensman3 on 2019-12-11
Try the commands"ip route"  , "netstat -r" or "netstat -nr",  and "route".

Ubuntu can remember the default route between boots.  Netplan is the culprit and is not (yet) a product for prime time.

---

