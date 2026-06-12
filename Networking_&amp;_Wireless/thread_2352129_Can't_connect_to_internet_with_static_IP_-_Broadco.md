---
title: "Can't connect to internet with static IP - Broadcom BCM5754"
date: 2017-02-09
forum: Networking &amp; Wireless
---

### Post by Randall_Quinn on 2017-02-09
Hi,

I got an old DELL T7400 donated to replace my less powerful file/plex server, but I cant seem to get it working with a static IP. It just drops all network connection when I try and set it up:

It's an ethernet adapter - Broadcom BCM5754It's currently connected to my router using DHCP with IP address 192.168.1.151, however I want it on 192.168.1.101. 

I have tried to set this up in "Edit connections" and I have tried to edit the interfaces file as follows:

```


#The loopback network interfaceauto lo
iface lo inet loopback


#The primary network interface
auto enp8s0
iface enp8s0 inet static
       address 192.168.1.101
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.1.255
       gateway 192.168.1.1
       dns-nameservers 8.8.8.8



```

Each time, network connectivity drops out. I can't see where I'm going wrong.

Here is the output from the wireless-info.txt:

```




########## wireless info START ##########


Report from: 09 Feb 2017 19:56 GMT +0000


Booted last: 09 Feb 2017 00:00 GMT +0000


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell NetXtreme BCM5754 Gigabit Ethernet PCI Express [1028:021d]
    Kernel driver in use: tg3


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. MK260 Wireless Combo Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp8s0    Link encap:Ethernet  HWaddr <MAC 'enp8s0' [IF1]>  
          inet addr:192.168.1.151  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::fb61:3cbc:bb48:733e/64 Scope:Link
          inet6 addr: fdd1:4be9:5109:0:18eb:2085:521b:9bfc/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100586055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67452243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146392253867 (146.3 GB)  TX bytes:6389203469 (6.3 GB)
          Interrupt:16 


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       856     1  0 06:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5754 Gigabit Ethernet PCI Express
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5754-v3.24
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Ethernet connection 1
GENERAL.CON-UUID:                       8648a7bb-f215-4470-8be1-b7c919b58590
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8648a7bb-f215-4470-8be1-b7c919b58590 | Ethernet connection 1
IP4.ADDRESS[1]:                         192.168.1.151/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             81.139.56.100
IP4.DNS[2]:                             81.139.57.100
IP4.DNS[3]:                             192.168.1.1
IP4.DNS[4]:                             8.8.4.4
IP4.DNS[5]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1486677254
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 10800
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.151
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 81.139.56.100 81.139.57.100 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fdd1:4be9:5109:0:18eb:2085:521b:9bfc/64
IP6.ADDRESS[2]:                         fe80::fb61:3cbc:bb48:733e/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fdd1:4be9:5109::/64, nh = ::, mt = 100


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


Region: Europe/Dublin (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp8s0    no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp8s0    Interface doesn't support scanning.


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


intel_rng: don't want to disable this in firmware setup, and if
[   43.317055] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready (repeated 2 times)
[   44.913807] tg3 0000:08:00.0 enp8s0: Link is up at 100 Mbps, full duplex
[   44.913824] tg3 0000:08:00.0 enp8s0: Flow control is on for TX and on for RX
[   44.913848] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready


########## wireless info END ############



```

If someone could point me in the right direction I would REALLY appreciate it.

EDIT: I commented out the static part of the interfaces to download and run the "wireless-info.txt". If i need to run it specifically with the settings I am having trouble with, let me know and I will.

Thanks

---

### Post by wildmanne39 on 2017-02-09
I see you are running network manager so it will over ride the interfaces file unless you uninstall it.

Here is a guide from the expert on networking:
[http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

### Post by Randall_Quinn on 2017-02-09
Thanks for the guide. I have tried deleting all connection from the network manager and starting up the interface with:

sudo ifdown enp8s0 && sudo ifup -v enp8s0

I have tried commenting out the interfaces lines specific to static IP address and adding it in with network manager separately, and vice versa.

I have tried the accepted answer in that guide and could not ping the gateway or google.

Do I need to do more to disable network manager than delete all the connections in it? (edit, sorry my tired eyes didn't read that right). Can I not just use the network manager to set the static IP then? I mean I know I'm supposed to be able to but I don't understand why it wont work. I'm adding in a new ethernet connection, changing DHCP to manual then:

Address: 198.168.1.101
Mask: 255.255.255.0
Gateway: 192.168.1.1
And save, disconnect, reconnect.... then it says I'm connected with 192.168.1.101 but I can't log into the router on 192.168.1.1 or get on the internet.

---

### Post by wildmanne39 on 2017-02-09
You have to uninstall network manager.

---

### Post by Randall_Quinn on 2017-02-10
I uninstalled network manager and still couldn't connect at all

---

### Post by wildmanne39 on 2017-02-10
Did you setup the interfaces file to look like the one in the link I gave you substituting your information though?

---

