---
title: "Cannot connect to WIFI after installing Ubuntu 16.04"
date: 2016-06-26
forum: Networking &amp; Wireless
---

### Post by federicodemaria on 2016-06-26
Hi, 
I've just installed Ubuntu 16.04 on brand new desktop. Everything works, a part from WIFI. I don't see any network. 

I've googled, and seen that it is a common problem, however, I have not been able to solve it. 

Via ethernet cable, I've updated the system. I paste below a bunch of info, hope usefull (lshw -C; wireless-info; lspci; network-manager)

My questions are: 
1) Do I have a wireless card? I guess so...
2) If it is a software/driver problem, how could I solve it? 

Obviously, I'm not an expert, just a normal user. 

Thank you 
j






**1) lshw -C**

```
Hardware Lister (lshw) - B.02.17
uso: lshw [-formato] [-opciones ...]
       lshw -version

	-versión de programa de muestra (B.02.17)

el formato puede ser
	- salida de estructura de hardware en HTML
	- salida de estructura de hardware en XML
	- salida de rutas cortas de hardware
	-businfo muestra información del bus

las opciones pueden ser
	-class CLASS solo muestra un cierto tipo de hardware
	-C CLASS es igual que «-class CLASS»
	-c CLASS es igual que «-class CLASS»
	-disable TEST desactiva una prueba (tipo pci, isapnp, cpuid, etc. )
	-enable TEST activa una prueba (tipo pci, isapnp, cpuid, etc. )
	-quiet no muestra el estado
	-sanitize sanea la salida (elimina información sensible tipo números de serie, etc.)
	-numeric muestra IDs numéricos (para PCI, USB, etc.)

```

**2) sudo apt-get install linux-headers-generic build-essential dkms**

DONE 


[B]3) ```
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info[/B]

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2016-06-26 11:40:33--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolviendo github.com (github.com)... 192.30.252.128
Conectando con github.com (github.com)[192.30.252.128]:443... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [siguiente]
--2016-06-26 11:40:34--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolviendo raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.60.133
Conectando con raw.githubusercontent.com (raw.githubusercontent.com)[151.101.60.133]:443... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 16122 (16K) [text/plain]
Grabando a: “wireless-info”

wireless-info       100%[===================>]  15,74K  --.-KB/s    in 0,08s   

Falta la cabecera de fecha de la última modificación -- marcas de tiempo desactivadas.
2016-06-26 11:40:35 (201 KB/s) - “wireless-info” guardado [16122/16122]


Results saved in "/home/veronica/wireless-info.txt".




########## wireless info START ##########

Report from: 26 Jun 2016 11:40 CEST +0200

Booted last: 26 Jun 2016 00:00 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 005 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 14cd:125c Super Top SD card reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a66f:5a49:faf6:2412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12034932 (12.0 MB)  TX bytes:1197488 (1.1 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       761     1  0 11:28 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexión cableada 1
GENERAL.CON-UUID:                       a9b05c41-fd6a-49f3-8f25-d676509217fc
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a9b05c41-fd6a-49f3-8f25-d676509217fc | Conexión cableada 1
IP4.ADDRESS[1]:                         192.168.1.18/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       expiry = 1467192603
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 259200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.18
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::a66f:5a49:faf6:2412/64
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

Region: Europe/Madrid (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

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

##### dmesg #############################

[   17.000868] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   17.227766] r8169 0000:02:00.0 enp2s0: link down
[   17.227812] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   90.087816] r8169 0000:02:00.0 enp2s0: link up
[   90.087824] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############

**4) ABOUT MY SYSTEM **

lspci

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
03:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)


5) **NETWORK MANAGER **

network-manager:
  Instalados: 1.2.0-0ubuntu0.16.04.2
  Candidato:  1.2.0-0ubuntu0.16.04.2
  Tabla de versión:
 *** 1.2.0-0ubuntu0.16.04.2 500
        500 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.1.93-0ubuntu4 500
        500 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages

**6) iwconfig**
enp2s0    no wireless extensions.

lo        no wireless extensions.

**7) lspci -n | egrep '0200|0280' | awk '{print$3}'**
10ec:8168
```

