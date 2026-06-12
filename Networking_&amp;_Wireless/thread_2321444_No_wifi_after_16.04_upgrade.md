---
title: "No wifi after 16.04 upgrade"
date: 2016-04-22
forum: Networking &amp; Wireless
---

### Post by jon114 on 2016-04-22
Hi all,
Have just completed the upgrade to 16.04 and have no wifi.
In the networking tab of the settings menu the is no option to enable wifi.
After some googling I saw a thread about lshw -C which gives me the following result

-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b0500000-b0507fff

Within the Additional drivers tab of the update menu it show that it is using a proiprietary Linux Broadcom driver which is selected

Other than that I am stuck.
Have tried googling Network unclaimed but can only find old results, nothing relevant.
Any help very gratefully received.
Many thanks
Jon

---

### Post by jon114 on 2016-04-22
ok so doing some more work and reading I have followed the sticky "before posting...."  and installed the wireless info script. I know I have a Broadcom wireless card but I get no 0208 output mentioning Broadcom so can't get any further there.
Looking up my pci id I get 14e4 4365 which from the table mentioned in Chili555's post I see is described as "special case 2"
I have followed the thread with "sudo apt-get install linux-headers-generic build-essential dkms" but get the output
 "Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
build-essential set to manually installed.
dkms is already the newest version (2.2.0.3-2ubuntu11).
dkms set to manually installed.
linux-headers-generic is already the newest version (4.4.0.21.22).
linux-headers-generic set to manually installed.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-base libcdaudio1 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libslv2-9
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade."
So if I understand correctly nothing was downloaded as the system already has the most up to date package?
So I am back to square 1 and no clue of what to try next.
I've had 14.04 and 15.10 on the same laptop with no problems so am really confused why problems this time.
Hopefully someone will be able to offer some guidance please, I'm not experienced with Linux and trying hard to understand, this is why I went for the LTS version after all.
Anyone please??

---

### Post by kc1di on 2016-04-22
Could you run the wireless script found in my signature and post the output file here.

---

### Post by jon114 on 2016-04-22
```
######### wireless info START ##########

Report from: 22 Apr 2016 21:06 BST +0100

Booted last: 22 Apr 2016 00:00 BST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel modules: bcma, wl

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo QCA8172 Fast Ethernet [17aa:3801]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 004: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 003 Device 003: ID 0603:1605 Novatek Microelectronics Corp. 
Bus 003 Device 002: ID 174f:148d Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              565248  0
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr 20:1a:06:a5:1e:c2  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4265:aad2:6f49:b588/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1278612 (1.2 MB)  TX bytes:3014641 (3.0 MB)
          Interrupt:18 


##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       788     1  0 21:00 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8172 Fast Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         20:1A:06:A5:1E:C2
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b3c17ed7-8d1a-4841-82f8-74c5a530d218
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b3c17ed7-8d1a-4841-82f8-74c5a530d218 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.105/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1461362675
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.105
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::4265:aad2:6f49:b588/64
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

```

---

### Post by smapdi on 2016-04-22
I had the same issue going from 15.10 to 16.04 with my BCM4352 WiFi card. I got annoyed and just wiped my laptop and installed 16.04 from scratch. Still having issues with the driver being unstable and disconnecting (especially if there is heavy USB activity like reading from a memory stick).

I'm considering just re-installing 15.10 because 16.04 just doesn't seem fully baked yet.

---

### Post by jon114 on 2016-04-22
kc1di, is that what you were looking for?

---

### Post by Hadaka on 2016-04-22
Hi, The special version 2 is for 64bit Ubuntu 12.04, Ubuntu 14.04 and above
use the regular broadcom-kernel-source driver.
From a working wired connection...
Please open a terminal .. ctrl/alt/t .. and do...
*Ignore file not found or errors..
```
sudo apt-get remove --purge broadcom-kernel-source
sudo rm -rf bcma
```
then do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
Then install the wl driver..
```
sudo apt-get install --reinstall broadcom-kernel-source
sudo modprobe -v wl
```
remove wired connection,boot and test wireless
thanks.

---

