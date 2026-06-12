---
title: "Installing TPlink T2u wireless driver"
date: 2018-03-14
forum: Networking &amp; Wireless
---

### Post by bstyles148 on 2018-03-14
Hi, im trying to install my t2u wireless driver on ubuntu but i cant seem to get it to play ball i have installed ndiswrapper and download the driver from the official website and installing it with ndis ive turned of ufi protected boot etc tried a few different drivers and wont play at all just wondering if anyone can help me at all please
thank you. 
here is my info  

```
########## wireless info START ##########

Report from: 14 Mar 2018 13:24 GMT +0000

Booted last: 14 Mar 2018 00:00 GMT +0000

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0e6f:0113 Logic3 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:761a Ralink Technology, Corp.      This is the one i need <---
Bus 001 Device 002: ID 03f0:e807 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1b1c:1b3c Corsair 
Bus 004 Device 002: ID 1a2c:2124 China Resource Semico Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.12  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::3d14:17d0:71bf:19f6  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 108272  bytes 133750710 (133.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 160233  bytes 115149923 (115.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2758  bytes 240590 (240.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2758  bytes 240590 (240.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       606     1  0 13:08 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (M4A785TD Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0a.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0342de75-4d10-367b-b311-9ffefc4b7ef7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0342de75-4d10-367b-b311-9ffefc4b7ef7 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.12/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = kry-System-Product-Name
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1521119297
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.12
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::3d14:17d0:71bf:19f6/64
IP6.GATEWAY:                            --

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

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

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############
```

---

### Post by chili555 on 2018-03-14
ndiswrapper requires the Windows XP inf and sys files. Is that what you downloaded and installed?

