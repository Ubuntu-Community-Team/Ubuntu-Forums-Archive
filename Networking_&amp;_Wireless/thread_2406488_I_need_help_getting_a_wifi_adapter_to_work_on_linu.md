---
title: "I need help getting a wifi adapter to work on linux"
date: 2018-11-21
forum: Networking &amp; Wireless
---

### Post by aramchekian on 2018-11-21
PC:
Lenovo Thinkcentre E73
 
Wifi Adapter(s):
Tp-link AC600 Archer T2U
Netgear Nighthawk AC1900 A7000
 
Router:
Netgear Nighthawk AC1900 R7000
 
Linux:
Kernel 4.15
Ubuntu 18.04

---

### Post by slickymaster on 2018-11-21
Hello aramchekian, welcome to the forums

Please have a read at the [Before posting in Networking & Wireless]("https://ubuntuforums.org/showthread.php?t=370108") sticky and afterwards do what is suggested there

---

### Post by aramchekian on 2018-11-21
Thank you for the quick reply! I am going to do a fresh installation of Ubuntu 18.04 and then follow your instructions.

---

### Post by aramchekian on 2018-11-21
I have read the thread "Before posting in Networking & Wireless" and followed the suggestions per your instructions. I am ready for any further instructions on how to resolve this issue.

---

### Post by slickymaster on 2018-11-21
Basically, all you have to do is to download and run the wireless info script, which will gather information to help diagnose your system. You can run it using this command```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

---

### Post by aramchekian on 2018-11-21
```
########## wireless info START ##########

Report from: 21 Nov 2018 12:35 EST -0500

Booted last: 21 Nov 2018 00:00 EST -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-39-generic #42-Ubuntu SMP Tue Oct 23 15:48:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3098]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 17ef:6019 Lenovo 
Bus 003 Device 003: ID 17ef:6018 Lenovo 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.0.16/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 2961sec preferred_lft 2961sec
    inet6 fe80::b3f1:2d8e:905b:e2c7/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp2s0 proto dhcp metric 20100 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.0.0/24 dev enp2s0 proto kernel scope link src 192.168.0.16 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
search earthlink.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       691     1  0 12:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       475a32dd-1e8b-30d2-99c9-f568fc6534d9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.16/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 20100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             207.69.188.186
IP4.DNS[2]:                             207.69.188.187
IP4.DOMAIN[1]:                          earthlink.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 207.69.188.186 207.69.188.187
DHCP4.OPTION[5]:                        ip_address = 192.168.0.16
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[14]:                       requested_domain_name_servers = 1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = earthlink.net
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1542824710
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       requested_host_name = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::b3f1:2d8e:905b:e2c7/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   475a32dd-1e8b-30d2-99c9-f568fc6534d9 | Wired connection 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   25.803363] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   26.014272] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[   26.014362] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   38.466617] r8169 0000:02:00.0 enp2s0: link up
[   38.466628] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############
```

---

### Post by chili555 on 2018-11-21
Was the USB wireless inserted when you ran the wireless script? We see nothing about it.

With the device inserted, please run and post:```
lsusb
```

---

### Post by aramchekian on 2018-11-21
No, the device was not inserted. I will be away from the computer until tomorrow, but I will do what you asked first thing in the morning. Thank you so much for looking into this.

Edit: I actually have 2 wifi usb adapters in my posession. I'm not sure which, if either of them, will work with the thinkcentre e73 and linux. If necessary or if you reccomend it, I can exchange one of them for a wifi adapter that is more compatible.

---

### Post by chili555 on 2018-11-21
> **aramchekian said:**
> No, the device was not inserted. I will be away from the computer until tomorrow, but I will do what you asked first thing in the morning. Thank you so much for looking into this.

Edit: I actually have 2 wifi usb adapters in my posession. I'm not sure which, if either of them, will work with the thinkcentre e73 and linux. If necessary or if you reccomend it, I can exchange one of them for a wifi adapter that is more compatible.Please run in turn:```
lsusb 
```...with each inserted. When we see the exact details, we'll further advise you.

Some USB wireless devices work out of the box, some can be made to work easily and some not at all. Once we know what you have, we'll recommend one or the other.

---

### Post by aramchekian on 2018-11-22
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 17ef:6019 Lenovo 
Bus 003 Device 004: ID 0846:9054 NetGear, Inc. 
Bus 003 Device 003: ID 17ef:6018 Lenovo 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by aramchekian on 2018-11-22
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 17ef:6019 Lenovo 
Bus 003 Device 005: ID 148f:761a Ralink Technology, Corp. 
Bus 003 Device 003: ID 17ef:6018 Lenovo 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by jeremy31 on 2018-11-22
For the Netgear adapter do ```
sudo apt install git dkms build-essential
git clone https://github.com/zebulon2/rtl8814au.git
gedit rtl8814au/dkms.conf
```
Change line 1 so it is ```
MAKE="'make' all KVER=${kernelver}"
```
Then save and exit gedit
```
cd
sudo dkms add ./rtl8814au
sudo dkms install rtl8814au/4.3.21
```
Reboot

---

### Post by aramchekian on 2018-11-22
That worked. Thank you to everybody who helped me with this. Before I mark this thread as solved, is there anything else I should do now, or in the event that it stops working? If not, the next task for me is getting this computer connected to a printer... I'll probably be starting a new thread for that, as I have never setup a printer on linux before.

Edit: I'm trying to share the oki c5150n printer connected to this computer with a windows 10 laptop. So far I am only able to print directly from this computer.

---

### Post by aramchekian on 2018-11-23
I am not sure if I should post a thread about the printer issue in "hardware" or "networking & wireless." Do I need to setup a network for printing?

---

### Post by slickymaster on 2018-11-25
> **aramchekian said:**
> I am not sure if I should post a thread about the printer issue in "hardware" or "networking & wireless." Do I need to setup a network for printing?

The correct sub-forum for it would be [Hardware]("https://ubuntuforums.org/forumdisplay.php?f=332")

---

