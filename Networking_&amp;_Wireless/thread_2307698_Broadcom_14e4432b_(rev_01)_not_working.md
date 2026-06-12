---
title: "Broadcom 14e4:432b (rev 01) not working"
date: 2015-12-27
forum: Networking &amp; Wireless
---

### Post by metheon on 2015-12-27
Hi.

I have tried various drives without luck, including bcmwl-kernel-source from the broadcom guide (rev 01 is not in the list). The computer is a MacBook Pro 7.1 with a freshly installed Ubuntu 15.10 (disregarding a few wifi driver install attempts). Best result so far is getting the wifi interface but unable to show any of the 30 or so wifi hotspots within range. In the cases with a working wifi interface an 'iwlist wlan0 scan' yielded 'unable to scan' or something to that effect.

Linux newbie so please be gentle :)

Here is the output from the script:

```

########## wireless info START ##########

Report from: 27 Dec 2015 22:12 CET +0100

Booted last: 27 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.0.21  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10854849 (10.8 MB)  TX bytes:878758 (878.7 KB)
          Interrupt:20 

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
search webspeed.dk

##### network managers ##################

Installed:

    NetworkManager

Running:

root       740     1  0 21:40 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       9776bdc4-7a5a-43cf-ac9d-afeb3e04967b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9776bdc4-7a5a-43cf-ac9d-afeb3e04967b | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.21/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
IP4.DOMAIN[1]:                          webspeed.dk
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1451335472
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       domain_name = webspeed.dk
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.21
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       domain_name_servers = 8.8.4.4 8.8.4.4
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0' [IF]>/64
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

##### iw reg get ########################

Region: Europe/Copenhagen (based on set time zone)

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

[   12.945393] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.133154] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   13.472223] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.474154] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   14.321812] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.728085] b43-phy0 ERROR: DMA RX reset timed out
[   60.912059] b43-phy0 ERROR: DMA TX reset timed out
[   60.931412] ssb: Timeout waiting for bitmask 01800000 on register 0F90 to clear.
[   61.624082] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   61.912147] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  108.782403] tg3 0000:03:00.0 enp3s0: Link is up at 1000 Mbps, full duplex
[  108.782439] tg3 0000:03:00.0 enp3s0: Flow control is off for TX and off for RX
[  108.782484] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  115.876006] tg3 0000:03:00.0 enp3s0: Link is down
[  197.468201] b43-phy0 ERROR: DMA RX reset timed out
[  197.652241] b43-phy0 ERROR: DMA TX reset timed out
[  197.671719] ssb: Timeout waiting for bitmask 01800000 on register 0F90 to clear.
[  200.016102] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  200.320331] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  235.133488] tg3 0000:03:00.0 enp3s0: Link is up at 1000 Mbps, full duplex
[  235.133530] tg3 0000:03:00.0 enp3s0: Flow control is off for TX and off for RX
[ 1181.736098] b43-phy0 ERROR: DMA RX reset timed out
[ 1181.920131] b43-phy0 ERROR: DMA TX reset timed out
[ 1181.939685] ssb: Timeout waiting for bitmask 01800000 on register 0F90 to clear.
[ 1182.172370] ssb: Found chip with id 0x4322, rev 0x01 and package 0x0A
[ 1182.172390] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x17, vendor 0x4243)
[ 1182.172402] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x10, vendor 0x4243)
[ 1182.172414] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x0B, vendor 0x4243)
[ 1182.172425] ssb: Core 3 found: PCI (cc 0x804, rev 0x0E, vendor 0x4243)
[ 1182.172436] ssb: Core 4 found: USB 2.0 Device (cc 0x81A, rev 0x05, vendor 0x4243)
[ 1182.172447] ssb: Core 5 found: UNKNOWN (cc 0x8FF, rev 0x00, vendor 0x4243)
[ 1182.172458] ssb: Core 6 found: Internal Memory (cc 0x80E, rev 0x03, vendor 0x4243)
[ 1182.229375] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[ 1182.274403] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[ 1182.304523] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[ 1182.304557] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[ 1182.316556] b43 ssb0:0: Direct firmware load for b43/ucode16_mimo.fw failed with error -2 (repeated 2 times)
[ 1182.316711] b43 ssb0:0: Direct firmware load for b43-open/ucode16_mimo.fw failed with error -2 (repeated 2 times)
[ 1182.316768] b43-phy0 ERROR: Firmware file "b43/ucode16_mimo.fw" not found
[ 1182.316775] b43-phy0 ERROR: Firmware file "b43-open/ucode16_mimo.fw" not found
[ 1182.316781] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

########## wireless info END ############

```