---

### Post by praseodym on 2016-06-26
Obviously, no card is detected. Check the BIOS if it can be activated there. Please also show
```

usb-devices
```

---

### Post by federicodemaria on 2016-06-26
Hi,
thanks for the reply. Here below "usb-devices". 

I'm sorry for my ignorance, what do you mean "Check the BIOS if it can be activated there"?

My knowledge is limited. I understand the BIOS is what I see once I turn on my computer (pressing F2 or F12, I think). 
In the past, I've changed the order for the boot, for example to install Ubuntu from CD/DVD. 

I would be grateful if you could give me some instructions about how to activate the card from the BIOS. 

Thanks a lot!

Best,
j

 





Code:

usb-devices




```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8008 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=8000 Rev=00.05
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-24-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=14cd ProdID=125c Rev=03.00
S:  Manufacturer=Generic
S:  Product=Mass Storage Device
S:  SerialNumber=125C20100726
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=248mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-24-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.04
S:  Manufacturer=Linux 4.4.0-24-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:03:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.10 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2109 ProdID=3431 Rev=04.20
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c31c Rev=64.00
S:  Manufacturer=Logitech
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=90mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=05 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c077 Rev=72.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.04
S:  Manufacturer=Linux 4.4.0-24-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:03:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

---

### Post by wildmanne39 on 2016-06-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by federicodemaria on 2016-06-26
ok, thanks for the clarification. I appreciate your kind help...

---

### Post by X-RED_Tech on 2016-06-26
> **federicodemaria said:**
> Hi, 
I've just installed Ubuntu 16.04 on brand new desktop.

Desktops usually don't come with WiFi. You can add either a PCI, PCI-e card or just a simple and cheap USB dongle.

Unless you add it then the answer is no, you don't have one.

---

### Post by federicodemaria on 2016-06-26
I've googled "ubuntu how to activate wifi card from bios". 

I've then followed the instructions from this thread: How do I fix a &#8220;Wireless is disabled by hardware switch&#8221; error?
[http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error](http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error)

It has not solved the problem. Here what I see from the Terminal: 

```

veronica@veronica-H81M-S2H:~$ rfkill unblock all
veronica@veronica-H81M-S2H:~$ rfkill list all
veronica@veronica-H81M-S2H:~$ rfkill list
veronica@veronica-H81M-S2H:~$ sudo rfkill unblock wifi

```
veronica@veronica-H81M-S2H:~$

---

### Post by X-RED_Tech on 2016-06-26
Those commands assume you have wireless. They do nothing otherwise.
Let's make it easier: Post your desktop's make/model and if assembled, the motherboards' make/model.

---

### Post by federicodemaria on 2016-06-26
I keep trying by checking other threads...
[http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card](http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card)

lsusb

```

veronica@veronica-H81M-S2H:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 005 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 14cd:125c Super Top SD card reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
veronica@veronica-H81M-S2H:~$ 

```

```

