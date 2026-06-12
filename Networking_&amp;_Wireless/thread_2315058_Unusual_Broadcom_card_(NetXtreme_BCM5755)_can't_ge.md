---
title: "Unusual Broadcom card (NetXtreme BCM5755) can't get working, Ubuntu 15.10"
date: 2016-02-25
forum: Networking &amp; Wireless
---

### Post by normtheconqueror on 2016-02-25
I got a surplus PC a little while ago and when I installed Ubuntu, there was no wireless ability (big surprise). I have zero clue what I can do about this, however; Googling doesn't bring up very many helpful guides. Here's the results of "lspci -nn -d 14e4:"

```
3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)
```

and here's the results of the wireless info script that's stickied here:

```
########## wireless info START ##########

Report from: 25 Feb 2016 19:54 EST -0500

Booted last: 25 Feb 2016 00:00 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-30-generic #35-Ubuntu SMP Fri Feb 19 13:52:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:2808]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0c45:0520 Microdia MaxTrack Wireless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp63s0   Link encap:Ethernet  HWaddr <MAC 'enp63s0' [IF]>  
          inet addr:192.168.0.23  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2606:a000:54c4:7000:2432:96c1:6dbd:a6c8/64 Scope:Global
          inet6 addr: 2606:a000:54c4:7000:<IP6 'enp63s0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'enp63s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2466 errors:0 dropped:1 overruns:0 frame:0
          TX packets:2183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:917502 (917.5 KB)  TX bytes:283751 (283.7 KB)
          Interrupt:17 

##### iwconfig ##########################

enp63s0   no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp63s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp63s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp63s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       553     1  0 19:46 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp63s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5755 Gigabit Ethernet PCI Express
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5755-v3.12
GENERAL.HWADDR:                         <MAC 'enp63s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:3f:00.0/net/enp63s0
GENERAL.IP-IFACE:                       enp63s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       eab80f15-c796-44cd-a6f6-000a440973a6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   eab80f15-c796-44cd-a6f6-000a440973a6 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.23/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.62
IP4.DNS[2]:                             209.18.47.61
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_interface_mtu = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        host_name = killian-hp-compaq-dc5700-small-form-factor
DHCP4.OPTION[8]:                        expiry = 1456451253
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_domain_name = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.23
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_lease_time = 3600
DHCP4.OPTION[20]:                       domain_name_servers = 209.18.47.62 209.18.47.61
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_domain_name_servers = 1
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2606:a000:54c4:7000:2432:96c1:6dbd:a6c8/64
IP6.ADDRESS[2]:                         2606:a000:54c4:7000:<IP6 'enp63s0' [IF]>/64
IP6.ADDRESS[3]:                         fe80::<IP6 'enp63s0' [IF]>/64
IP6.GATEWAY:                            fe80::eaed:5ff:fe3e:2bf7

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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

enp63s0   no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp63s0   Interface doesn't support scanning.

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
blacklist b43
blacklist ssb

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   29.959160] IPv6: ADDRCONF(NETDEV_UP): enp63s0: link is not ready (repeated 2 times)
[   33.758752] tg3 0000:3f:00.0 enp63s0: Link is up at 1000 Mbps, full duplex
[   33.758778] tg3 0000:3f:00.0 enp63s0: Flow control is on for TX and on for RX
[   33.758810] IPv6: ADDRCONF(NETDEV_CHANGE): enp63s0: link becomes ready
[   56.420045] tg3 0000:3f:00.0 enp63s0: Link is down
[   73.673614] IPv6: ADDRCONF(NETDEV_UP): enp63s0: link is not ready (repeated 2 times)
[   86.700129] tg3 0000:3f:00.0 enp63s0: Link is up at 1000 Mbps, full duplex
[   86.700158] tg3 0000:3f:00.0 enp63s0: Flow control is on for TX and on for RX
[   86.700201] IPv6: ADDRCONF(NETDEV_CHANGE): enp63s0: link becomes ready

########## wireless info END ############
```

Again, I'm really at a loss for what to do. If there's anyone who has experience with this device, what was your solution?

---

### Post by Hadaka on 2016-02-25
Hi, That is your wired connection card, your Ethernet not wireless..
```
Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b]
    Subsystem: Hewlett-Packard Company Device [103c:2808]
    Kernel driver in use: tg3
```
it is currently in use as your wired connection
Your wireless 'lspci...lsusb..ifconfig...iwconfig wireless report showed NO wireless card present.
I would suggest replacing the card or using a usb wireless.
And just so you dont go away empty handed please open a terminal ctrl/alt/t
then copy and paste.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```
Thanks.

---

### Post by FaultedGeologist on 2016-02-26
> **normtheconqueror said:**
> I got a surplus PC a little while ago and when I installed Ubuntu, there was no wireless ability (big surprise). I have zero clue what I can do about this, however; Googling doesn't bring up very many helpful guides. 

Again, I'm really at a loss for what to do. If there's anyone who has experience with this device, what was your solution?

You can get a native supported card for use in or on your PC here:

[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

Be prepared for the $15 shipping charge.  I am awaiting an answer on what is good from Amazon.  There are other threads on supported hardware, but you never know if you are getting the right chipset in your model.  Running unsupported wifi cards requires some driver searching and installation or some windows wrapper work, which others say is not so supported.

You can use a pci card with antenna on the back for better range in a huuuge house, but the two usb options should work fine.  Look at the router you are using, google the model number, and find out if it is G, N, or AC.  G is old, N is still functional but probably needs updated firmware, and AC is current/future and not so supported on many mid-age devices.  If your router is type N, order that thumbnail size usb wifi card in the penguin link above and be done with the hassle.

Cheers!

---