---

### Post by Hadaka on 2015-12-27
Hi,from a working wired connection, please COPY and paste.
#Set country code:
```
sudo iw reg set DK
sudo sed -i 's/^REG.*=$/&DK/' /etc/default/crda
```
#Verify your country code..change if not correct..'left side list'
[URL="http://www.osb.org/geog/countrycodes.html"]http://www.osb.org/geog/countrycodes.html
[/URL]
#Load current updates to Ubuntu 15.10:
```
sudo apt-get update
sudo apt-get dist-upgrade
#sudo apt get dist-upgrade does not upgrade you to the next load. It upgrades, brings up to date your currently loaded packages
```
#Ubuntu Linux Education:
[URL="http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade"]http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade
[/URL]
#Remove incorrect wifi driver module:
```
sudo modprobe -rf b43
sudo modprobe -rf ssb
```
#Blacklist incorrect wifi modules:
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
#Ignore if not found:
```
sudo apt-get remove --purge bcmwl-kernel-source
```
#Load correct wifi driver module:
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -v wl
```
#Clean up:
```
sudo apt-get autoremove
sudo apt-get autoclean
```
*Remove wired connection-test wireless

---

### Post by metheon on 2015-12-28
Hello Hadaka :) Thank you for giving this a go.

Here is the terminal output from running all your commands.

```

metheon@ubuntu-mbp:~$ sudo iw reg set DK
[sudo] password for metheon:
metheon@ubuntu-mbp:~$ sudo sed -i 's/^REG.*=$/&DK/' /etc/default/crda
metheon@ubuntu-mbp:~$ sudo apt-get update
Hit http://dk.archive.ubuntu.com wily InRelease
Hit http://dk.archive.ubuntu.com wily-updates InRelease
Hit http://dk.archive.ubuntu.com wily-backports InRelease        
Hit http://security.ubuntu.com wily-security InRelease           
Hit http://dk.archive.ubuntu.com wily/main Sources
Hit http://dk.archive.ubuntu.com wily/restricted Sources       
Hit http://dk.archive.ubuntu.com wily/universe Sources         
Hit http://dk.archive.ubuntu.com wily/multiverse Sources       
Hit http://dk.archive.ubuntu.com wily/main amd64 Packages        
Hit http://dk.archive.ubuntu.com wily/restricted amd64 Packages  
Hit http://dk.archive.ubuntu.com wily/universe amd64 Packages    
Hit http://dk.archive.ubuntu.com wily/multiverse amd64 Packages  
Hit http://security.ubuntu.com wily-security/main Sources        
Hit http://dk.archive.ubuntu.com wily/main i386 Packages         
Hit http://dk.archive.ubuntu.com wily/restricted i386 Packages   
Hit http://dk.archive.ubuntu.com wily/universe i386 Packages     
Hit http://dk.archive.ubuntu.com wily/multiverse i386 Packages   
Hit http://security.ubuntu.com wily-security/restricted Sources  
Hit http://dk.archive.ubuntu.com wily/main Translation-en        
Hit http://dk.archive.ubuntu.com wily/multiverse Translation-en  
Hit http://dk.archive.ubuntu.com wily/restricted Translation-en  
Hit http://security.ubuntu.com wily-security/universe Sources    
Hit http://security.ubuntu.com wily-security/multiverse Sources  
Hit http://dk.archive.ubuntu.com wily/universe Translation-en    
Hit http://dk.archive.ubuntu.com wily-updates/main Sources    
Hit http://security.ubuntu.com wily-security/main amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/restricted Sources
Hit http://dk.archive.ubuntu.com wily-updates/universe Sources
Hit http://dk.archive.ubuntu.com wily-updates/multiverse Sources
Hit http://dk.archive.ubuntu.com wily-updates/main amd64 Packages
Hit http://security.ubuntu.com wily-security/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/universe amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com wily-security/universe amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/main i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/restricted i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/universe i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/multiverse i386 Packages
Hit http://security.ubuntu.com wily-security/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/main Translation-en
Hit http://dk.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://dk.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://security.ubuntu.com wily-security/main i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/main Sources     
Hit http://security.ubuntu.com wily-security/restricted i386 Packages
Hit http://security.ubuntu.com wily-security/universe i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/restricted Sources
Hit http://dk.archive.ubuntu.com wily-backports/universe Sources
Hit http://dk.archive.ubuntu.com wily-backports/multiverse Sources
Hit http://dk.archive.ubuntu.com wily-backports/main amd64 Packages
Hit http://security.ubuntu.com wily-security/multiverse i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com wily-backports/universe amd64 Packages
Hit http://dk.archive.ubuntu.com wily-backports/multiverse amd64 Packages
Hit http://security.ubuntu.com wily-security/main Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/main i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/restricted i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/universe i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/multiverse i386 Packages
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/main Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/multiverse Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/restricted Translation-en
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/universe Translation-en
Hit http://security.ubuntu.com wily-security/universe Translation-en
Reading package lists... Done               
metheon@ubuntu-mbp:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
metheon@ubuntu-mbp:~$ sudo modprobe -rf b43
metheon@ubuntu-mbp:~$ sudo modprobe -rf ssb
metheon@ubuntu-mbp:~$ echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist b43
blacklist ssb
metheon@ubuntu-mbp:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
metheon@ubuntu-mbp:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,515 kB of archives.
After this operation, 8,012 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 210091 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu7_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu7) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu7) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-22-generic
Building for architecture x86_64
Building initial module for 4.2.0-22-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-22-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-22-generic
metheon@ubuntu-mbp:~$ sudo modprobe -v wl
metheon@ubuntu-mbp:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
metheon@ubuntu-mbp:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