veronica@veronica-H81M-S2H:~$ ifconfig
enp2s0    Link encap:Ethernet  direcciónHW 40:8d:5c:d9:dd:10  
          Direc. inet:192.168.1.18  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::a66f:5a49:faf6:2412/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:89974 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:81726 errores:0 perdidos:14 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:79837134 (79.8 MB)  TX bytes:10373998 (10.3 MB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:9049 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9049 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1 
          Bytes RX:837497 (837.4 KB)  TX bytes:837497 (837.4 KB)

veronica@veronica-H81M-S2H:~$

```

If I run 
```

lspci -nn -d 14e4:

```
I dont get anything

```

veronica@veronica-H81M-S2H:~$ sudo lshw -C network
  *-network               
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: enp2s0
       versión: 0c
       serie: 40:8d:5c:d9:dd:10
       tamaño: 100Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.18 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:29 ioport:e000(size=256) memoria:f7d00000-f7d00fff memoria:f0000000-f0003fff
veronica@veronica-H81M-S2H:~$ 

```

---

### Post by X-RED_Tech on 2016-06-26
> **federicodemaria said:**
> I keep trying by checking other threads...
[http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card](http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card)

lsusb

```

veronica@veronica-H81M-S2H:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 005 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 005 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 14cd:125c Super Top SD card reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
veronica@veronica-H81M-S2H:~$ 

```

```

veronica@veronica-H81M-S2H:~$ ifconfig
enp2s0    Link encap:Ethernet  direcciónHW 40:8d:5c:d9:dd:10  
          Direc. inet:192.168.1.18  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::a66f:5a49:faf6:2412/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:89974 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:81726 errores:0 perdidos:14 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:79837134 (79.8 MB)  TX bytes:10373998 (10.3 MB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:9049 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9049 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1 
          Bytes RX:837497 (837.4 KB)  TX bytes:837497 (837.4 KB)

veronica@veronica-H81M-S2H:~$

```


The linked page assumes you have a USB WiFi device connected which you don't according to lsusb. Have you connected some? If so it's probably dead. But I suspect you didn't, that you don't have any WiFi card/dongle.

Also I've asked a few question above. Would you please provide the requested info? It's just to be sure...

---

### Post by federicodemaria on 2016-06-26
I'm not sure how I can show you the info you ask for. 
I hope this helps, otherwise, please suggest a command for the terminal 

```

veronica@veronica-H81M-S2H:~$ sudo dmidecode -t 2
# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: H81M-S2H
	Version: x.x
	Serial Number: To be filled by O.E.M.
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

veronica@veronica-H81M-S2H:~$ 

```

```

veronica@veronica-H81M-S2H:~$ lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
03:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
veronica@veronica-H81M-S2H:~$

```

I hope this clarifies. At this point, it might make sense that I don't have a wifi card, although it's strange. I bought it in a little shop in my village, and I thought it was obvious that it comes with one. :-) 

Here the results about my desktop and motherboard model, apologies for the Spanish. 

```

veronica@veronica-H81M-S2H:~$ lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
03:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)

```

```

veronica@veronica-H81M-S2H:~$ sudo lshw  
veronica-h81m-s2h         
    descripción: Equipo de escritorio
    producto: H81M-S2H (To be filled by O.E.M.)
    fabricante: Gigabyte Technology Co., Ltd.
    versión: To be filled by O.E.M.
    serie: To be filled by O.E.M.
    anchura: 64 bits
    capacidades: smbios-2.7 dmi-2.7 vsyscall32
    configuración: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=40028D03-5C04-D905-DD06-100700080009
  *-core
       descripción: Placa base
       producto: H81M-S2H
       fabricante: Gigabyte Technology Co., Ltd.
       id físico: 0
       versión: x.x
       serie: To be filled by O.E.M.
       ranura: To be filled by O.E.M.
     *-firmware
          descripción: BIOS
          fabricante: American Megatrends Inc.
          id físico: 0
          versión: F2
          date: 08/11/2015
          tamaño: 64KiB
          capacidad: 4032KiB
          capacidades: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          descripción: L1 caché
          id físico: 4
          ranura: CPU Internal L1
          tamaño: 256KiB
          capacidad: 256KiB
          capacidades: internal write-back
          configuración: level=1
     *-cache:1
          descripción: L2 caché
          id físico: 5
          ranura: CPU Internal L2
          tamaño: 1MiB
          capacidad: 1MiB
          capacidades: internal write-back unified
          configuración: level=2
     *-cache:2
          descripción: L3 caché
          id físico: 6
          ranura: CPU Internal L3
          tamaño: 6MiB
          capacidad: 6MiB
          capacidades: internal write-back unified
          configuración: level=3
     *-memory
          descripción: Memoria de sistema
          id físico: 7
          ranura: Placa de sistema o placa base
          tamaño: 8GiB
        *-bank:0
             descripción: DIMM DDR3 Síncrono 1600 MHz (0,6 ns)
             producto: KHX1600C10D3/8G
             fabricante: Kingston
             id físico: 0
             serie: 6E0BB049
             ranura: ChannelA-DIMM0
             tamaño: 8GiB
             anchura: 64 bits
             reloj: 1600MHz (0.6ns)
        *-bank:1
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-04-15 05:57+0000X-Generator: Launchpad (build 17995) [vacío]
             producto: [Empty]
             fabricante: [Empty]
             id físico: 1
             serie: [Empty]
             ranura: ChannelA-DIMM1
        *-bank:2
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-04-15 05:57+0000X-Generator: Launchpad (build 17995) [vacío]
             producto: [Empty]
             fabricante: [Empty]
             id físico: 2
             serie: [Empty]
             ranura: ChannelB-DIMM0
        *-bank:3
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-04-15 05:57+0000X-Generator: Launchpad (build 17995) [vacío]
             producto: [Empty]
             fabricante: [Empty]
             id físico: 3
             serie: [Empty]
             ranura: ChannelB-DIMM1
     *-cpu
          descripción: CPU
          producto: Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz
          fabricante: Intel Corp.
          id físico: 40
          información del bus: cpu@0
          versión: Intel(R) Core(TM) i5-4460 CPU @ 3.20GHz
          ranura: SOCKET 0
          tamaño: 3356MHz
          capacidad: 3400MHz
          anchura: 64 bits
          reloj: 100MHz
          capacidades: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
          configuración: cores=4 enabledcores=1
     *-pci
          descripción: Host bridge
          producto: 4th Gen Core Processor DRAM Controller
          fabricante: Intel Corporation
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 06
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=hsw_uncore
          recursos: irq:0
        *-display
             descripción: VGA compatible controller
             producto: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             fabricante: Intel Corporation
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 06
             anchura: 64 bits
             reloj: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list rom
             configuración: driver=i915 latency=0
             recursos: irq:30 memoria:f7800000-f7bfffff memoria:e0000000-efffffff ioport:f000(size=64)
        *-multimedia:0
             descripción: Audio device
             producto: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             fabricante: Intel Corporation
             id físico: 3
             información del bus: pci@0000:00:03.0
             versión: 06
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuración: driver=snd_hda_intel latency=0
             recursos: irq:31 memoria:f7e14000-f7e17fff
        *-usb:0
             descripción: USB controller
             producto: 8 Series/C220 Series Chipset Family USB xHCI
             fabricante: Intel Corporation
             id físico: 14
             información del bus: pci@0000:00:14.0
             versión: 05
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi xhci bus_master cap_list
             configuración: driver=xhci_hcd latency=0
             recursos: irq:26 memoria:f7e00000-f7e0ffff
           *-usbhost:0
                producto: xHCI Host Controller
                fabricante: Linux 4.4.0-24-generic xhci-hcd
                id físico: 0
                información del bus: usb@4
                nombre lógico: usb4
                versión: 4.04
                capacidades: usb-3.00
                configuración: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                producto: xHCI Host Controller
                fabricante: Linux 4.4.0-24-generic xhci-hcd
                id físico: 1
                información del bus: usb@3
                nombre lógico: usb3
                versión: 4.04
                capacidades: usb-2.00
                configuración: driver=hub slots=10 speed=480Mbit/s
              *-usb
                   descripción: Dispositivo de almacenamiento masivo
                   producto: Mass Storage Device
                   fabricante: Generic
                   id físico: 6
                   información del bus: usb@3:6
                   nombre lógico: scsi5
                   versión: 3.00
                   serie: 125C20100726
                   capacidades: usb-2.00 scsi emulated scsi-host
                   configuración: driver=usb-storage maxpower=248mA speed=480Mbit/s
                 *-disk
                      descripción: SCSI Disk
                      id físico: 0.0.0
                      información del bus: scsi@5:0.0.0
                      nombre lógico: /dev/sdb
                      configuración: logicalsectorsize=512 sectorsize=512
        *-communication
             descripción: Communication controller
             producto: 8 Series/C220 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             id físico: 16
             información del bus: pci@0000:00:16.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi bus_master cap_list
             configuración: driver=mei_me latency=0
             recursos: irq:32 memoria:f7e1e000-f7e1e00f
        *-usb:1
             descripción: USB controller
             producto: 8 Series/C220 Series Chipset Family USB EHCI #2
             fabricante: Intel Corporation
             id físico: 1a
             información del bus: pci@0000:00:1a.0
             versión: 05
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci-pci latency=0
             recursos: irq:16 memoria:f7e1c000-f7e1c3ff
           *-usbhost
                producto: EHCI Host Controller
                fabricante: Linux 4.4.0-24-generic ehci_hcd
                id físico: 1
                información del bus: usb@1
                nombre lógico: usb1
                versión: 4.04
                capacidades: usb-2.00
                configuración: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   descripción: USB hub
                   fabricante: Intel Corp.
                   id físico: 1
                   información del bus: usb@1:1
                   versión: 0.05
                   capacidades: usb-2.00
                   configuración: driver=hub slots=4 speed=480Mbit/s
        *-multimedia:1
             descripción: Audio device
             producto: 8 Series/C220 Series Chipset High Definition Audio Controller
             fabricante: Intel Corporation
             id físico: 1b
             información del bus: pci@0000:00:1b.0
             versión: 05
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuración: driver=snd_hda_intel latency=0
             recursos: irq:33 memoria:f7e10000-f7e13fff
        *-pci:0
             descripción: PCI bridge
             producto: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             fabricante: Intel Corporation
             id físico: 1c
             información del bus: pci@0000:00:1c.0
             versión: d5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:16
        *-pci:1
             descripción: PCI bridge
             producto: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             fabricante: Intel Corporation
             id físico: 1c.2
             información del bus: pci@0000:00:1c.2
             versión: d5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:18 ioport:e000(size=4096) memoria:f7d00000-f7dfffff ioport:f0000000(size=1048576)
           *-network
                descripción: Ethernet interface
                producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                fabricante: Realtek Semiconductor Co., Ltd.
                id físico: 0
                información del bus: pci@0000:02:00.0
                nombre lógico: enp2s0
                versión: 0c
                serie: 40:8d:5c:d9:dd:10
                tamaño: 100Mbit/s
                capacidad: 1Gbit/s
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.18 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                recursos: irq:29 ioport:e000(size=256) memoria:f7d00000-f7d00fff memoria:f0000000-f0003fff
        *-pci:2
             descripción: PCI bridge
             producto: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             fabricante: Intel Corporation
             id físico: 1c.3
             información del bus: pci@0000:00:1c.3
             versión: d5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:19 memoria:f7c00000-f7cfffff
           *-usb
                descripción: USB controller
                producto: VL805 USB 3.0 Host Controller
                fabricante: VIA Technologies, Inc.
                id físico: 0
                información del bus: pci@0000:03:00.0
                versión: 01
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress xhci bus_master cap_list
                configuración: driver=xhci_hcd latency=0
                recursos: irq:27 memoria:f7c00000-f7c00fff
              *-usbhost:0
                   producto: xHCI Host Controller
                   fabricante: Linux 4.4.0-24-generic xhci-hcd
                   id físico: 0
                   información del bus: usb@6
                   nombre lógico: usb6
                   versión: 4.04
                   capacidades: usb-3.00
                   configuración: driver=hub slots=4 speed=5000Mbit/s
              *-usbhost:1
                   producto: xHCI Host Controller
                   fabricante: Linux 4.4.0-24-generic xhci-hcd
                   id físico: 1
                   información del bus: usb@5
                   nombre lógico: usb5
                   versión: 4.04
                   capacidades: usb-2.00
                   configuración: driver=hub slots=1 speed=480Mbit/s
                 *-usb
                      descripción: USB hub
                      producto: USB2.0 Hub
                      fabricante: VIA Labs, Inc.
                      id físico: 1
                      información del bus: usb@5:1
                      versión: 4.20
                      capacidades: usb-2.10
                      configuración: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                    *-usb:0
                         descripción: Teclado
                         producto: USB Keyboard
                         fabricante: Logitech
                         id físico: 1
                         información del bus: usb@5:1.1
                         versión: 64.00
                         capacidades: usb-1.10
                         configuración: driver=usbhid maxpower=90mA speed=1Mbit/s
                    *-usb:1
                         descripción: Ratón
                         producto: USB Optical Mouse
                         fabricante: Logitech
                         id físico: 2
                         información del bus: usb@5:1.2
                         versión: 72.00
                         capacidades: usb-2.00
                         configuración: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-usb:2
             descripción: USB controller
             producto: 8 Series/C220 Series Chipset Family USB EHCI #1
             fabricante: Intel Corporation
             id físico: 1d
             información del bus: pci@0000:00:1d.0
             versión: 05
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci-pci latency=0
             recursos: irq:23 memoria:f7e1b000-f7e1b3ff
           *-usbhost
                producto: EHCI Host Controller
                fabricante: Linux 4.4.0-24-generic ehci_hcd
                id físico: 1
                información del bus: usb@2
                nombre lógico: usb2
                versión: 4.04
                capacidades: usb-2.00
                configuración: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   descripción: USB hub
                   fabricante: Intel Corp.
                   id físico: 1
                   información del bus: usb@2:1
                   versión: 0.05
                   capacidades: usb-2.00
                   configuración: driver=hub slots=6 speed=480Mbit/s
        *-isa
             descripción: ISA bridge
             producto: C220 Series Chipset Family H81 Express LPC Controller
             fabricante: Intel Corporation
             id físico: 1f
             información del bus: pci@0000:00:1f.0
             versión: 05
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master cap_list
             configuración: driver=lpc_ich latency=0
             recursos: irq:0
        *-storage
             descripción: SATA controller
             producto: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             fabricante: Intel Corporation
             id físico: 1f.2
             información del bus: pci@0000:00:1f.2
             versión: 05
             anchura: 32 bits
             reloj: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list
             configuración: driver=ahci latency=0
             recursos: irq:28 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memoria:f7e1a000-f7e1a7ff
        *-serial NO RECLAMADO
             descripción: SMBus
             producto: 8 Series/C220 Series Chipset Family SMBus Controller
             fabricante: Intel Corporation
             id físico: 1f.3
             información del bus: pci@0000:00:1f.3
             versión: 05
             anchura: 64 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: memoria:f7e19000-f7e190ff ioport:f040(size=32)
     *-scsi:0
          id físico: 1
          nombre lógico: scsi0
          capacidades: emulated
        *-disk
             descripción: ATA Disk
             producto: ST1000DM003-1SB1
             fabricante: Seagate
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/sda
             versión: CC43
             serie: Z9A1A3V1
             tamaño: 931GiB (1TB)
             capacidades: gpt-1.00 partitioned partitioned:gpt
             configuración: ansiversion=5 guid=636754fb-b8af-4cb6-86b1-4b51889dbb94 logicalsectorsize=512 sectorsize=4096
           *-volume:0 NO RECLAMADO
                descripción: Windows FAT volumen
                fabricante: mkfs.fat
                id físico: 1
                información del bus: scsi@0:0.0.0,1
                versión: FAT32
                serie: 2149-8fa8
                tamaño: 510MiB
                capacidad: 511MiB
                capacidades: boot fat initialized
                configuración: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                descripción: partición EXT4
                fabricante: Linux
                id físico: 2
                información del bus: scsi@0:0.0.0,2
                nombre lógico: /dev/sda2
                nombre lógico: /
                versión: 1.0
                serie: ea31f1a9-2042-4abb-8811-c13abb428eee
                tamaño: 923GiB
                capacidades: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuración: created=2016-06-23 21:01:40 filesystem=ext4 lastmountpoint=/ modified=2016-06-26 11:28:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-06-26 11:28:38 state=mounted
           *-volume:2
                descripción: Linux swap volumen
                fabricante: Linux
                id físico: 3
                información del bus: scsi@0:0.0.0,3
                nombre lógico: /dev/sda3
                versión: 1
                serie: 56c81b96-21f5-4ac1-8434-fd1433bb8dcb
                tamaño: 8088MiB
                capacidad: 8089MiB
                capacidades: nofs swap initialized
                configuración: filesystem=swap pagesize=4095
     *-scsi:1
          id físico: 2
          nombre lógico: scsi4
          capacidades: emulated
        *-cdrom
             descripción: DVD-RAM writer
             producto: DVDRAM GH24NSD1
             fabricante: HL-DT-ST
             id físico: 0.0.0
             información del bus: scsi@4:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/dvd
             nombre lógico: /dev/dvdrw
             nombre lógico: /dev/sr0
             versión: LG00
             capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuración: ansiversion=5 status=nodisc
  *-power NO RECLAMADO
       descripción: To Be Filled By O.E.M.
       producto: To Be Filled By O.E.M.
       fabricante: To Be Filled By O.E.M.
       id físico: 1
       versión: To Be Filled By O.E.M.
       serie: To Be Filled By O.E.M.
       capacidad: 32768mWh
veronica@veronica-H81M-S2H:~$ 

```

> **X-RED_Tech said:**
> The linked page assumes you have a USB WiFi device connected which you don't according to lsusb. Have you connected some? If so it's probably dead. But I suspect you didn't, that you don't have any WiFi card/dongle.

Also I've asked a few question above. Would you please provide the requested info? It's just to be sure...

1) I've not connected any USB WIFI device. I was assuming that the PC has a WIFI card. 
Apologies for the chaos. I don't really understand what all these commands really mean, and I just kept trying (without really understanding).  

2) "Few questions above"? 
Sorry, I'm not sure to which questions you refer. Please, clarify, if possible. 

Thank you very much for your kind support, I really appreciate...

Right now, I'm in the BIOS looking for the network settings page. 
To tell you the truth, I don't find it. 

I see the following pages: 
- M.I.T 
- System information
- BIOS features
- Peripherals 
- Power management 
- Save & Exit

I don't see anything that says Network, a part for "Network stack" under BIOS Feature, but I understand this is something different. 

Under "Perypherals" the only disabled one is "EHCI Hand-off"

---

### Post by X-RED_Tech on 2016-06-26
1) You're really wasting your time on a wrong assumption.
You shouldn't run anything you find in Google just because. It may do nothing or it can have serious consequences. Not in this case fortunately because all you did applies to non-existing hardware.
No, desktops usually don't come with WiFi (except for perhaps half a dozen with onboard WiFi.

2) I just asked for specs and to make it easier - as it was just to confirm - I asked about the make/model (brand and model) of that desktop, or, if assembled from store bought parts, the motherboards' make/model... Also, about whether or not you added hardware/peripherals and you finally answered. Thank you.

The dmidecode above shows you have a [Gigabyte H81M-S2H]("http://www.gigabyte.com/products/product-page.aspx?pid=5158#ov") motherboard (check the specifications) which, rather unsurprisingly, has only wired network onboard:
```
[TABLE="class: tblborder, width: 1459, align: center"]
[TR]
[TD="class: midborderline, align: left"]LAN[/TD]
[TD]
[LIST=1]
[*]Realtek[SUP]®[/SUP] GbE LAN chip (10/100/1000 Mbit)
[/LIST]
[/TD]
[/TR]
[/TABLE]

```

So, knowing it has not onboard WiFi and that you had not add any WiFi device, doesn't it make the answer extremely obvious?
(You can add WiFi with a cheap USB dongle, starting at US$8-10)

---

### Post by federicodemaria on 2016-06-26
I've found more information about the PC I bought. 
My knowledge is very limited, but from what I understand, I don't see any WIFI card listed in the characteristics of this PC. 

It's the following: 
[http://www.appinformatica.com/ordenadores-marca-zone-evil-mini-h81-i5-4460-8gb-1tb-hdmi-usb-3.0-fr.php](http://www.appinformatica.com/ordenadores-marca-zone-evil-mini-h81-i5-4460-8gb-1tb-hdmi-usb-3.0-fr.php)

```

ordenadores marca zone evil
zone evil mini h81 i5 4460 8gb 1tb hdmi usb 3.0 fr
( 8 / 10 ) estrellas
valoración top ventas
APP Informática
TOP 2614 ( 22/06/2016 )
Devolución: 0%



Atención este ordenador esta dotado de una fuente de alimentación de bajo consumo. Cumple la normativa europea de 85% de eficiencia,

obligatoria en todos los ordenadores desde Junio de 2014.

Ordenador ZONE EVIL con procesador Intel i5 4460, 8GB de RAM, 1TB de disco duro.
Dispone de multilector de tarjetas y Grabadora de DVD.
Mejor accesibilidad con USB 3.0 FRONTAL.

TIPO CAJA Slim
COLOR Negro
PUERTOS 1 x USB 3.0 FRONTAL, 1 x USB 2.0 FRONTAL , 1 x Audio, 1 x Mic
DIMENSIONES 410 x 100 x 306
Fuente ALIMENTACIÓN: 85 % EFICIENCIA (Cumpliendo Normativa Europea para equipos nuevos)

Intel Core i5 4460 3.2Ghz

Modelo del procesador* i5-4460
Frecuencia del procesador* 3,2 GHz
De caché L3 6 MB

Memoria 8GB 1600Mhz HYPERX
Memoria interna* 8 GB
Tipo de memoria interna* DDR3
Velocidad de memoria del reloj* 1600 MHz


Disco duro 1TB 7200 RPM
Interfaz del disco duro* Serial ATA III
Capacidad de disco duro* 1000 GB
Velocidad de rotación de disco duro* 7200 RPM

LG GH24NSC0 Grabadora DVD 24x Negra

PLACA BASE GIGABYTE H81M-S2H

Puertos HDMI, DVI y D-SUB en panel posterior
GIGABYTE On/Off Charge™ para dispositivos USB

Chipset Intel® H81 Express

Memoria soporta hasta:
2 x socket DIMM DDR3 con capacidad para 16 GB de memoria de sistema
Arquitectura de memoria Dual Channel

Gráfica Integrada
Procesador gráfico integrado – Soporte Intel® HD Graphics:
1 x HDMI port, supporting a maximum resolution of 4096x2160
* Support for HDMI 1.4a version.
1 x puerto DVI-D, que soporta una resolución máxima de 1920x1200
*El puerto DVI-D no soporta conexión D-Sub por adaptador.
1 x puerto D-Sub, que soporta una resolución máxima de 1920x1200
Máxima memoria compartida: 1 GB.

Audio
Realtek® ALC887 codec
Audio de alta definición
2/4/5.1/7.1-channel
* Para configurar el audio de 7.1 canales, tiene que utilizar un módulo frontal de audio HD y activar la función de múltiples canales de audio a través del controlador de audio.

LAN
Chip Realtek® GbE LAN (10/100/1000 Mbit)


Panel E/S Trasero
1 x puerto RJ-45
2 x puerto USB 2.0/1.1
4 x puerto USB 3.0/2.0
1 x HDMI
1 x DVI-D
3 x jacks de audio (Line In, Line Out, Mic In)
1 x puerto de ratón PS / 2
1 x puerto de Teclado PS / 2
1 x puerto D-Sub

Conectores Internos E/S
1 x conector del puerto de serie
1 x USB 3.0/2.0
1 x conector Trusted Platform Module (TPM)
*La función TPM es opcional según las diferentes políticas locales
1 x conector de alimentación ATX 12V de 4-pin
1 x conector del ventilador de la CPU
1 x conector del panel frontal
1 x conector de alimentación principal ATX 24-pin
1 x conector de audio en el panel frontal
1 x conector del ventilador del sistema
2 x conectores USB 2.0/1.1
1 x Clear CMOS jumper
2 x conector SATA 3Gb/s
2 x conector SATA 6Gb/s

```

Thank you very much. 
It's very obvious now, I don't have a WIFI card. That is why it doesn't work. :-) 

This is the first desktop PC (non laptop) I buy, so I didn't know they don't come with onboard WIFI. 
It's very very clear now, and I'm grateful for your help. I had considered this option since my first post, but didn't really know how to check it. 

I'll now buy an USB dongle. 

Thank you!!!

---