From the command:```
man ndiswrapeer
```> 
ndiswrapper - Linux kernel module and user space tool to load and run Windows **XP** drivers for wireless cardsI see that your device is this:> 
148f:761a Ralink Technology, Corp. 
Please check here: [https://wikidevi.com/wiki/TP-LINK_Archer_T2U](https://wikidevi.com/wiki/TP-LINK_Archer_T2U) and my post #18 here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u)

---

### Post by bstyles148 on 2018-03-14
Result of command lsusb:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0e6f:0113 Logic3 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:761a Ralink Technology, Corp. 
Bus 001 Device 002: ID 03f0:e807 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1b1c:1b3c Corsair 
Bus 004 Device 002: ID 1a2c:2124 China Resource Semico Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I tried the Xp version  (rt2870.inf) still no luck installed while device unplugged , restarted plugged in start to start it no anvil

ndiswrapper -i RT2870.inf
driver rt2870 is already installed

---

### Post by chili555 on 2018-03-14
Did you see my edit to my post above? I doubt that there is much hope.

---

### Post by praseodym on 2018-03-14
[https://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver](https://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver)

There is a Linux driver from the manufacturer, but I don't know if it works with kernel 4.13

---

### Post by chili555 on 2018-03-14
> **praseodym said:**
> [https://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver](https://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver)

There is a Linux driver from the manufacturer, but I don't know if it works with kernel 4.13It says: > Operating System: Linux (Kernel version 2.6~3.16)...so I'll bet that kernel version 4.13 is too new.

---

### Post by praseodym on 2018-03-14
Here, it compiled up to kernel 4.4

---

### Post by jeremy31 on 2018-03-14
I think some of the github sites still work with the 4.4 kernel
[https://github.com/ulli-kroll/mt7610u](https://github.com/ulli-kroll/mt7610u) shows some updates to work in kernel 4.15

---

### Post by bstyles148 on 2018-03-14
Hi sorry for the late reply i tried the official driver from the website no luck @jeremy31 should i try that driver?

---

### Post by jeremy31 on 2018-03-14
You could try it after removing ndiswrapper and make sure Secure Boot is disabled in UEFI/BIOS

---

### Post by bstyles148 on 2018-03-14
okay i'll try that thank you

---

### Post by bstyles148 on 2018-03-14
@jeremy31 
Here's what happened 
```
kry@kry-System-Product-Name:~/Downloads/mt7610u-master$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-37-generic/build M=/home/kry/Downloads/mt7610u-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-37-generic'
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/rt_profile.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/assoc.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/auth.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/auth_rsp.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/sync.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/sanity.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/rtmp_data.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/connect.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/wpa.o
  CC [M]  /home/kry/Downloads/mt7610u-master/sta/sta_cfg.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mgmt/mgmt_vht.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/vht.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/crypt_md5.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/crypt_sha2.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/crypt_hmac.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/crypt_aes.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/crypt_arc4.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/mlme.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_wep.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/action.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_data.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rtmp_init.o
/home/kry/Downloads/mt7610u-master/common/rtmp_init.c: In function &#8216;NICInitializeAsic.part.0&#8217;:
/home/kry/Downloads/mt7610u-master/common/rtmp_init.c:1026:1: warning: the frame size of 2040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rtmp_init_inf.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_tkip.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_aes.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_sync.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_sanity.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_info.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_cfg.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_wpa.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_radar.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/spectrum.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rtmp_timer.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rt_channel.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_profile.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_asic.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/scan.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_cmd.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/uapsd.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/ps.o
  CC [M]  /home/kry/Downloads/mt7610u-master/rate_ctrl/ra_ctrl.o
  CC [M]  /home/kry/Downloads/mt7610u-master/rate_ctrl/alg_legacy.o
  CC [M]  /home/kry/Downloads/mt7610u-master/rate_ctrl/alg_ags.o
  CC [M]  /home/kry/Downloads/mt7610u-master/chips/rtmp_chip.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/txpower.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mac/rtmp_mac.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mgmt/mgmt_entrytb.o
  CC [M]  /home/kry/Downloads/mt7610u-master/phy/rlt_phy.o
  CC [M]  /home/kry/Downloads/mt7610u-master/phy/rlt_rf.o
  CC [M]  /home/kry/Downloads/mt7610u-master/rate_ctrl/alg_grp.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/ba_action.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mgmt/mgmt_ht.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rt_os_util.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/sta_ioctl.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/rt_linux.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/rt_main_dev.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rt_led.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/cfg80211.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/cfg80211drv.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_mac_usb.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/cmm_data_usb.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rtusb_io.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rtusb_data.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rtusb_bulk.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/rt_usb.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/rt_rf.o
  CC [M]  /home/kry/Downloads/mt7610u-master/chips/rt65xx.o
  CC [M]  /home/kry/Downloads/mt7610u-master/chips/mt76x0.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mac/ral_nmac.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mcu/mcu.o
  CC [M]  /home/kry/Downloads/mt7610u-master/mcu/mcu_and.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/rt_usb_util.o
  CC [M]  /home/kry/Downloads/mt7610u-master/os/linux/usb_main_dev.o
  CC [M]  /home/kry/Downloads/mt7610u-master/common/frq_cal.o
  LD [M]  /home/kry/Downloads/mt7610u-master/mt7610u.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/kry/Downloads/mt7610u-master/mt7610u.mod.o
  LD [M]  /home/kry/Downloads/mt7610u-master/mt7610u.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-37-generic'
kry@kry-System-Product-Name:~/Downloads/mt7610u-master$ sudo make installfw
[sudo] password for kry: 
cp -n firmware/* /lib/firmware
kry@kry-System-Product-Name:~/Downloads/mt7610u-master$ sudo insmod mt7610u.ko
insmod: ERROR: could not insert module mt7610u.ko: Unknown symbol in module
```

---

### Post by jeremy31 on 2018-03-14
Try ```
sudo cp ~/Downloads/mt7610u-master/mt7610u.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
sudo depmod -a
```
Reboot

---

### Post by bstyles148 on 2018-03-14
Okay that activated in the wireless manager but i cant seem to pick up networks , there is networks around me of course so hardware is okay , just keeps searching
any thoughts on that?

[https://imgur.com/7gucpzi](https://imgur.com/7gucpzi)

---

### Post by jeremy31 on 2018-03-14
Lets see new script results
```
cd
./wireless-info
cat wireless-info.txt | nc termbin.com 9999
```
Post URL

---

### Post by bstyles148 on 2018-03-14
[http://paste.ubuntu.com/p/yZftnhYFb4/](http://paste.ubuntu.com/p/yZftnhYFb4/)

---

### Post by jeremy31 on 2018-03-14
I would access the router and change the wifi encryption to WPA2 only using AES/CCMP as it uses TKIP on 2.4 Ghz and TKIP causes issues

---