And here I did the wifi debug script again.

```

########## wireless info START ##########

Report from: 28 Dec 2015 07:01 CET +0100

Booted last: 28 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              548864  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.0.21  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2954 (2.9 KB)  TX bytes:10055 (10.0 KB)
          Interrupt:20 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:75
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search webspeed.dk

##### network managers ##################

Installed:

    NetworkManager

Running:

root       751     1  0 06:58 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       96695da2-8a1e-4ab2-bb3c-92c1ad8408fb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   96695da2-8a1e-4ab2-bb3c-92c1ad8408fb | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.21/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
IP4.DOMAIN[1]:                          webspeed.dk
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1451368828
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       domain_name = webspeed.dk
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.21
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       domain_name_servers = 8.8.4.4 8.8.4.4
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

Region: Europe/Copenhagen (based on set time zone)

country DK: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
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

[   11.972714] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.980541] wl: module verification failed: signature and/or required key missing - tainting kernel
[   12.058544] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   12.066460] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   13.030761] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   13.037944] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   69.431873] ERROR @wl_dev_intvar_get : error (-1)
[  108.687977] tg3 0000:03:00.0 enp3s0: Link is up at 1000 Mbps, full duplex
[  108.688019] tg3 0000:03:00.0 enp3s0: Flow control is off for TX and off for RX
[  108.689454] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  152.715219] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

What's next? :)

---

### Post by jeremy31 on 2015-12-28
Try using this newer version, select a download site from
 [http://packages.ubuntu.com/xenial/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/xenial/amd64/bcmwl-kernel-source/download)

---

### Post by metheon on 2015-12-28
Hi Jeremy, thank you for your input. Tried your solution, but still no luck. :-/

Driver got upgraded from 6.30.223.248+bdcom-0ubuntu7 to bcmwl-kernel-source amd64 6.30.223.248+bdcom-0ubuntu8

Terminal output:

```

