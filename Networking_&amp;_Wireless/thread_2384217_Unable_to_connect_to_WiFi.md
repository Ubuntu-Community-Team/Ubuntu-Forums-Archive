---
title: "Unable to connect to WiFi"
date: 2018-02-03
forum: Networking &amp; Wireless
---

### Post by joecitizien on 2018-02-03
Hello,

I am unable to connect to the Internet using WiFi on my PC. There's no option to "enable wifi" in the drop-down menu. I am, however, able to use a wired connection. 

I have never had this problem on this PC before - WiFi has always worked in the past. I haven't recently upgraded to a new version of Ubuntu or anything. 

Anyone have any suggestions about how I can go about resolving this issue? Thank you!

Best,

Joe

---

### Post by Autodave on 2018-02-03
Wifi adapter died?  Is this a desktop or laptop?

If laptop, here is something easy to try and I am always amazed at how many times I have fixed a laptop by doing this:

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

If a desktop, have you ti\ried rebooting?

---

### Post by Hadaka on 2018-02-03
hi please try..
[COLOR=#242729][FONT=Arial]```
[/FONT][/COLOR]sudo systemctl restart network[COLOR=#242729][FONT=Arial]
```[/FONT][/COLOR]

---

### Post by joecitizien on 2018-02-04
Hi there,

I'm using a desktop, not a laptop. 

I tried that command and this was the response: 

Failed to restart network.service: Unit network.service not found.

---

### Post by jeremy31 on 2018-02-04
See the wireless script link in my signature and post results

---

### Post by joecitizien on 2018-02-04
> **jeremy31 said:**
> See the wireless script link in my signature and post results

Here are the results

```

########## wireless info START ##########

Report from: 04 Feb 2018 17:40 EST -0500

Booted last: 04 Feb 2018 00:00 EST -0500

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection [1043:85f0]
    Kernel driver in use: igb

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 258a:0001  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2604:2000:d0a1:d400:2c8c:300b:c912:7808/64 Scope:Global
          inet6 addr: 2601:241:300:f18b::1d96/128 Scope:Global
          inet6 addr: 2604:2000:d0a1:d400:c228:17a0:1450:d4c3/64 Scope:Global
          inet6 addr: fe80::7768:7b2d:c4ea:6bf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:714795 (714.7 KB)  TX bytes:262527 (262.5 KB)
          Memory:fe700000-fe71ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:44421 (44.4 KB)  TX bytes:44421 (44.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp4s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0

##### resolv.conf #######################

nameserver 127.0.1.1
search nyc.rr.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       888     1  0 17:37 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        I211 Gigabit Network Connection
GENERAL.DRIVER:                         igb
GENERAL.DRIVER-VERSION:                 5.3.0-k
GENERAL.FIRMWARE-VERSION:                0. 6-1
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       affb37e2-706d-3507-a4cd-217bbdaa0293
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   affb37e2-706d-3507-a4cd-217bbdaa0293 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.6/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.62
IP4.DNS[2]:                             209.18.47.61
IP4.DOMAIN[1]:                          nyc.rr.com
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 209.18.47.62 209.18.47.61
DHCP4.OPTION[5]:                        ip_address = 192.168.0.6
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = nyc.rr.com
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1517787484
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2601:241:300:f18b::1d96/128
IP6.ADDRESS[2]:                         2604:2000:d0a1:d400:2c8c:300b:c912:7808/64
IP6.ADDRESS[3]:                         2604:2000:d0a1:d400:c228:17a0:1450:d4c3/64
IP6.ADDRESS[4]:                         fe80::7768:7b2d:c4ea:6bf2/64
IP6.GATEWAY:                            fe80::5613:79ff:fef2:4d3c
IP6.ROUTE[1]:                           dst = 2604:2000:d0a1:d400::/56, nh = fe80::5613:79ff:fef2:4d3c, mt = 100

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

##### Netplan config ####################

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

lo        no frequency information.

enp4s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp4s0    Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl819cu.conf]
blacklist rtl8192cu

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.319724] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready (repeated 2 times)
[    7.310597] igb 0000:04:00.0 enp4s0: igb: enp4s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[    7.310792] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready

########## wireless info END ############

```

---

### Post by wildmanne39 on 2018-02-04
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2018-02-04
Please do:
```
sudo modprobe -v rtl8192cu
```
watch for errors, does it come on? if so we will need to unblacklist that driver.

---

### Post by joecitizien on 2018-02-04
> **wildmanne39 said:**
> Please do:
```
sudo modprobe -v rtl8192cu
```
watch for errors, does it come on? if so we will need to unblacklist that driver.

Here are the results

```
insmod /lib/modules/4.4.0-112-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
insmod /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko 
insmod /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko 
insmod /lib/modules/4.4.0-112-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko 

```

---

### Post by wildmanne39 on 2018-02-04
Did the wifi come on?

---

### Post by joecitizien on 2018-02-04
> **wildmanne39 said:**
> Did the wifi come on?

No, it did not unfortunately. I still do not have an "enable wifi" option in the menu.

---

### Post by wildmanne39 on 2018-02-04
While the driver is loaded, this means before you reboot your computer please run the wireless script again and post the results so we can see what is happening while the driver is loaded.

Thanks

---

### Post by joecitizien on 2018-02-04
> **wildmanne39 said:**
> While the driver is loaded, this means before you reboot your computer please run the wireless script again and post the results so we can see what is happening while the driver is loaded.

Thanks

Here's the script again. I have not rebooted. 

```

########## wireless info START ##########

Report from: 04 Feb 2018 17:40 EST -0500

Booted last: 04 Feb 2018 00:00 EST -0500

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection [1043:85f0]
    Kernel driver in use: igb

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 258a:0001  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  40960  1 asus_wmi
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2604:2000:d0a1:d400:2c8c:300b:c912:7808/64 Scope:Global
          inet6 addr: 2601:241:300:f18b::1d96/128 Scope:Global
          inet6 addr: 2604:2000:d0a1:d400:c228:17a0:1450:d4c3/64 Scope:Global
          inet6 addr: fe80::7768:7b2d:c4ea:6bf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:714795 (714.7 KB)  TX bytes:262527 (262.5 KB)
          Memory:fe700000-fe71ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:44421 (44.4 KB)  TX bytes:44421 (44.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp4s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp4s0

##### resolv.conf #######################

nameserver 127.0.1.1
search nyc.rr.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root       888     1  0 17:37 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        I211 Gigabit Network Connection
GENERAL.DRIVER:                         igb
GENERAL.DRIVER-VERSION:                 5.3.0-k
GENERAL.FIRMWARE-VERSION:                0. 6-1
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       affb37e2-706d-3507-a4cd-217bbdaa0293
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   affb37e2-706d-3507-a4cd-217bbdaa0293 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.6/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             209.18.47.62
IP4.DNS[2]:                             209.18.47.61
IP4.DOMAIN[1]:                          nyc.rr.com
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 209.18.47.62 209.18.47.61
DHCP4.OPTION[5]:                        ip_address = 192.168.0.6
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = nyc.rr.com
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1517787484
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         2601:241:300:f18b::1d96/128
IP6.ADDRESS[2]:                         2604:2000:d0a1:d400:2c8c:300b:c912:7808/64
IP6.ADDRESS[3]:                         2604:2000:d0a1:d400:c228:17a0:1450:d4c3/64
IP6.ADDRESS[4]:                         fe80::7768:7b2d:c4ea:6bf2/64
IP6.GATEWAY:                            fe80::5613:79ff:fef2:4d3c
IP6.ROUTE[1]:                           dst = 2604:2000:d0a1:d400::/56, nh = fe80::5613:79ff:fef2:4d3c, mt = 100

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

##### Netplan config ####################

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

lo        no frequency information.

enp4s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp4s0    Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl819cu.conf]
blacklist rtl8192cu

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.319724] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready (repeated 2 times)
[    7.310597] igb 0000:04:00.0 enp4s0: igb: enp4s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[    7.310792] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready

########## wireless info END ############
```

Shall I reboot?

---

### Post by jeremy31 on 2018-02-04
Are you sure you have a wireless device installed?  I do not see one, if it is USB I would switch ports and I would switch slots if it is PCI

---

### Post by joecitizien on 2018-02-04
> **jeremy31 said:**
> Are you sure you have a wireless device installed?  I do not see one, if it is USB I would switch ports and I would switch slots if it is PCI

Yes, I've been able to use wireless on this computer before. It must be PCI - I've never had a wireless adapter plugged into a USB port on this machine.

---

### Post by wildmanne39 on 2018-02-04
I thought this usb device was it.
```
258a:0001
```

---

### Post by joecitizien on 2018-02-04
> **wildmanne39 said:**
> I thought this usb device was it.
```
258a:0001
```

Is there a way to confirm that? Is a USB device always plugged into an external port, or are they also internal? I have no wireless device plugged into an external port, never did when wireless was working.

---

### Post by wildmanne39 on 2018-02-04
There is only very rare cases where an internal device is seen as an usb device and I think that is only on real old computers but I am not sure about that, Jeremy31 has more recent experience in wireless issues so I am going to back out and let him take over.

---

### Post by joecitizien on 2018-02-04
Hm, well, not sure what to do. Anyone have any ideas? 
Would this device also enable wireless, or is it strictly for a wired connection? 

Intel Corporation I211 Gigabit Network Connection

---

### Post by wildmanne39 on 2018-02-04
It is your wired connection only.

You can go into the bios and see if wireless is enabled, if you are using the legacy bios you can reset it and see if that helps, it looks like the wifi card could be defective.

If this is a laptop you can take the battery out for 30 minutes then put it back in and see if that helps.

Your wifi card is not showing up at all, I was wrong earlier.

What brand of computer is this?

---

### Post by Hadaka on 2018-02-05
Hi, you state..
"WiFi has always worked in the past. I haven't recently upgraded to a new version of Ubuntu or anything."
and your wireless report as jeremy31 and wildmanne39 both posted , there appears to be no wifi card present.
Let's see if we can determine if the wifi card has failed or perhaps the wifi card slot or a possible kernel update
is causing issues. First try 
booting to an earlier kernel.
1. Power down the computer then power back up while holding down the 'shift' key
2. from the grub menu ..choose an earlier kernel and boot up to it
3.test wireless

#Hardware
1. re-seat the wifi card in it's current slot and test (check antenna connections)
2. move card to a different card slot..if possible
3.test wireless
Thanks.

*If it still fails..it is likely the card is defective and should be removed and replaced.

---

### Post by the.fallen.one on 2018-02-06
[INDENT] 					Hey jeremy31, i am a complete noob to linux and know nothing but  want to learn everything. I had installed mint cinnamon 18.3 but it had  this very slow wi fi connection( was getting 0.30mbps down speed on  speed test) but had exact speed on ethernet(25MBps) so i shifted to  ubuntu which i wanted to do eventually after learning mint which i  reserched as the basics. but the problem still persists and after  searching through forums a was able to get some sort of solution by  running clone from github of the realtek driver. Before i run that  script wi fi was very slow but now its completely not even detecting the  network. i ran the above scrpits too but to no avail. If you could help  me and teach me whats is wrong that i'm doing, i'd be really grateful  to you sir. 				[/INDENT]

---

### Post by wildmanne39 on 2018-02-06
Hello and welcome to the forum the.fallen.one please do not hijack someone else's thread or create more then one post on the same topic, it is considered rude and you will get the best help by creating your own thread.

Thanks

---

