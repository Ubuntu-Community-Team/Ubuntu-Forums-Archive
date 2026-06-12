---
title: "wifi not working on my Asus Laptop, Ubuntu 16.04 LTS"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by justin95 on 2016-06-04
I'm unable to use the wifi on my ASUS laptop only wired ethernet connection, here is the results of the wireless info script.
```

########## wireless info START ##########

Report from: 04 Jun 2016 19:23 EDT -0400

Booted last: 04 Jun 2016 00:00 EDT -0400

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. MT7630e 802.11bgn Wireless Network Adapter [105b:e074]
    Kernel modules: wl

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 0489:e069 Foxconn / Hon Hai 
Bus 002 Device 002: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################

wl                   6365184  0
cfg80211              565248  1 wl
toshiba_wmi            16384  0
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  2 toshiba_wmi,asus_wmi
wmi                    20480  2 toshiba_wmi,asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp4s0    Link encap:Ethernet  HWaddr 1c:b7:2c:29:ce:e0  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::499d:976e:f4c4:cfe6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85944459 (85.9 MB)  TX bytes:2314640 (2.3 MB)


##### iwconfig ##########################

enp4s0    no wireless extensions.

lo        no wireless extensions.


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       692     1  0 18:41 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         1C:B7:2C:29:CE:E0
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.2/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       2fbf7841-7e62-481c-b335-b46729afd3d5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2fbf7841-7e62-481c-b335-b46729afd3d5 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.0.20/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1465070766
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 3600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.20
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::499d:976e:f4c4:cfe6/64
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

```

also here is the info on my wireless networking card
   
description: Network controller

        product: MT7630e 802.11bgn Wireless Network Adapter
        vendor: MEDIATEK Corp.
        physical id: 0
        bus info: pci@0000:03:00.0
        version: 00
        width: 32 bits
        clock: 33MHz
        capabilities: cap_list
        configuration: latency=0
        resources: memory:fea00000-feafffff

---

### Post by Hadaka on 2016-06-07
Hi please open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then do..
```
sudo apt-get install --reinstall git linux-headers-$(uname -r) build-essential dkms
git clone https://github.com/neurobin/MT7630E/
cd MT7630E/
make
sudo make install
```

source.[http://ubuntuforums.org/showthread.php?t=2300107&page=2](http://ubuntuforums.org/showthread.php?t=2300107&page=2)
post#13

---

### Post by blurryface on 2016-12-22
Hello there, Im a noob to linux but Im not new to ubuntu.
I am using an asus k555lf laptop which came with the MT7630e wifi+bluetooth combo card.
I was having a plethora of issues to get the wireless to work but i did  my research and this method is sure to work on your card if you follow  every condition to boot.

here goes, Im using ubuntu- Gnome 16.04 but it should work for your build regardless of the desktop environment.
Try to go with a clean install for better results.
you will need ethernet of course.
after installation, you should update your build and you can do that by navigating to the software updater app.

next up run this command 
```
sudo apt-get install linux-headers-generic build-essential git
```

let the terminal do it's magic 

after its done downloading, run this command 
```
sudo apt-get install dkms
```

let the terminal do it's magic

next up youre gonna want to navigate to

```
https://github.com/neurobin/MT7630E/releases
``` 
and download the source code.zip of the latest release in your home folder also extract it .

navigate into the extracted folder and open a terminal there
run 
```
[FONT=arial] chmod +x install test uninstall bpatch[/FONT] 
```

the run 
```
[FONT=arial]
sudo ./install[/FONT]
```

or run 
```
sudo make dkms
```

to install with dkms.

your wireless should be working and the drivers will load at startup. 

cheers :grin:

---