metheon@ubuntu-mbp:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 8,012 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 210169 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu7) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu7) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-22-generic
metheon@ubuntu-mbp:~$ sudo apt-get update
Hit http://security.ubuntu.com wily-security InRelease
Hit http://dk.archive.ubuntu.com wily InRelease
Hit http://security.ubuntu.com wily-security/main Sources
Hit http://dk.archive.ubuntu.com wily-updates InRelease     
Hit http://dk.archive.ubuntu.com wily-backports InRelease                
Get:1 http://dk.archive.ubuntu.com xenial InRelease [227 kB]             
Hit http://security.ubuntu.com wily-security/restricted Sources
Hit http://security.ubuntu.com wily-security/universe Sources           
Hit http://security.ubuntu.com wily-security/multiverse Sources         
Hit http://security.ubuntu.com wily-security/main amd64 Packages        
Hit http://security.ubuntu.com wily-security/restricted amd64 Packages      
Hit http://security.ubuntu.com wily-security/universe amd64 Packages     
Hit http://security.ubuntu.com wily-security/multiverse amd64 Packages   
Hit http://security.ubuntu.com wily-security/main i386 Packages          
Hit http://security.ubuntu.com wily-security/restricted i386 Packages   
Hit http://security.ubuntu.com wily-security/universe i386 Packages     
Hit http://dk.archive.ubuntu.com wily/main Sources                        
Hit http://dk.archive.ubuntu.com wily/restricted Sources                                
Hit http://dk.archive.ubuntu.com wily/universe Sources                                  
Hit http://dk.archive.ubuntu.com wily/multiverse Sources                                
Hit http://dk.archive.ubuntu.com wily/main amd64 Packages          
Hit http://dk.archive.ubuntu.com wily/restricted amd64 Packages    
Hit http://dk.archive.ubuntu.com wily/universe amd64 Packages      
Hit http://dk.archive.ubuntu.com wily/multiverse amd64 Packages    
Hit http://dk.archive.ubuntu.com wily/main i386 Packages           
Hit http://dk.archive.ubuntu.com wily/restricted i386 Packages     
Hit http://dk.archive.ubuntu.com wily/universe i386 Packages       
Hit http://dk.archive.ubuntu.com wily/multiverse i386 Packages     
Hit http://dk.archive.ubuntu.com wily/main Translation-en          
Hit http://dk.archive.ubuntu.com wily/multiverse Translation-en    
Hit http://dk.archive.ubuntu.com wily/restricted Translation-en    
Hit http://dk.archive.ubuntu.com wily/universe Translation-en 
Hit http://dk.archive.ubuntu.com wily-updates/main Sources    
Hit http://dk.archive.ubuntu.com wily-updates/restricted Sources
Hit http://dk.archive.ubuntu.com wily-updates/universe Sources
Hit http://security.ubuntu.com wily-security/multiverse i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/multiverse Sources
Hit http://dk.archive.ubuntu.com wily-updates/main amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/universe amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com wily-updates/main i386 Packages  
Hit http://security.ubuntu.com wily-security/main Translation-en  
Hit http://dk.archive.ubuntu.com wily-updates/restricted i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/universe i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/multiverse i386 Packages
Hit http://dk.archive.ubuntu.com wily-updates/main Translation-en 
Hit http://dk.archive.ubuntu.com wily-updates/multiverse Translation-en
Hit http://dk.archive.ubuntu.com wily-updates/restricted Translation-en
Hit http://dk.archive.ubuntu.com wily-updates/universe Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/main Sources      
Hit http://dk.archive.ubuntu.com wily-backports/restricted Sources
Hit http://dk.archive.ubuntu.com wily-backports/universe Sources  
Hit http://dk.archive.ubuntu.com wily-backports/multiverse Sources
Hit http://dk.archive.ubuntu.com wily-backports/main amd64 Packages
Hit http://dk.archive.ubuntu.com wily-backports/restricted amd64 Packages
Hit http://dk.archive.ubuntu.com wily-backports/universe amd64 Packages
Hit http://dk.archive.ubuntu.com wily-backports/multiverse amd64 Packages
Hit http://dk.archive.ubuntu.com wily-backports/main i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/restricted i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/universe i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/multiverse i386 Packages
Hit http://dk.archive.ubuntu.com wily-backports/main Translation-en
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/multiverse Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/restricted Translation-en
Hit http://dk.archive.ubuntu.com wily-backports/universe Translation-en
Get:2 http://dk.archive.ubuntu.com xenial/main amd64 Packages [1,463 kB]
Hit http://security.ubuntu.com wily-security/restricted Translation-en      
Hit http://security.ubuntu.com wily-security/universe Translation-en        
Get:3 http://dk.archive.ubuntu.com xenial/restricted amd64 Packages [15.8 kB]                                                       
Get:4 http://dk.archive.ubuntu.com xenial/main i386 Packages [1,461 kB]                                                             
Get:5 http://dk.archive.ubuntu.com xenial/restricted i386 Packages [16.1 kB]                                                        
Get:6 http://dk.archive.ubuntu.com xenial/main Translation-en [848 kB]                                                              
Get:7 http://dk.archive.ubuntu.com xenial/restricted Translation-en [4,302 B]                                                       
Fetched 4,035 kB in 33s (122 kB/s)                                                                                                  
Reading package lists... Done
metheon@ubuntu-mbp:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 982 not upgraded.
Need to get 1,515 kB of archives.
After this operation, 8,013 kB of additional disk space will be used.
Get:1 http://dk.archive.ubuntu.com/ubuntu/ xenial/restricted bcmwl-kernel-source amd64 6.30.223.248+bdcom-0ubuntu8 [1,515 kB]
Fetched 1,515 kB in 15s (98.0 kB/s)                                                                                                 
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 210091 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-22-generic
Building for architecture x86_64
Building initial module for 4.2.0-22-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.2.0-22-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-22-generic
metheon@ubuntu-mbp:~$ sudo modprobe -v wl
metheon@ubuntu-mbp:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 982 not upgraded.
metheon@ubuntu-mbp:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