### Post by jon114 on 2016-04-23
> **Hadaka said:**
> Hi, The special version 2 is for 64bit Ubuntu 12.04, Ubuntu 14.04 and above
use the regular broadcom-kernel-source driver.
From a working wired connection...
Please open a terminal .. ctrl/alt/t .. and do...
*Ignore file not found or errors..
```
sudo apt-get remove --purge broadcom-kernel-source
sudo rm -rf bcma
```
then do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
Then install the wl driver..
```
sudo apt-get install --reinstall broadcom-kernel-source
sudo modprobe -v wl
```
remove wired connection,boot and test wireless
thanks.

Hi Hadaka,
Ok so tried the bits of code you mention with various errors being displayed.
The first line returns "E: Unable to locate package broadcom-kernel-source"
and the reinstall line returns "E: Unable to locate package broadcom-kernel-source" also
while the modprobe line returns "insmod /lib/modules/4.4.0-21-generic/updates/dkms/wl.ko 
modprobe: ERROR: could not insert 'wl': Required key not available"

---

### Post by jon114 on 2016-04-23
ah sorry my mistake I should be changeing 
--reinstall broadcom-kernel-source

for the new driver?
Problem is I didn't understand the sticky on installing a new driver, started off nice and easy and then jumped a few steps

---

### Post by Hadaka on 2016-04-23
Hi thats why i suggested..
```
"Please open a terminal .. ctrl/alt/t .. and do...
*Ignore file not found or errors.."
```
Before the first command..please re-do one line
at a time..thanks.

---

### Post by jon114 on 2016-04-23
Not sure I understand, do I type "* ignore file not found or errors.." In to the terminal window or are you saying for me to ignore?
I did type it in 1 line at a time but will try again when get home later.

---

### Post by Hadaka on 2016-04-23
Hi jon114, usually anything outside the "box"/code tags
is a comment or instruction or note, I put it inside the code tags
to "magnify" it in post #10. also linux does not normally accept
things like * and uppercase letters.."*Ignore" so. I was giving instruction
and making a point. so basically do all the commands...one at a time even
if you get an error..just ignore and do the next command,
thanks,

---

### Post by jon114 on 2016-04-24
Ok thanks for that, may seem dumb but just wanted to be sure I was missing something obvious.
I repeated the lines one by one but unfortunately still no wifi or the ability to select wifi.
Just noticed another post that mentions secure boot, thought it worth mentioning as I was asked during install to create a password to disable secure boot, which I did?

---

### Post by adrian88 on 2016-04-24
Hey there, gonna hitch a ride on this post cause I just bough a new HP laptop, setup dual boot ubuntu/win10 and been banging my head for the past 4 hours over the exact same error with the exact same Broadcom card (BCM43142). Here's my wireless-info.txt for reference...

