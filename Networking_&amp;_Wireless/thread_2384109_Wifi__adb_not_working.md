---
title: "Wifi / adb not working"
date: 2018-02-02
forum: Networking &amp; Wireless
---

### Post by GirishSharma on 2018-02-02
Hello,
I am using Ubuntu 16.04 LTS 64 bit machine. Just before few minutes, I was using internet by WiFi receiver which is working on my friend's windows machine. I don't have any other option to say apt-get install neither by my android device (adb) nor by device's hotspot. I tried to solve by other links, but I found some commands in this regard, so I am posting those outputs for your reference please :

```
girish@gk:~$ sudo lshw -class network
[sudo] password for girish: 
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 00
       serial: 60:45:cb:a3:6f:8f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:130 memory:f7100000-f711ffff
girish@gk:~$ rfkill list
girish@gk:~$ lspci -nn | grep -i network
girish@gk:~$ lsmod | grep -e wmi -e acpi rfkill list all
grep: rfkill: No such file or directory
grep: list: No such file or directory
grep: all: No such file or directory
girish@gk:~$ lsmod | grep -e wmi -e acpi
mxm_wmi                16384  0
wmi                    24576  1 mxm_wmi
girish@gk:~$ iwconfig
lo        no wireless extensions.

enp0s31f6  no wireless extensions.

girish@gk:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

girish@gk:~$ lspci -n
00:00.0 0600: 8086:591f (rev 05)
00:02.0 0300: 8086:5912 (rev 04)
00:14.0 0c03: 8086:a2af
00:16.0 0780: 8086:a2ba
00:17.0 0106: 8086:a282
00:1b.0 0604: 8086:a2e7 (rev f0)
00:1c.0 0604: 8086:a290 (rev f0)
00:1c.2 0604: 8086:a292 (rev f0)
00:1c.4 0604: 8086:a294 (rev f0)
00:1d.0 0604: 8086:a298 (rev f0)
00:1f.0 0601: 8086:a2c5
00:1f.2 0580: 8086:a2a1
00:1f.3 0403: 8086:a2f0
00:1f.4 0c05: 8086:a2a3
00:1f.6 0200: 8086:15b8
03:00.0 0604: 1b21:1080 (rev 04)
05:00.0 0c03: 1b21:1242
girish@gk:~$ 

```
Kindly help me, and ask if you need any further info. Before the issue, all was working fine after saying this command because my virtual box not working so I said :

```
sudo apt-get install -reinstall virtualbox-dkms
```

After this command wifi/adb etc. all stopped.

---

### Post by wildmanne39 on 2018-02-02
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

You mentioned virtualbox but your Ubuntu is not running in virtualbox correct? if it is not click on the wireless script in my signature and follow the directions in the link.

Thanks

---

### Post by GirishSharma on 2018-02-02
Thanks for your valuable reply. I am sorry to forget to apply code tags.
My host os is Ubuntu and running virtual box to run windows as guest os in it. All was working fine before when I tried to switch on a virtual pc, I got an error message saying something FATAL error which said to install virtualbox-dkms. It got installed and when I again tried to switch on virtual pc, Ubuntu got hanged without any error message. I powered off the pc and after reboot the pc neither virtual pc got started, rather WiFi too got stopped working. I first time saw this unexpected behaviour of Ubuntu on my brand new assembled 64 bit pc, anyway this is what nearby wifi issue.
Since, I have to go on a 4 day journey, I will try the script and post the results after 4 days, because even my daughter too is not having the knowledge to download, permission, run and paste the result.
I once again thank you.

---

### Post by GirishSharma on 2018-02-06
This is output of the script please :
```


########## wireless info START ##########

Report from: 07 Feb 2018 09:27 IST +0530

Booted last: 07 Feb 2018 00:00 IST +0530

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

lspci: Unable to load libkmod resources: error -12

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
	Kernel driver in use: e1000e

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 13ba:0018 PCPlay Barcode PCP-BCG4209
Bus 001 Device 004: ID 05c6:6764 Qualcomm, Inc. A0001 Phone [OnePlus One]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi                16384  0
wmi                    24576  1 mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f7100000-f7120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404832 (404.8 KB)  TX bytes:404832 (404.8 KB)

##### iwconfig ##########################

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root       801     1  0 09:13 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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

[[/etc/NetworkManager/system-connections/AndroidAP_5640]] (600 root)
[connection] id=AndroidAP_5640 | type=wifi | permissions=user:girish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP_5640
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/yu 6000]] (600 root)
[connection] id=yu 6000 | type=wifi | permissions=user:girish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=yu 6000
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

enp0s31f6  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s31f6  Interface doesn't support scanning.

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

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    1.188708] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    2.628466] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)

########## wireless info END ############



```