And another output from the wifi debug script.

```

########## wireless info START ##########

Report from: 28 Dec 2015 15:20 CET +0100

Booted last: 28 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              548864  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3097 (3.0 KB)  TX bytes:9853 (9.8 KB)
          Interrupt:20 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:396
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

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

root       720     1  1 15:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       8c666eb0-54bc-4134-8da2-28de2ce579c9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8c666eb0-54bc-4134-8da2-28de2ce579c9 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.10/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451398796
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.10
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 8.8.4.4 8.8.4.4
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

Region: Europe/Copenhagen (based on set time zone)

country DK: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
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

[   12.112202] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.143964] wl: module verification failed: signature and/or required key missing - tainting kernel
[   12.327903] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   12.380376] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   13.199207] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   13.995588] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   16.398465] tg3 0000:03:00.0 enp3s0: Link is up at 1000 Mbps, full duplex
[   16.398478] tg3 0000:03:00.0 enp3s0: Flow control is off for TX and off for RX
[   16.398497] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   58.798529] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

### Post by Hadaka on 2015-12-28
Hi,everything ran without error,logically you should have wireless
but,you do not.Did you have to adjust "EFI" like windows UEFI to
install Ubuntu? I am going to suggest you load Ubuntu 14.04 LTS
its supported longer than 15.10 anyway and is much more stable.
If you choose to do so,after run the update and upgrade commands.
thanks.

---

### Post by metheon on 2015-12-28
Hi Hadaka.

I actually did not modify EFI at all, I merely installed Ubuntu on a second drive in my laptop (a replacement for the optical drive). That means I now have my machine defaulting into Ubuntu, and I have to press the alt key during boot to be able to select OS X using the default mac boot selection menu. I chose this option in order to be able to utilize full disk encryption for both drives.

While I have not tried your exact sequence of commands on 14.04 I did spend a couple of evenings may '14 in an effort to get wireless working (in vain).

Could there be some human error going on here? I suspect that when booting linux, if the wifi was working it would automatically show nearby hotspots in the wifi menu? Both in the tray icon as well as in the application Network? Does it need to be enabled somehow?

In general this whole thing is a bit weird as I have found numerous cases on the web with people with this exact network card getting it to work. Following the various guides have obviously yielded no positive results. I did however notice that in the list of broadcom cards else where on this forum there is a match for 14e4:432b but NOT for my card specifically which is 14e4:432b (rev 01).

---

### Post by Hadaka on 2015-12-28
im not seeing anything for 14e4:432b (rev 01).either.
we can try the bcma and brcmsmac combo and see if  that works,
try..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe bcma
sudo modprobe brcmsmac
```
dont boot and test wireless.

---

### Post by metheon on 2015-12-28
Hi again.

Hope I did this correctly.

Terminal output:

```

&#9654; sudo apt-get remove --purge bcmwl-kernel-source -y
[sudo] password for metheon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 977 not upgraded.
After this operation, 8,013 kB disk space will be freed.
(Reading database ... 212584 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.120ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-22-generic

~                                                                                                                                   
&#9654; sudo modprobe bcma

~                                                                                                                                   
&#9654; sudo modprobe brcmsmac

```

Another go at the debug script.

