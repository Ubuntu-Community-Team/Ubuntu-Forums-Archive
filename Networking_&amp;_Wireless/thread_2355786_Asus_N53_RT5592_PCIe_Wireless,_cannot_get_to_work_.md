---
title: "Asus N53 RT5592 PCIe Wireless, cannot get to work on 16.04-16.10"
date: 2017-03-16
forum: Networking &amp; Wireless
---

### Post by the-alchemist on 2017-03-16
So, this is the driver I found...

[https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10](https://github.com/kuttor/Asus-N53-PCU-RT5592STA-Driver-for-Linux-Kernel-4.6-Ubuntu-16.10)

And I can get the    sudo lshw -C network    to show this:

[https://cdn.discordapp.com/attachments/291740981508964353/291973322537697281/IMG_20170316_123711586.jpg](https://cdn.discordapp.com/attachments/291740981508964353/291973322537697281/IMG_20170316_123711586.jpg)

so the system not only knows it's there, but what it is...

However, I still cannot find a way to use it. I'm a complete newbro to all of this so it could just be massive, wild, unrivaled incompetence on my part and just not knowing where to look.

Even then, the little thing that says "DISABLED" next to the entry tells me something isnt right. 

The logical name I believe is enp6s0, and I did try running    ifconfig enp6s0 up    which seems to remove the disabled status, but i still do not get wifi... 

Not sure where to go from here, so any help would be appreciated!

---

### Post by jeremy31 on 2017-03-16
*Thread moved to **Networking & Wireless**.* 
Welcome to the forums, check results for ```
rfkill list all
```
Who made the computer?

---

### Post by the-alchemist on 2017-03-16
Thanks!

rfkill list all does not return anything at all. It just runs, no errors nothing.


And I made the computer. It's my last rig that I wanted to turn into a linux box, but to do anything with it that I'd have wanted to, I need it to connect to the internet. I "could" hard line it in but not long term.

---

### Post by jeremy31 on 2017-03-16
If you connect to a hard line, see the wireless script link in my signature and post results.  

From the looks of the source on github, I would have run ```
make clean
``` right after changing into the source directory as whoever this guy is uploaded it after compiling rather than uploading clean source code

---

### Post by the-alchemist on 2017-03-16
Incoming wall of text...


```
########## wireless info START ##########

Report from: 16 Mar 2017 16:44 EDT -0400

Booted last: 16 Mar 2017 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

##### kernel ############################

Linux 4.8.0-41-generic #44-Ubuntu SMP Fri Mar 3 15:27:17 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 04)
    Subsystem: ASRock Incorporation Ethernet Connection I217-V [1849:153b]
    Kernel driver in use: e1000e

04:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: ASRock Incorporation I211 Gigabit Network Connection [1849:1539]
    Kernel driver in use: igb

06:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
    Subsystem: ASUSTeK Computer Inc. RT5592 PCIe Wireless Network Adapter [1043:851a]

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 003: ID 1532:0036 Razer USA, Ltd RZ01-0075, Gaming Mouse [Naga Hex]
Bus 003 Device 002: ID 03f0:2a4a Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf3500000-f3520000  

enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4b87:cee6:acfc:44fa  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1283  bytes 1009243 (1.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1111  bytes 117737 (117.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xf3300000-f331ffff  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 9275  bytes 568978 (568.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9275  bytes 568978 (568.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp4s0    no wireless extensions.

enp0s25   no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       947     1  0 16:39 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        I211 Gigabit Network Connection
GENERAL.DRIVER:                         igb
GENERAL.DRIVER-VERSION:                 5.3.0-k
GENERAL.FIRMWARE-VERSION:                0. 4-1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       12f225fc-c8cb-38ac-aee1-c77ee9c5c713
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   12f225fc-c8cb-38ac-aee1-c77ee9c5c713 | Wired connection 2
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1489783205
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.6
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::4b87:cee6:acfc:44fa/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection I217-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

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

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp4s0    no frequency information.

enp0s25   no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp4s0    Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############
```

---

### Post by andrew-kuttor on 2017-05-24
[COLOR=#111111][FONT=Ubuntu]Suprised to see someone link to my Github. :)

Just confirmed the driver is working on 16.04 and 16.10 -- AND, up to linux Kernel 4.11.2

To get it to work I did the make clean, make, make install. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Then, [/FONT][/COLOR]

[LIST=1]
[*]sudo ip link set "name of the Wifi" down
[*]sudo ip link set "name of the Wifi" up
[*]sudo systemctl restart NetworkManager
[/LIST]

(I am currently using the driver unchanged from my repo)

P.S. When The wifi card shows up on my list it appears as "enp2s0"

```

yeti@machine$ uname -a
Linux machine 4.11.2-041102-generic #201705201036 SMP Sat May 20 14:38:21 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

yeti@machine$ ip link show enp2s0
3: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DORMANT group default qlen 1000
    link/ether e0:3f:49:8b:90:0a brd ff:ff:ff:ff:ff:ff


```

---

### Post by wildmanne39 on 2017-05-24
@andrew-kuttor, thanks for posting and for having the driver on github for people to use.  We rely on drivers on github quite a bit working with wireless issues.:D

---

### Post by andrew-kuttor on 2017-05-24
@Jeremy31

Yeah, thanks for catching that.

---

### Post by andrew-kuttor on 2017-05-24
@wildmanne39

Absolutely, I'm just stoked it's found some benefit other than myself... The PCE-N53 is such a pain and Asus isn't much help.

---

### Post by praseodym on 2017-05-25
[https://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915](https://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915)

Try this one. You are using Kernel 4.8, not 4.6. Of course, this one may not work either

---