```

########## wireless info START ##########

Report from: 24 Apr 2016 23:15 AEST +1000

Booted last: 24 Apr 2016 00:00 AEST +1000

Script from: 27 Sep 2015 00:34 UTC +0000

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

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: NAMI
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:80cb]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 04f2:b509 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 2001:3319 D-Link Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  1 b43
ssb                    65536  1 b43
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              565248  2 b43,mac80211
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:150.203.223.88  Bcast:150.203.223.255  Mask:255.255.254.0
          inet6 addr: fe80::2df3:259d:8b7a:baa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9786759 (9.7 MB)  TX bytes:908590 (908.5 KB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         150.203.223.1   0.0.0.0         UG    100    0        0 enp3s0
130.56.15.84    150.203.223.1   255.255.255.255 UGH   100    0        0 enp3s0
150.203.222.0   0.0.0.0         255.255.254.0   U     100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search anu.edu.au

##### network managers ##################

Installed:

    NetworkManager

Running:

root       730     1  0 22:41 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       dcde6ebc-6d48-45d8-a4fa-96fb721d674c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dcde6ebc-6d48-45d8-a4fa-96fb721d674c | Wired connection 1
IP4.ADDRESS[1]:                         150.203.223.88/23
IP4.GATEWAY:                            150.203.223.1
IP4.ROUTE[1]:                           dst = 130.56.15.84/32, nh = 150.203.223.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             150.203.1.10
IP4.DNS[2]:                             150.203.22.28
IP4.DOMAIN[1]:                          anu.edu.au
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1461510493
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 150.203.223.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 150.203.223.88
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = anu.edu.au
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 150.203.223.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 7200
DHCP4.OPTION[23]:                       domain_name_servers = 150.203.1.10 150.203.22.28
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.254.0
DHCP4.OPTION[26]:                       network_number = 150.203.222.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 130.56.15.84
IP6.ADDRESS[1]:                         fe80::2df3:259d:8b7a:baa5/64
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

Region: Australia/Sydney (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ssb]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/wireless-bcm43142-dkms.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   11.393576] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   11.393589] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   22.923893] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   23.187003] r8169 0000:03:00.0 enp3s0: link down
[   23.187100] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  188.990511] r8169 0000:03:00.0 enp3s0: link up
[  188.990542] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 1007.201065] bcma: bus0: Found chip with id 43142, rev 0x01 and package 0x08
[ 1007.201094] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[ 1007.201114] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[ 1007.201149] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[ 1007.201192] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[ 1007.216181] bcma: bus0: Bus registered
[ 1013.054881] r8169 0000:03:00.0 enp3s0: link down
[ 1175.358646] r8169 0000:03:00.0 enp3s0: link up
[ 1502.312556] r8169 0000:03:00.0 enp3s0: link down
[ 1607.841877] r8169 0000:03:00.0 enp3s0: link up

########## wireless info END ############


```

I also followed the commands hadaka posted, and I got the following error from the very last bit;

```
sudo apt-get install --reinstall broadcom-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package broadcom-kernel-source
adrian@adrian-HP-Notebook:~$ sudo modprobe -v wl
install /sbin/modprobe --ignore-install wl $CMDLINE_OPTS 
insmod /lib/modules/4.4.0-21-generic/updates/dkms/wl.ko 
modprobe: ERROR: could not insert 'wl': Required key not available
modprobe: ERROR: ../libkmod/libkmod-module.c:977 command_do() Error running install command for wl
modprobe: ERROR: could not insert 'wl': Operation not permitted


```

Would appreciate any help!

---

### Post by jon114 on 2016-04-25
After reading a few more of the threads I decided to do a clean install via a USB drive which installed much more easily.
Interestingly I was again asked to choose a password to disable secure boot and used the same password as last time. This time however it wouldn't let me proceed as the password wasn't long enough, it didn't cause an error last time I guess it just ignored it and carried on.
A better password and things proceeded, so I was hopefull.
Unfortunately still no wifi but this time in the additional drives tab of software updates the wifi card is selected as "Do not use the device" where as the LTA driver was selected last time. Selecting LTA makes no difference as the selection does not hold after clicking Apply Changes.
Hadaka I carried out your instructions from earlier but again no change and have included the Wireless-info.txt output below from kc1di
Help, please!
```


########## wireless info START ##########

Report from: 25 Apr 2016 10:14 BST +0100

Booted last: 25 Apr 2016 00:00 BST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

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

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel driver in use: bcma-pci-bridge

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo QCA8172 Fast Ethernet [17aa:3801]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 004: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 003 Device 003: ID 0603:1605 Novatek Microelectronics Corp. 
Bus 003 Device 002: ID 174f:148d Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              565248  0
bcma                   53248  0
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ec5e:a781:e2cb:5601/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4245503 (4.2 MB)  TX bytes:347736 (347.7 KB)
          Interrupt:18 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       770     1  0 10:05 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8172 Fast Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0ad3cf6d-dbd0-46f0-bd37-a341d0eec593
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0ad3cf6d-dbd0-46f0-bd37-a341d0eec593 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.103/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1461582371
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.103
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::ec5e:a781:e2cb:5601/64
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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Homelands_farm_on_AB
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   11.620090] bcma: bus0: Found chip with id 43142, rev 0x01 and package 0x08
[   11.620117] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[   11.620138] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[   11.620180] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[   11.620232] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[   11.635122] bcma: bus0: Bus registered
[   28.770191] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   81.745029] alx 0000:03:00.0 enp3s0: NIC Up: 100 Mbps Full
[   81.745681] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready

########## wireless info END ############

```