```

########## wireless info START ##########

Report from: 28 Dec 2015 15:20 CET +0100

Booted last: 28 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              548864  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3097 (3.0 KB)  TX bytes:9853 (9.8 KB)
          Interrupt:20 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:396
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

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

root       720     1  1 15:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       8c666eb0-54bc-4134-8da2-28de2ce579c9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8c666eb0-54bc-4134-8da2-28de2ce579c9 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.10/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451398796
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.10
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 8.8.4.4 8.8.4.4
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

Region: Europe/Copenhagen (based on set time zone)

country DK: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
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

[   12.112202] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.143964] wl: module verification failed: signature and/or required key missing - tainting kernel
[   12.327903] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   12.380376] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   13.199207] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   13.995588] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   16.398465] tg3 0000:03:00.0 enp3s0: Link is up at 1000 Mbps, full duplex
[   16.398478] tg3 0000:03:00.0 enp3s0: Flow control is off for TX and off for RX
[   16.398497] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   58.798529] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

In other news, tethering via my iPhone via Bluetooth works flawlessly.

Thanks again. :)

---

### Post by Mohamed_Selim on 2015-12-28
Hi,
I have the same problem with Dell XPS 15 with Ubuntu 15.10 along with Broadcom BCM4352 wireless. I've downloaded the STA driver from broadcom.com ([https://www.broadcom.com/support/802.11](https://www.broadcom.com/support/802.11)). You have to build the driver and install it yourself.

Hope this helps

---

### Post by Hadaka on 2015-12-28
Hi, lets try that again only a little different this time
its showing "wl" broacom-kernel-source as the driver
and it shouldnt,..please do..
```
sudo apt-get remove --purge bcmwl-kernel-source 
sudo modprobe -rf wl
```
BOOT
```
sudo modprobe bcma 
sudo modprobe brcmsmac
```
test wireless

---

### Post by metheon on 2015-12-29
Hi Hadaka.

That didn't work either. :( 

Terminal output.

```

&#9654; sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for metheon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 977 not upgraded.

~                                                                              
&#9654; sudo modprobe -rf wl
modprobe: FATAL: Module wl not found.

#######
REBOOT
#######

&#9654; sudo modprobe bcma
[sudo] password for metheon: 

~                                                                              
&#9654; sudo modprobe brcmsmac


```

In fact, now the wireless interface under Network is completely gone. :/

And the wifi debug script.

```

########## wireless info START ##########

Report from: 28 Dec 2015 15:20 CET +0100

Booted last: 28 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              548864  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3097 (3.0 KB)  TX bytes:9853 (9.8 KB)
          Interrupt:20 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:396
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

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

root       720     1  1 15:19 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       8c666eb0-54bc-4134-8da2-28de2ce579c9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8c666eb0-54bc-4134-8da2-28de2ce579c9 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.10/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1451398796
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.0.1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.10
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 8.8.4.4 8.8.4.4
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

Region: Europe/Copenhagen (based on set time zone)

country DK: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
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

[   12.112202] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.143964] wl: module verification failed: signature and/or required key missing - tainting kernel
[   12.327903] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   12.380376] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   13.199207] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   13.995588] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   16.398465] tg3 0000:03:00.0 enp3s0: Link is up at 1000 Mbps, full duplex
[   16.398478] tg3 0000:03:00.0 enp3s0: Flow control is off for TX and off for RX
[   16.398497] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   58.798529] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

What I have seen now a couple of times is this bit, is that worrying?

```

##### dmesg #############################

[   12.112202] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.143964] wl: module verification failed: signature and/or required key missing - tainting kernel

```

---

### Post by metheon on 2015-12-29
> **Mohamed_Selim said:**
> Hi,
I have the same problem with Dell XPS 15 with Ubuntu 15.10 along with Broadcom BCM4352 wireless. I've downloaded the STA driver from broadcom.com ([https://www.broadcom.com/support/802.11](https://www.broadcom.com/support/802.11)). You have to build the driver and install it yourself.

Hope this helps

Hi Mohamed_Selim.

Gave this a shot as well. Thank you for your suggestion. :)

Downloaded the driver for 64-bit and ran the following commands in the terminal.

