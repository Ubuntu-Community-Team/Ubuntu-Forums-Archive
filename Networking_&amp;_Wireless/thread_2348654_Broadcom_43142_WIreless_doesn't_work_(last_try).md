---
title: "Broadcom 43142 WIreless doesn't work (last try)"
date: 2017-01-05
forum: Networking &amp; Wireless
---

### Post by Random20240316 on 2017-01-05
Hey I've this problem since i installed Ubuntu 4 days ago and this is driving me crazy!
I've tried nstalling the b43 delete the kernel source and then reboot.
I tried installing the broadcom wireless dkms and that stuff of essentials and reboot, nothing.
Something that i made was put a blacklist in modprobe.d blacklist wl above the b43xxxx and i don't know if i made something wrong
I installed Ubuntu alongside WIndows 10 and i don't know how unistall it for install it again.


```
lspci -nn -d 14e4:02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

```
modprobe wl
modprobe: FATAL: Module wl not found in directory /lib/modules/4.4.0-57-generic

```

```
ifconfig
enp3s0f1  Link encap:Ethernet  direcciónHW c4:54:44:c0:ed:10  
          Direc. inet:192.168.1.67  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fda0:8d16:6c4:3300:f719:9d31:38a8:cd17/64 Alcance:Global
          Dirección inet6: fe80::976d:f536:6a3c:95a0/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:5906 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5252 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:5032179 (5.0 MB)  TX bytes:708631 (708.6 KB)


lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:513 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:513 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1 
          Bytes RX:43815 (43.8 KB)  TX bytes:43815 (43.8 KB)

```

```
iwconfig
enp3s0f1  no wireless extensions.


lo        no wireless extensions.

```

```
lshw -c network
*-network               
       descripción: Network controller
       producto: BCM43142 802.11b/g/n
       fabricante: Broadcom Limited
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: 01
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: driver=bcma-pci-bridge latency=0
       recursos: irq:18 memoria:90500000-90507fff
  *-network
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0.1
       información del bus: pci@0000:03:00.1
       nombre lógico: enp3s0f1
       versión: 12
       serie: c4:54:44:c0:ed:10
       tamaño: 100Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.67 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:264 ioport:1000(size=256) memoria:90404000-90404fff memoria:90400000-90403fff

```

```
clear

```

There's a comand to restore all the packages i install?

---

### Post by wildmanne39 on 2017-01-05
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by Random20240316 on 2017-01-05
[B]If 'Broadcom' appears in the output next to '[0280]', please head over to the[ Broadcom guide]("http://ubuntuforums.org/showthread.php?t=2214110").
[/B]sudo apt-get install  bcmwl-kernel-source


It didnt work :/

---

### Post by wildmanne39 on 2017-01-05
Your were supposed to run the wireless script in that link and post the file it creates here for us to see.
Thanks

---

### Post by Random20240316 on 2017-01-05
OK i executed this is what it drop in wireless-info.txt
```

########## wireless info START ##########

Report from: 05 Jan 2017 22:31 CST -0600


Booted last: 05 Jan 2017 00:00 CST -0600


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Foxconn International, Inc. BCM43142 802.11b/g/n [105b:e07e]
    Kernel modules: bcma, wl


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:0934]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b47f Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0489:e055 Foxconn / Hon Hai 
Bus 001 Device 003: ID 1ea7:0064  
Bus 001 Device 002: ID 3938:1032  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
cfg80211              565248  0
video                  40960  2 i915,acer_wmi
wmi                    20480  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f1  Link encap:Ethernet  HWaddr <MAC 'enp3s0f1' [IF1]>  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fda0:8d16:6c4:3300:f719:9d31:38a8:cd17/64 Scope:Global
          inet6 addr: fe80::976d:f536:6a3c:95a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:409289 (409.2 KB)  TX bytes:151439 (151.4 KB)


##### iwconfig ##########################


enp3s0f1  no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp3s0f1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0f1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0f1


##### resolv.conf #######################


nameserver 127.0.1.1
search huawei.net


##### network managers ##################


Installed:


    NetworkManager


Running:


root       840     1  0 22:27 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp3s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.1/net/enp3s0f1
GENERAL.IP-IFACE:                       enp3s0f1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     casa
GENERAL.CON-UUID:                       45cee85b-ef31-4893-8c6a-675462e51732
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   45cee85b-ef31-4893-8c6a-675462e51732 | casa
IP4.ADDRESS[1]:                         192.168.1.67/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          huawei.net
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1483763269
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.254
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.67
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = huawei.net
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.254 192.168.1.254
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fda0:8d16:6c4:3300:f719:9d31:38a8:cd17/64
IP6.ADDRESS[2]:                         fe80::976d:f536:6a3c:95a0/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fda0:8d16:6c4:3300::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:12:cf:f7:af:a0:8d:16:6:c4:33
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:c0:5a:d0:ae:7d:cc:8b:a8:dc:88:3d:4e:d2:86:f4:70


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


Region: America/Monterrey (based on set time zone)


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


enp3s0f1  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp3s0f1  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


b43
b43


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


[/etc/pm/config.d/unload_modules] (644 root)
SUSPEND_MODULES="$SUSPEND_MODULES r8169"


##### udev rules ########################


##### dmesg #############################


[   34.424404] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[   34.643686] r8169 0000:03:00.1 enp3s0f1: link down (repeated 2 times)
[   34.643810] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[   36.339677] r8169 0000:03:00.1 enp3s0f1: link up
[   36.339692] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0f1: link becomes ready


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-01-05
Does the wifi come on if you do:
```
sudo modprobe wl
```
Thanks

---

### Post by Random20240316 on 2017-01-06
modprobe: ERROR: could not insert 'wl': Required key not available

This has been appaering since the first solutions i have tried

---

### Post by wildmanne39 on 2017-01-06
That is what I thought would be shown, please go into your bios and turn off secure boot and your wifi should come on when you boot ubuntu.
Thanks

---

### Post by Random20240316 on 2017-01-06
hahaha now i lose the grub menu :)

---

### Post by wildmanne39 on 2017-01-06
Just turning off secure boot should not do that but let's work on the wireless issue, did wifi come on? do you have wireless enabled in network manager?
if it did not come on do:
```
sudo sed -i '/^b43/ d' /etc/modules
```
```
sudo iw reg set MX
sudo sed -i 's/=.*/=MX/' /etc/default/crda
```
what does the following two commands tell us?
```
sudo modprobe -v wl
dmesg | grep wl
```
Please copy and paste all commands for accuracy.
Thanks

---

### Post by Random20240316 on 2017-01-06
Bro thank you for this, now i can see the networks now and i connect it to my laptop and now is working ! All this by you!

THANKS !

---

### Post by Random20240316 on 2017-01-06
Hey can i delete all the txts in my personal folder?? like the wireless-info

---

### Post by wildmanne39 on 2017-01-06
Reboot and make sure it still works please, we may have to set the driver to load at boot if it does not.
Thanks

---

### Post by wildmanne39 on 2017-01-06
Yes you can delete the text files.

---