---

### Post by jon114 on 2016-04-25
tried to select the STA driver again in Additional drives tab and for some reason the 3rd time it held after applying.
It now shows the device as using the broadcom STA driver, still doesn't work but maybe thats a step??

---

### Post by jon114 on 2016-04-26
After days of trying to fix this and reading all of the other threads with by far the majority also failing to find a fix I am giving up.
I've reinstalled 14LTS without issue and will stick with that until 16 is proven.
Seems to me it's not really ready for release to the public and they rushed it out.
Very disappointed.

---

### Post by jeremy31 on 2016-04-26
jon114, was Secure Boot enabled?  It seems to be an issue with the broadcom STA module

---

### Post by HuaiDan on 2016-05-01
Hi,
Just jumping on the bandwagon with random disconnects on a bcm43142 after upgrading to 16.04.
wl module wouldn't even load with secure boot enabled, so I had to disable that. Now I get random disconnects every couple of hours that require a reboot.

Edit: Shouldn't "broadcom-kernel-source" be "bcmwl-kernel-source"?

---

### Post by HuaiDan on 2016-05-01
Is a bug report open on this?

---

### Post by jeremy31 on 2016-05-01
> **HuaiDan said:**
> Hi,
Just jumping on the bandwagon with random disconnects on a bcm43142 after upgrading to 16.04.
wl module wouldn't even load with secure boot enabled, so I had to disable that. Now I get random disconnects every couple of hours that require a reboot.

Edit: Shouldn't "broadcom-kernel-source" be "bcmwl-kernel-source"?

It should be bcmwl-kernel-source

Please start your own post about disconnect issues and see the wireless script link in my signature and post the output in your post using code tags so formatting is preserved

If you have an ethernet connection feel free to enable secure boot and file a bug report.  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

There is a [bug report](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1572659) just click the pen icon near "Does this bug affect you" to be added to the affected users.  Do not add comments like others have done