```

&#9654; cd Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271 

~/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271                
&#9654; make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-22-generic'
CFG80211 API is prefered for this kernel version
/home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/Makefile:85: Neither CFG80211 nor Wireless Extension is enabled in kernel
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-22-generic'

~/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271                
&#9654; make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-22-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/built-in.o
  CC [M]  /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/src/shared/linux_osl.o
  CC [M]  /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/src/wl/sys/wl_linux.o
  CC [M]  /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/src/wl/sys/wl_iw.o
  CC [M]  /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/src/wl/sys/wl_cfg80211_hybrid.o
  LD [M]  /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/wl.o
  Building modules, stage 2.
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  MODPOST 1 modules
  CC      /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/wl.mod.o
  LD [M]  /home/metheon/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271/wl.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-22-generic'

&#9654; sudo cp wl.ko /lib/modules/4.2.0-22-generic/kernel/net/wireless/

~/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271                
&#9654; ls /lib/modules/4.2.0-22-generic/kernel/net/wireless/
cfg80211.ko             lib80211_crypt_tkip.ko  lib80211.ko
lib80211_crypt_ccmp.ko  lib80211_crypt_wep.ko   wl.ko

~/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271                
&#9654; sudo depmod

~/Downloads/hybrid-v35_64-nodebug-pcoem-6_30_223_271                
&#9654; sudo modprobe wl

```

Sadly this is no different from running the stock bcmwl-kernel-source driver, at least in my eyes.

Here's the wifi debug script.

```

########## wireless info START ##########

Report from: 29 Dec 2015 08:19 CET +0100

Booted last: 29 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6447104  0
cfg80211              548864  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

bnep0     Link encap:Ethernet  HWaddr <MAC 'bnep0' [IF]>  
          inet addr:172.20.10.5  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::<IP6 'bnep0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:620916 (620.9 KB)  TX bytes:967177 (967.1 KB)

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:1402
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

bnep0     no wireless extensions.

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    800    0        0 bnep0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 bnep0
172.20.10.0     0.0.0.0         255.255.255.240 U     800    0        0 bnep0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       723     1  0 08:03 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_DC_37_14_84_66_7C
GENERAL.IP-IFACE:                       bnep0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kenneths iPhone Network
GENERAL.CON-UUID:                       27cbe148-ca3d-49d4-8f6f-03f52f8a29d3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   27cbe148-ca3d-49d4-8f6f-03f52f8a29d3 | Kenneths iPhone Network
IP4.ADDRESS[1]:                         172.20.10.5/28
IP4.GATEWAY:                            172.20.10.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.20.10.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = Kenneths-iPhone
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1451458362
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 172.20.10.1
DHCP4.OPTION[11]:                       broadcast_address = 172.20.10.15
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 172.20.10.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 85536
DHCP4.OPTION[16]:                       ip_address = 172.20.10.5
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 172.20.10.1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.240
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       network_number = 172.20.10.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.20.10.1
IP6.ADDRESS[1]:                         fe80::<IP6 'bnep0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

Region: Europe/Copenhagen (based on set time zone)

country DK: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

bnep0     no frequency information.

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz

##### iwlist scan #######################

bnep0     Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/wl.ko
license:        MIXED/Proprietary
srcversion:     FC97760864C4FC86CF8284C
depends:        cfg80211
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-22-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        5B:A1:35:31:09:D2:78:49:DD:D6:FB:D5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo:   sha512
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

[   13.504577] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   14.307288] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   75.052131] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 16 times)
[  947.837977] ERROR @wl_dev_intvar_get : error (-1)
[  949.049833] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)

########## wireless info END ############

```

---