---

### Post by GirishSharma on 2018-02-07
Any update please.

---

### Post by wildmanne39 on 2018-02-07
Is the file you posted the complete file? there is a lot of information that is not filled in, lspci does not even show your wireless device.

Is the device an internal device?

Please post the outptut of:
```
lspci -nnk | grep -iA2 net
```
we will see if we get the same error message running the command this way.

Thanks

---

### Post by GirishSharma on 2018-02-07
Yes please, file is complete and device is internal. I just used to connect to the internet by only hotspot of my smartphone and in 5-7 seconds it used to connect. Here is output of command:

```

girish@gk:~$ lspci -nnk | grep -iA2 net
lspci: Unable to load libkmod resources: error -12
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
	Kernel driver in use: e1000e
03:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 04)
girish@gk:~$ 

```

I came to know that this error is belong to chrooting. Even I tried to choot the system by some commands and choot /mntri /bin/bash (without any error), but networking is not coming up.

Thanks again for your continued help.

---

### Post by wildmanne39 on 2018-02-07
Please run:
```
sudo apt install --reinstall linux-headers-$(uname -r)
```
watch for errors, when the command is finished running reboot and let us know if wifi comes on, if not please run the wireless script again and post the results here.

Thanks

---

### Post by GirishSharma on 2018-02-07
Thanks again, but my problem is I am not able to connect the pc to internet, neither by my phone (thetering) nor by any other mean. So, will the above command work without internet please?

---

### Post by wildmanne39 on 2018-02-07
No, I suggest you take the computer some where you can use an ethernet or tethered connection without one there is nothing I can do to help, maybe someone else has an idea, but it is almost impossible with an internet connection.

---

### Post by GirishSharma on 2018-02-07
Ok, I will try to take the pc to the shop from which I assembled it, but I think there too I will face the problem of network, because I feel that there may something corruption happened at hardware level with PCI card. Problem is, in the pc networking is not coming up, but anyway I will take the pc to the shop and will let you know, what happens there. Please keep in touch with the thread.

---

### Post by GirishSharma on 2018-02-08
Now, I am sending this message from the shop using its wired connection.

Here is output of last command :
```

girish@gk:~$ sudo apt install --reinstall linux-headers-$(uname -r)
[sudo] password for girish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-28 linux-headers-4.10.0-28-generic linux-headers-4.10.0-38
  linux-headers-4.10.0-38-generic linux-headers-4.10.0-40 linux-headers-4.10.0-40-generic
  linux-image-4.10.0-28-generic linux-image-4.10.0-38-generic linux-image-4.10.0-40-generic
  linux-image-extra-4.10.0-28-generic linux-image-extra-4.10.0-38-generic
  linux-image-extra-4.10.0-40-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 101 not upgraded.
Need to get 699 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.13.0-32-generic amd64 4.13.0-32.35~16.04.1 [699 kB]
Fetched 699 kB in 2s (261 kB/s)                          
(Reading database ... 321211 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.13.0-32-generic_4.13.0-32.35~16.04.1_amd64.deb ...
Unpacking linux-headers-4.13.0-32-generic (4.13.0-32.35~16.04.1) over (4.13.0-32.35~16.04.1) ...
Setting up linux-headers-4.13.0-32-generic (4.13.0-32.35~16.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
girish@gk:~$ 

```

Reboted the PC, but still wireless not coming up.

As you suggested to run wireless script, here is output please :

