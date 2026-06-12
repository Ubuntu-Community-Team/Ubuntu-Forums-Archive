---
title: "Wifi not visible after reinstalling Ubuntu 16.04 Sony Vaio Qualcomm Atheros AR9485"
date: 2017-03-31
forum: Networking &amp; Wireless
---

### Post by penthicilea on 2017-03-31
Please could you help me.

I upgraded from Trusty to Xenial a few months ago and have been experiencing an extremely slow system since. I then tried installing the Mint desktop which did install as I suddenly had 2 different software centres and 2 folder icons on the left of the screen for Files but I never figured out how to actuall boot into the Mint desktop. 
Anyway I decided to start fresh (relatively) and booted from a USB running 16.04 and went for the install "something different" option to install Ubuntu fresh without having to format and put all my data back etc. I have done 2 backups, one using the ubuntu backup software and one by copying the "Home" folder onto an external drive.
So if I really have to I could reinstall properly.
I have a dual boot system setup with Windows 7

My Problem is that since the installation (I selected 3rd party software and do updates during installation) I cannot connect to the internet
The wifi icon is there and it shows a live Ethernet connection. (I'm not sure what that means, there are no cables plugged in)
It cannot see my router (or any others for that matter)
Yet everything was working fine before.
If I boot from USB everything is fine, I can see the router and get online

I tried reinstall 4 or 5 times. with and without the 3rd party software or the"update while installing"

all no go

I am now sitting on the floor with a cable plugged into the router and I'm online. Ive tried a few thigs that I've seen other people suggest. I am not comfortable with command line beyond copy pasting commands really.

I've done sudo apt-get update and 
sudo apt dist-upgrade

NO difference

spci -nn gives me

```

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] [1002:6741] (rev ff)
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 07)
03:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e232] (rev 04)
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
```

iwconfig gives me

```
lo        no wireless extensions.

enp5s0    no wireless extensions.


```

Lots of the other solutions seem to be specific to Broadcom wireless and mine is Qualcomm Atheros

The results of the ./wireless info is

```

########## wireless info START ##########

Report from: 31 Mar 2017 17:09 BST +0100

Booted last: 31 Mar 2017 00:00 BST +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

lspci: Unable to load libkmod resources: error -12

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Foxconn International, Inc. Unex DHXA-225 [105b:e044]

03:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 07)

05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Sony Corporation AR8151 v2.0 Gigabit Ethernet [104d:9081]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 003: ID 062a:4101 Creative Labs Wireless Keyboard/Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:18c0 Ricoh Co., Ltd 
Bus 001 Device 004: ID 0489:e036 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp5s0    Link encap:Ethernet  HWaddr <MAC 'enp5s0' [IF1]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::23cd:b765:a436:2521/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:639812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:359355 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:922526057 (922.5 MB)  TX bytes:26979757 (26.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1580614 (1.5 MB)  TX bytes:1580614 (1.5 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp5s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp5s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp5s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       655     1  0 15:20 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8151 v2.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp5s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/enp5s0
GENERAL.IP-IFACE:                       enp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b8b36774-8768-479f-80ff-2abe60499104
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b8b36774-8768-479f-80ff-2abe60499104 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1491057551
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.5
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = lan
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::23cd:b765:a436:2521/64
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

[[/etc/NetworkManager/system-connections/PLUSNET-T6P3RP]] (600 root)
[connection] id=PLUSNET-T6P3RP | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PLUSNET-T6P3RP
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

enp5s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp5s0    Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  996.778726] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready (repeated 2 times)
[ 1004.297046] atl1c 0000:05:00.0: atl1c: enp5s0 NIC Link is Up<100 Mbps Full Duplex>
[ 1004.297083] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready

########## wireless info END ############


```

As said if I really have to I could probably reformat properly and reinstall. But after looking for a solution for this and seeing how many other people have had the same or similar problems after installing 16.04 I'm concerned I might still have the same issue.

Thanking you in advance for any help and clear instructions you can give.

There were also some instructions I found last night along the lines of a command to switch the wireless networks off and on again. But all that did was get me a message popup saying wireless connection now off-line (or something. ie the same message I would usually get if I switch my wifi off manually on the laptop) and then the wireless light goes out and doesn't come back even if I try switch it on again

sudo ip link set wlan0 up    gets an answer of 
Cannot find device "wlan0"

---

### Post by jeremy31 on 2017-03-31
For some reason the wireless driver didn't load
```
sudo modprobe -v ath9k
```

---

### Post by penthicilea on 2017-03-31
OK. I had the idea to reboot again. clearly something that I tried has worked because it seems to all be up and running now. 
<3
Yay

yep. That's what seemed to happen with many people who've posted similar issues. At least it's working now. But I threw so many different things at it I have no idea which one stuck.

---