### Post by gernot3 on 2016-02-21
I found to have the wifi not starting on my mac book pro (14e4:432b (rev 01) as well, tried everything in this thread and had it working on/off sometimes but not really reproduceable.

so I wiped all packages and went back to the initial bcmwl-kernel-source
and it worked immediately again after installing .. that is until i rebooted. I've tried around a bit again and long story short: i just noticed that wifi is working only after I wake up the notebook from suspend ..

here's the wireless info right after a clean boot:
```

########## wireless info START ##########

Report from: 21 Feb 2016 14:07 CET +0100

Booted last: 21 Feb 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-6-generic #21-Ubuntu SMP Tue Feb 16 20:32:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              557056  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:8110
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       668     1  1 14:04 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/vossinet]] (600 root)
[connection] id=vossinet | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=vossinet
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/claunet]] (600 root)
[connection] id=claunet | type=wifi | permissions=user:vossi:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=claunet
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Vienna (based on set time zone)

country AT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp2s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-6-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-6-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-6-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     512CEC08D825E0BE23341B3
depends:        
intree:         Y
vermagic:       4.4.0-6-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

powertop --auto-tune
exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   17.448320] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.454802] wl: module verification failed: signature and/or required key missing - tainting kernel
[   17.518329] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   17.524817] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   37.754523] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   37.756325] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   67.027402] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 3 times)
[  196.495325] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  196.496300] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[  198.344134] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 4 times)
[  247.116354] ERROR @wl_dev_intvar_get : error (-1)
[  249.021597] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 2 times)

########## wireless info END ############


```

here's the wireless info after the following suspend with working wifi:
```

########## wireless info START ##########

Report from: 21 Feb 2016 14:11 CET +0100

Booted last: 21 Feb 2016 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-6-generic #21-Ubuntu SMP Tue Feb 16 20:32:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              557056  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.53  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:8364
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9413 (9.4 KB)  TX bytes:9379 (9.3 KB)
          Interrupt:21 

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:"claunet"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'claunet' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       668     1  0 14:04 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     claunet
GENERAL.CON-UUID:                       f4458ac6-1208-4c38-bcc8-5e2c9fa94198
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     300 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f4458ac6-1208-4c38-bcc8-5e2c9fa94198 | claunet
IP4.ADDRESS[1]:                         192.168.1.53/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.1.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_host_name = 1
DHCP4.OPTION[8]:                        host_name = vossimacbook
DHCP4.OPTION[9]:                        expiry = 1456146616
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       next_server = 192.168.1.1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.1
DHCP4.OPTION[17]:                       ip_address = 192.168.1.53
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[21]:                       dhcp_lease_time = 86400
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_domain_name_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
UPC Wi-Free       <MAC 'UPC Wi-Free' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X  no        
UPC5732859        <MAC 'UPC5732859' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
PS4-35FEAA1ED7F1  <MAC 'PS4-35FEAA1ED7F1' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2         no        
claunet_EXT       <MAC 'claunet_EXT' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2         no        
vossivpn          <MAC 'vossivpn' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Y580D_537E        <MAC 'Y580D_537E' [AC2]>  Infra  2     2417 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
UPC0039664        <MAC 'UPC0039664' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
A1-B54B0D         <MAC 'A1-B54B0D' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
UPC Wi-Free       <MAC 'UPC Wi-Free' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2 802.1X  no        
UPC2344833        <MAC 'UPC2344833' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        
UPC Wi-Free       <MAC 'UPC Wi-Free' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        
vossicast         <MAC 'vossicast' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  --           no        
claunet           <MAC 'claunet' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2         no        
claunet           <MAC 'claunet' [AC1]>  Infra  44    5220 MHz  54 Mbit/s  73      &#9602;&#9604;&#9606;_  WPA2         yes     * 

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

[[/etc/NetworkManager/system-connections/vossinet]] (600 root)
[connection] id=vossinet | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=vossinet
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/claunet]] (600 root)
[connection] id=claunet | type=wifi | permissions=user:vossi:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=claunet
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Vienna (based on set time zone)

country AT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz
          Current Frequency:5.22 GHz (Channel 44)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.22 GHz (Channel 44)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'claunet' [AC1]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"claunet"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Y580D_537E' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Y580D_537E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'claunet' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"claunet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'PS4-35FEAA1ED7F1' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"PS4-35FEAA1ED7F1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'vossivpn' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"vossivpn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UPC5732859' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"UPC5732859"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC Wi-Free' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'UPC0039664' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"UPC0039664"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'UPC Wi-Free' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-6-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-6-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-6-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     512CEC08D825E0BE23341B3
depends:        
intree:         Y
vermagic:       4.4.0-6-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

powertop --auto-tune
exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   37.754523] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   37.756325] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   67.027402] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 3 times)
[  196.495325] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  196.496300] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[  198.344134] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 4 times)
[  247.116354] ERROR @wl_dev_intvar_get : error (-1)
[  249.021597] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22) (repeated 4 times)
[  375.142880] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  375.151008] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[  473.693814] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

for better readability - here's a diff of the 2 (not working is right) [https://www.diffchecker.com/g1zalsy7](https://www.diffchecker.com/g1zalsy7)
weird :)

---

### Post by Hadaka on 2016-02-21
Hi, you really need to open a new thread with this problem and
mark this one solved if you are satisfied with the results. You
currently have posted a completely different ubuntu load and a
different computer,please post a new thread.
thanks.

---

### Post by gernot3 on 2016-02-21
done - [http://ubuntuforums.org/showthread.php?t=2314494&p=13443684#post13443684](http://ubuntuforums.org/showthread.php?t=2314494&p=13443684#post13443684)
sorry!

---