It also says that you can use kernel 4.4.0-18 with secure boot enabled and have a functioning wifi so Pilot6 might be on to something in  [this answer](http://askubuntu.com/a/762255/300665)

---

### Post by HuaiDan on 2016-05-02
Done.
Could you please provide a hint on how to install the 4.4.0-18 kernel? Here's the result of my lame attempt. All the information I found googling suggests this should be possible:

```
$ sudo apt-get install linux-image-4.4.0-18-generic linux-headers-4.4.0-18 linux-headers-4.4.0-18-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-4.4.0-18-generic
E: Couldn't find any package by glob 'linux-image-4.4.0-18-generic'
E: Couldn't find any package by regex 'linux-image-4.4.0-18-generic'
E: Unable to locate package linux-headers-4.4.0-18
E: Couldn't find any package by glob 'linux-headers-4.4.0-18'
E: Couldn't find any package by regex 'linux-headers-4.4.0-18'
E: Unable to locate package linux-headers-4.4.0-18-generic
E: Couldn't find any package by glob 'linux-headers-4.4.0-18-generic'
E: Couldn't find any package by regex 'linux-headers-4.4.0-18-generic'

```
I've got all software sources enabled and updated. 
Edit: It seems all the deb's have been deleted from launchpad.

---

### Post by jeremy31 on 2016-05-02
Reboot and hold the shift key until the grub menu appears, then select advanced options, then select the 4.4.0-18 kernel

---

### Post by HuaiDan on 2016-05-02
Sorry, I guess I should've said I looked there already. The only other kernel I have installed is 4.2.0-35 left over from 15.10. I would need to install 4.4.0-18, but as I mentioned, neither the repos nor launchpad seem to offer it anymore.

---

### Post by jeremy31 on 2016-05-02
Pilot6 posted that 4.4.0-21 was the first Ubuntu kernel that causes this issue due to a change in the kernel config.  I will look to see if I have the debs on my Linux Mint laptop, LM uses stock Ubuntu kernels

But you might want to see if his answer on askubuntu works for you [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-dkms-modules-in-ubuntu-16/762255#762255](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-dkms-modules-in-ubuntu-16/762255#762255)

---

### Post by snehal4 on 2016-05-20
I've installed Ubuntu 16.04 from scratch and the wireless does not seem to work. I ran the wireless script, this being the output - 
```

########## wireless info START ##########

Report from: 20 May 2016 13:02 IST +0530

Booted last: 20 May 2016 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

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

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
    Kernel driver in use: bcma-pci-bridge

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Sony Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [104d:90be]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b42d Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0489:e062 Foxconn / Hon Hai 
Bus 002 Device 002: ID 03eb:880f Atmel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: nfc0: NFC
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

bcma                   53248  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5614:9037:b080:4fb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43454055 (43.4 MB)  TX bytes:1428691 (1.4 MB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       718     1  0 12:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       9123208f-1e4f-4a15-bde4-59d8f9aa26fd
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9123208f-1e4f-4a15-bde4-59d8f9aa26fd | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = Beetel
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.7
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
DHCP4.OPTION[20]:                       expiry = 1464007648
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc5
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::5614:9037:b080:4fb7/64
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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=ArcSneh
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[bcma]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    7.963264] bcma: bus0: Found chip with id 43142, rev 0x01 and package 0x08
[    7.963289] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[    7.963307] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[    7.963342] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[    7.963385] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[    7.978032] bcma: bus0: Bus registered
[    9.239860] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    9.239864] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   22.124059] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   22.211288] r8169 0000:03:00.0 enp3s0: link down
[   22.211353] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[ 1480.904382] r8169 0000:03:00.0 enp3s0: link up
[ 1480.904402] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 1497.931281] r8169 0000:03:00.0 enp3s0: link down
[ 1499.550351] r8169 0000:03:00.0 enp3s0: link up

########## wireless info END ############

```

I can't seem to figure out the problem. Any sort of help would be great :).

---

### Post by jeremy31 on 2016-05-20
> **snehal4 said:**
> I've installed Ubuntu 16.04 from scratch and the wireless does not seem to work. I ran the wireless script, this being the output - 
```

########## wireless info START ##########

Report from: 20 May 2016 13:02 IST +0530

Booted last: 20 May 2016 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

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

02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e071]
    Kernel driver in use: bcma-pci-bridge

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Sony Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [104d:90be]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b42d Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0489:e062 Foxconn / Hon Hai 
Bus 002 Device 002: ID 03eb:880f Atmel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: nfc0: NFC
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

bcma                   53248  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5614:9037:b080:4fb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43454055 (43.4 MB)  TX bytes:1428691 (1.4 MB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       718     1  0 12:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       9123208f-1e4f-4a15-bde4-59d8f9aa26fd
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9123208f-1e4f-4a15-bde4-59d8f9aa26fd | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = Beetel
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.7
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
DHCP4.OPTION[20]:                       expiry = 1464007648
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc5
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::5614:9037:b080:4fb7/64
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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=ArcSneh
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

enp3s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[bcma]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    7.963264] bcma: bus0: Found chip with id 43142, rev 0x01 and package 0x08
[    7.963289] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[    7.963307] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[    7.963342] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[    7.963385] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[    7.978032] bcma: bus0: Bus registered
[    9.239860] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[    9.239864] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   22.124059] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   22.211288] r8169 0000:03:00.0 enp3s0: link down
[   22.211353] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[ 1480.904382] r8169 0000:03:00.0 enp3s0: link up
[ 1480.904402] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 1497.931281] r8169 0000:03:00.0 enp3s0: link down
[ 1499.550351] r8169 0000:03:00.0 enp3s0: link up

########## wireless info END ############

```

I can't seem to figure out the problem. Any sort of help would be great :).

You will need to have secure boot disable in BIOS, then ```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```  Reboot

---

### Post by westwin-z on 2016-06-04
Hi Jeremy31.  As another one affected by the upgrade problem,  I really appreciate reading your helpful comments.  I was out of town for awhile and have been using the Windows partition on my laptop, since I did the 16.04 upgrade, but today will work on the wireless problem and get back to booting in to Ubuntu.  I am thinking of setting up an additional partition for keeping an older working-version of Ubuntu to boot up in the future if another upgrade "breaks" Ubuntu again.

---

### Post by dime-m on 2016-06-17
Hi, don't know where to post this (and my English is not so good, sorry), but: i have the same problems with my bcm43142 (HP G4 250 laptop) + (4.4.0-24-generic #43-Ubuntu 16.04 64'bit' GNU/Linux) - it drops connections per "any random time". Today (after many days of wifipain) I've seem that ping drop so many packages, BUT not for the first time - ONLY when u start ping anywhere for the second time after `modprobe or .. wifi goes on?` ! So i have decided to check if terminal will always ping ( * my router ip, cause don't be banned by anybody, of couse) and what i've seen: NO DROPPING while pinging. at all. (also packets AND wifi connection i mean + wifi signal meters "don't jump"). (64 bytes from 192.168.10.1: icmp_seq=6338 ttl=64 time=0.628 ms). but. Before this i disabled ipv6 and didn't change it back.. Tomorrow will check with ipv6 and other options.. I know this is not a cure, but it's working for me. What do next if i can help?
wrote all this here too [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1415880?comments=all](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1415880?comments=all)

---

### Post by vimothy on 2016-06-26
I'm having the same problem (as far as I can tell). Here's the output of the wireless script:

```


########## wireless info START ##########


Report from: 26 Jun 2016 19:18 BST +0100


Booted last: 26 Jun 2016 00:00 BST +0100


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell BCM4352 802.11ac Wireless Network Adapter [1028:0019]
	Kernel modules: bcma, wl


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
Bus 003 Device 005: ID 04f3:20d1 Elan Microelectronics Corp. 
Bus 003 Device 004: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 007: ID 0bda:573c Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 05ac:12a0 Apple, Inc. iPhone 4S
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: nfc0: NFC
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
cfg80211              565248  0
wmi                    20480  2 dell_wmi,mxm_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF1]>  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp0s20u1c4i2 Link encap:Ethernet  HWaddr <MAC 'enp0s20u1c4i2' [IF2]>  
          inet addr:172.20.10.2  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::3e3d:e9ae:8c33:1d53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4870789 (4.8 MB)  TX bytes:1566665 (1.5 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp0s20u1c4i2  no wireless extensions.


docker0   no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    100    0        0 enp0s20u1c4i2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 docker0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.20.10.0     0.0.0.0         255.255.255.240 U     100    0        0 enp0s20u1c4i2


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1087     1  0 19:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       2e88719f-98f9-4362-91b8-0362752814d7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{20}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2e88719f-98f9-4362-91b8-0362752814d7 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s20u1c4i2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Apple Inc.
GENERAL.PRODUCT:                        iPhone
GENERAL.DRIVER:                         ipheth
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s20u1c4i2' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:4.2/net/enp0s20u1c4i2
GENERAL.IP-IFACE:                       enp0s20u1c4i2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     iPhone
GENERAL.CON-UUID:                       3355f90b-5e1c-45e4-aa8b-46bdccd1cd79
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{17}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3355f90b-5e1c-45e4-aa8b-46bdccd1cd79 | iPhone
IP4.ADDRESS[1]:                         172.20.10.2/28
IP4.GATEWAY:                            172.20.10.1
IP4.DNS[1]:                             172.20.10.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = Lauras-iPhone
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 172.20.10.1
DHCP4.OPTION[11]:                       expiry = 1467050178
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 85536
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 172.20.10.2
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 172.20.10.1
DHCP4.OPTION[20]:                       broadcast_address = 172.20.10.15
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 172.20.10.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.240
DHCP4.OPTION[26]:                       network_number = 172.20.10.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.20.10.1
IP6.ADDRESS[1]:                         fe80::3e3d:e9ae:8c33:1d53/64
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


[[/etc/NetworkManager/system-connections/OnTheBeach]] (600 root)
[connection] id=OnTheBeach | type=wifi
[ipv6] method=auto
[wifi] ssid=OnTheBeach | mac-address=<MAC address>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TALKTALK-36FE0C]] (600 root)
[connection] id=TALKTALK-36FE0C | type=wifi
[wifi] ssid=TALKTALK-36FE0C | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BTHub3-H3P6]] (600 root)
[connection] id=BTHub3-H3P6 | type=wifi
[wifi] ssid=BTHub3-H3P6 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BTWiFi]] (600 root)
[connection] id=BTWiFi | type=wifi
[wifi] ssid=BTWiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/PARKSQCAFE]] (600 root)
[connection] id=PARKSQCAFE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PARKSQCAFE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EE-BrightBox-qykm4y]] (600 root)
[connection] id=EE-BrightBox-qykm4y | type=wifi
[wifi] ssid=EE-BrightBox-qykm4y | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR52]] (600 root)
[connection] id=NETGEAR52 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR52
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Bizspace]] (600 root)
[connection] id=Bizspace | type=wifi
[wifi] ssid=Bizspace | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BTHub5-F5TS]] (600 root)
[connection] id=BTHub5-F5TS | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=BTHub5-F5TS
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OnTheBeachGuestAccess]] (600 root)
[connection] id=OnTheBeachGuestAccess | type=wifi
[wifi] ssid=OnTheBeachGuestAccess | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PlusnetWirelessB44F44]] (600 root)
[connection] id=PlusnetWirelessB44F44 | type=wifi
[wifi] ssid=PlusnetWirelessB44F44 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TBO]] (600 root)
[connection] id=TBO | type=wifi
[wifi] ssid=TBO | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/rubyacademy]] (600 root)
[connection] id=rubyacademy | type=wifi
[wifi] ssid=rubyacademy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OTB]] (600 root)
[connection] id=OTB | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=OTB
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PlusnetWireless40AE25]] (600 root)
[connection] id=PlusnetWireless40AE25 | type=wifi
[wifi] ssid=PlusnetWireless40AE25 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OTB Guest]] (600 root)
[connection] id=OTB Guest | type=wifi
[wifi] ssid=OTB Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp0s20u1c4i2  no frequency information.


docker0   no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s20u1c4i2  Interface doesn't support scanning.


docker0   Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x155a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (r8152)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"


##### dmesg #############################


[    8.083026] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-216f.hcd failed with error -2
[    8.083030] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-216f.hcd not found
[    8.663606] ipheth 3-1:4.2 enp0s20u1c4i2: renamed from eth0
[    9.041156] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1c4i2: link is not ready
[   10.191693] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready


########## wireless info END ############



```

Any help, gratefully received, Thanks.

---

### Post by praseodym on 2016-06-26
Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11_all.deb)

Installation:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo dpkg -i ~/Downloads/*.deb
```
Reboot

---

### Post by vimothy on 2016-06-27
Thanks.

When I reboot, I get a dialogue box saying "Perform MOK Management". I select "continue boot". Still no wifi.

---

### Post by vimothy on 2016-06-27
Just ran both commands again. My computer does not automatically reboot, which I guess was supposed to happen.

Here's the terminal output (note that '[COLOR=#000000][FONT=&amp]bcmwl-kernel-source' is not installed)[/FONT][/COLOR]:

```
&#10140;  ~ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for timothymillar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gir1.2-gconf-2.0 gksu libgksu2-0
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
&#10140;  ~ sudo dpkg -i ~/Downloads/*.deb
(Reading database ... 356012 files and directories currently installed.)
Preparing to unpack .../Downloads/atom-amd64.deb ...
Unpacking atom (1.0.19) over (1.0.19) ...
Preparing to unpack .../broadcom-sta-dkms_6.30.223.271-2_all.deb ...


-------- Uninstall Beginning --------
Module:  broadcom-sta
Version: 6.30.223.271
Kernel:  4.4.0-24-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-24-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


Backing up initrd.img-4.4.0-24-generic to /boot/initrd.img-4.4.0-24-generic.old-dkms
Making new initrd.img-4.4.0-24-generic
(If next boot fails, revert to initrd.img-4.4.0-24-generic.old-dkms image)
update-initramfs....


DKMS: uninstall completed.


------------------------------
Deleting module version: 6.30.223.271
completely from the DKMS tree.
------------------------------
Done.
Unpacking broadcom-sta-dkms (6.30.223.271-2) over (6.30.223.271-2) ...
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11) over (2.2.0.3-2ubuntu11) ...
Preparing to unpack .../dropbox_2015.10.28_amd64.deb ...
Unpacking dropbox (2015.10.28) over (2015.10.28) ...
dpkg: warning: downgrading pandoc from 1.16.0.2~dfsg-1 to 1.15.1-1
Preparing to unpack .../pandoc-1.15.1-1-amd64.deb ...
Unpacking pandoc (1.15.1-1) over (1.16.0.2~dfsg-1) ...
dpkg-deb: error: '/home/timothymillar/Downloads/redis-server_2.0.1-2_amd64.deb' is not a debian format archive
dpkg: error processing archive /home/timothymillar/Downloads/redis-server_2.0.1-2_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Selecting previously unselected package ubuntu-tweak.
Preparing to unpack .../ubuntu-tweak_0.8.7-1-trusty2_all.deb ...
Unpacking ubuntu-tweak (0.8.7-1~trusty2) ...
Setting up atom (1.0.19) ...
Setting up dkms (2.2.0.3-2ubuntu11) ...
Setting up dropbox (2015.10.28) ...
Please restart all running instances of Nautilus, or you will experience problems. i.e. nautilus --quit
Dropbox installation successfully completed! You can start Dropbox from your applications menu.
Setting up pandoc (1.15.1-1) ...
dpkg: dependency problems prevent configuration of ubuntu-tweak:
 ubuntu-tweak depends on gir1.2-vte-2.90; however:
  Package gir1.2-vte-2.90 is not installed.


dpkg: error processing package ubuntu-tweak (--install):
 dependency problems - leaving unconfigured
Setting up broadcom-sta-dkms (6.30.223.271-2) ...
Loading new broadcom-sta-6.30.223.271 DKMS files...
Building only for 4.4.0-24-generic
Building initial module for 4.4.0-24-generic
Done.


wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-24-generic/updates/dkms/


depmod....


Backing up initrd.img-4.4.0-24-generic to /boot/initrd.img-4.4.0-24-generic.old-dkms
Making new initrd.img-4.4.0-24-generic
(If next boot fails, revert to initrd.img-4.4.0-24-generic.old-dkms image)
update-initramfs....


DKMS: install completed.
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160523-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-24-generic
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Errors were encountered while processing:
 /home/timothymillar/Downloads/redis-server_2.0.1-2_amd64.deb
 ubuntu-tweak

```

---

### Post by arekszklarczyk on 2016-07-06
Thanks! It worked for me - first time Ubuntu 16.04/Win10 dual boot on Lenovo ThinkPad 430. Best. A

---

### Post by Randyman99 on 2016-09-05
I had the same problem , but with a Realtek USB WIFI adapter. I was able to solve it, but then with another kernel update again last week, it broke again. Now I have it solved again, and hopefully with a procedure that will continue to work with future kernel updates and upgrades. It turns out that the module (driver) needs to be rebuilt for the current kernel. I was able to dig around and find that my current module was built for the previous kernel. I could not rebuild it and reinstall it without first removing the module from the kernel, and for good measure, deleting the source directory (only the object files are an issue, but why use a rifle when a shotgun will work?). See this page where I discuss my steps, and see if you can adapt it to your problem with your wifi adapter.
[URL="http://askubuntu.com/questions/777696/xubuntu-wifi-driver-not-working-after-update/813683#813683"]
http://askubuntu.com/questions/777696/xubuntu-wifi-driver-not-working-after-update/813683#813683[/URL]

---

### Post by UbuntuWho on 2017-01-28
Hey everyone. I keep getting "docker0" in my network connections list each time I reboot. I don't even know what a "docker0" is, nor do I have one set up. It interferes with me connecting via wifi. How do I keep this from appearing?

---