```


########## wireless info START ##########

Report from: 08 Feb 2018 11:06 IST +0530

Booted last: 08 Feb 2018 00:00 IST +0530

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

lspci: Unable to load libkmod resources: error -12

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 001 Device 002: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi                16384  0
wmi                    24576  1 mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF1]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::adbb:f827:2490:e8d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6135 (6.1 KB)  TX bytes:17248 (17.2 KB)
          Interrupt:16 Memory:f7100000-f7120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20475 (20.4 KB)  TX bytes:20475 (20.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp0s31f6
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s31f6
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s31f6

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       803     1  0 11:03 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       50db91ff-b4d9-337f-8ac3-1441f314acec
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   50db91ff-b4d9-337f-8ac3-1441f314acec | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = TP-LINK
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        ip_address = 192.168.1.2
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
DHCP4.OPTION[20]:                       expiry = 1518327346
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc0
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::adbb:f827:2490:e8d0/64
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

[[/etc/NetworkManager/system-connections/AndroidAP_5640]] (600 root)
[connection] id=AndroidAP_5640 | type=wifi | permissions=user:girish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AndroidAP_5640
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/yu 6000]] (600 root)
[connection] id=yu 6000 | type=wifi | permissions=user:girish:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=yu 6000
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] bssid=<MAC address> | mac-address=00:E1:29:00:F6:94 | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

enp0s31f6  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

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

[    1.219815] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) <MAC 'enp0s31f6' [IF1]>
[    1.219816] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.219923] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    1.220316] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[    1.237912] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    1.854711] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[    2.595471] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    5.399249] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.399250] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[    5.399297] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
[   94.579211] e1000e: enp0s31f6 NIC Link is Down
[  167.528145] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  167.528152] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO

########## wireless info END ############

```

---

### Post by wildmanne39 on 2018-02-08
There is something wrong with that kernel, I hope you left a couple of old kernels installed, reboot and go into grub and select the last kernel that you know the wifi worked on that should get wifi working.

---

### Post by GirishSharma on 2018-02-08
> **wildmanne39 said:**
> There is something wrong with that kernel, I hope you left a couple of old kernels installed, reboot and go into grub and select the last kernel that you know the wifi worked on that should get wifi working.

Will you please tell me the complete steps of grub and install correct kernel. How do I know that this kernel is working for wifi.

---

### Post by wildmanne39 on 2018-02-08
Reboot the computer then quickly press and hold the Shift key, which will bring up the GNU GRUB menu. (If you see the Ubuntu logo, you've missed the point where you can enter the GRUB menu.)

It is possible that your kernel is missing the extra package but I do not think you would have that error in your lspci from that.

We need to find out if booting an older kernel works before we go into trying to install a new kernel.

It is late here so I am going to be getting off line pretty soon but report back and let us know if the older kernel works from the grub menu.

---

### Post by GirishSharma on 2018-02-08
> **wildmanne39 said:**
> Reboot the computer then quickly press and hold the Shift key, which will bring up the GNU GRUB menu. (If you see the Ubuntu logo, you've missed the point where you can enter the GRUB menu.)

It is possible that your kernel is missing the extra package but I do not think you would have that error in your lspci from that.

We need to find out if booting an older kernel works before we go into trying to install a new kernel.

It is late here so I am going to be getting off line pretty soon but report back and let us know if the older kernel works from the grub menu.

But sir, I am noob, I don't know the commands and steps to install old / working kernel from grub menu.

---

### Post by wildmanne39 on 2018-02-08
You do not have to install a kernel in the grub menu, as I said you boot into the grub menu and there will be some old kernels there then you just select one to boot from. You can refer to my previous post for directions how to get into the grub menu.

---

### Post by GirishSharma on 2018-02-08
Yes, I think its due to dual installed kernels. I booted the pc from old kernel something 4.10.... generic, I am missing its long entry and I saw the wireless connections, but when I reboot the pc, again it botted in new kernel. How do I reboot the pc with old kernel without going into grub.

---

### Post by wildmanne39 on 2018-02-08
You have to go into the grub to boot the old kernel, wifi connects in the old kernel?

We can see if we can fix the new kernel tomorrow but it is to late for me to get into that here tonight.

I do not know why that kernel is installed, 16.04 comes with 4.10 kernel, it could be that HWE upgrade it.

---

### Post by GirishSharma on 2018-02-08
Problem solved ... !

I just booted the pc with 4.10 kernel, it showed me wifi connections and worked fine.  I just rebooted the pc and this time it got 4.32 kernel, and this time too wifi connections visible and working. I don't know how and why just booting the pc with working kernel solved the problem.

I am really thankful to you for your kind and continue support.  God Bless You ...

---

### Post by wildmanne39 on 2018-02-08
I am glad it is now working!

Enjoy!

---

