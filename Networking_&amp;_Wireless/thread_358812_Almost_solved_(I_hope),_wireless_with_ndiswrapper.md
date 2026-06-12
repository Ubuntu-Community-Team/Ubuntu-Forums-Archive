---
title: "Almost solved (I hope), wireless with ndiswrapper"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-02-11
I have a netgear WG111v2 dongle and I've downloaded and installed (using ndiswrapper) the driver from there website (something funny is wrong with my CD-ROM but that's another, less important problem).
I get this from sudo ndiswrapper -l :
```

net111v2 : driver installed
        device (0846:6A00) present

```
Which is all good an well, but the blue light doesn't light up on the dongle and by other reports it should.

But this is the real problem, when I run sudo ndiswrapper -m I get:
```

module configuration contains directive install usb:v0846p4220d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 400.
module configuration contains directive install usb:v0846p4240d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper line 713, <MODPROBE> line 401.
module configuration already contains alias directive

```

I'm not using the ndiswrapper from the repository, I'm using the newest stable one from sourceforge. Any ideas on how to fix this. I'm going to try a make clean and then a make install and try again but I don't think that will fix it.

Any ideas?

---

### Post by malfist on 2007-02-11
did work
tryed using sudo ndiswrapper -d 0846:6a00
and sudo ndiswrapper -d 0846:6A00
and neither work, syntax error

---

### Post by malfist on 2007-02-11
I don't see any wlan devices sense I removed the *rt818* driver.

---

### Post by malfist on 2007-02-11
I see wlan0 on restart but still no lights and not working. Maybe it is network configure issuse only. Let us see.

---

### Post by malfist on 2007-02-11
not quiet working,it may be my inablility to configure a network, any good tutorials?
DHCP request is always returning nothing.

---

### Post by corax on 2007-02-11
Hi ! 

Please post what is the output of:

```
ifconfig wlan0
```

and the output of:

```
iwconfig wlan0
```

---

### Post by malfist on 2007-02-11
```

jerome@ubuntu:~$ sudo iwconfig wlan0
Password:
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and
```

jerome@ubuntu:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:6C:5F:CB:67
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by malfist on 2007-02-12
Any ideas?

---

### Post by sumgi on 2007-02-12
> **malfist said:**
> not quiet working,it may be my inablility to configure a network, any good tutorials?
DHCP request is always returning nothing.

This is a good wireless debug guide.
[TroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Also you can tail you system logs.

tail -f /var/log/messages

---

### Post by corax on 2007-02-13
Hi ! 

It seems fine ...

Try this :

0, ```
iwlist wlan0 scan
```

  - you can find all informations about accesspoints on your area

1, ```
sudo iwconfig wlan0 essid "youressid" key off channel x
```

  - where youressid is your essid :), key off (turn off every encryption for testing on your accesspoint (you can leave MAC filtering on )), x is your router's channel

2, ```
sudo ifconfig wlan0 up
```

  - to be sure it is switched on ...

3, ```
sudo dhclient wlan0
```

  - then you will get ip address

This above works for me but I don't use cards with ndiswrapper (i have an atheros and an ipw2200) but as i see your card is recognised you just have to connect ...

---

### Post by malfist on 2007-02-14
No luck, checking the tutorial now.

```

jerome@ubuntu:~$ sudo iwconfig wlan0 essid "hollonet" key off channel 6

```
returns nothing

```

jerome@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     No scan results

```
both before and after config

```

jerome@ubuntu:~$ sudo ifconfig wlan0 up

```
returns nothing

```

jerome@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:14:6c:5f:cb:67
Sending on   LPF/wlan0/00:14:6c:5f:cb:67
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

and
```

jerome@ubuntu:~$ sudo tail -f /var/log/messages
Feb 14 17:37:25 localhost syslogd 1.4.1#17ubuntu7: restart.

```
Never finishs with or without sudo, it gets that far and just stops.

---

### Post by sumgi on 2007-02-14
malfist try removing the quotes around your essid when you run iwconfig.

> 
jerome@ubuntu:~$ sudo iwconfig wlan0 essid hollonet key off channel 6


If you get an error, remove the key part and run them seperately.

> 
jerome@ubuntu:~$ sudo iwconfig wlan0 essid hollonet channel 6.
jerome@ubuntu:~$ sudo iwconfig wlan0 key off.


you may need to simply open up the Network Console, System ..> Administration ..> Networking. Enter in your wireless information there.

---

### Post by malfist on 2007-02-14
Router info
```

 	MAC Address:  	00:18:F8:58:60:E7  	   	 
  	  	  	Mode: 	Mixed 11/54Mbps  	  	 
  	  	  	SSID: 	hollonet  	  	 
  	  	  	DHCP Server: 	Enable 	  	 
  	  	  	Channel: 	11  	  	 
  	  	  	Encryption Function: 	Disable 

```
What I've been trying:
```

jerome@ubuntu:~$ sudo iwconfig wlan0 essid hollonet ap 00:18:F8:60:E7 commit Invalid hardware address 00:18:F8:60:E7
Error for wireless request "Set AP Address" (8B14) :
    invalid argument "00:18:F8:60:E7".
jerome@ubuntu:~$ sudo iwconfig wlan0 essid hollonet ap 00:18:F8:58:60:E7 commit
jerome@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     No scan results
jerome@ubuntu:~$

```

More router info:
Wireless Network Mode:     	     Mixed 
Wireless Network Name (SSID): 	 hollonet  	 
Wireless Channel: 	   	  	11 
Wireless SSID Broadcast:            Enabled
Security Mode:                           Null(disabled)
Wireless Mac Filter                      Disabled

Authentication Type:  	    Auto	   	 
Basic Rate: 	                Defualt 	  	 
Transmission Rate: 	   Auto	  	 
CTS Protection Mode: 	  Disable 	  	 
 Frame Burst: 	              Disable 	  	 
 Beacon Interval: 	      100 	  	 
 DTIM Interval: 	        1 	  	 
 Fragmentation Threshold: 	  2346 	  	 
 RTS Threshold: 	      2347	  	 
 AP Isolation: 	                 off 	  	 
 Secure Easy Setup:         enable

It's a linksys WRT54G router

---

### Post by malfist on 2007-02-14
ap is the wirelss MAC for the router, I've also tried with my MAC (off of the dongles sticker), neither works nor does what you said to do.

---

### Post by sumgi on 2007-02-14
Please post the output from the following commands.
[LIST]
[*]sudo lshw -businfo
[*]lspci -v
[*]sudo lsmod
[*]sudo ifconfig
[/LIST]

EDIT:

Ok this is USB

Post output from 

sudo lsusb -v instead of lspci -v

---

### Post by malfist on 2007-02-14
```

jerome@ubuntu:~$ sudo lshw -businfo
Password:
Bus info     Device     Class      Description
==============================================
                        system     "
                        bus        Tabor3 CopperMine WS440BX
                        memory     BIOS
cpu@0                   processor  Pentium III (Coppermine)
                        memory     L1 cache
                        memory     L2 cache
                        memory     System Memory
                        memory     DIMM DRAM Synchronous
                        memory     DIMM DRAM Synchronous
                        memory     DIMM DRAM Synchronous
pci@00:00.0             bridge     440BX/ZX/DX - 82443BX/ZX/DX Host bridge
pci@00:01.0             bridge     440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
pci@01:00.0             display    Rage 128 RF/SG AGP
pci@00:07.0             bridge     82371AB/EB/MB PIIX4 ISA
pci@00:07.1             storage    82371AB/EB/MB PIIX4 IDE
ide@0        ide0       bus        IDE Channel 0
ide@0.0      /dev/hda   disk       ST340810A
ide@0.0,1    /dev/hda1  disk       Linux filesystem partition
ide@0.0,2    /dev/hda2  disk       Extended partition
ide@1        ide1       bus        IDE Channel 1
ide@1.0      /dev/hdc   disk       CD-ROM 24X/AKOx
             /dev/hdc   disk
pci@00:07.2             bus        82371AB/EB/MB PIIX4 USB
usb@1        usb1       bus        UHCI Host Controller
usb@1:1                 generic    NETGEAR WG111v2
pci@00:07.3             bridge     82371AB/EB/MB PIIX4 ACPI
pci@00:0d.0  eth1       network    SMC2-1211TX
             wlan0      network    Wireless interface
jerome@ubuntu:~$

```

lsusb -v
```

jerome@ubuntu:~$ sudo lsusb -v

Bus 001 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0846 NetGear, Inc.
  idProduct          0x6a00 WG111 WiFi (v2)
  bcdDevice            1.00
  iManufacturer           1 NETGEAR WG111v2
  iProduct                2 NETGEAR WG111v2
  iSerial                 3 00146C5FCB67
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Wireless Network Card
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              5 Bulk-IN,Bulk-OUT,Bulk-OUT
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-27-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:07.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0xc0
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered

```
sudo lsmod
```

jerome@ubuntu:~$ sudo lsmod
Module                  Size  Used by
sg                     37920  0
scsi_mod              139496  1 sg
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
apm                    21228  1
r128                   44032  1
drm                    73236  2 r128
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
dm_mod                 58936  1
md_mod                 72532  0
ipv6                  265856  43
af_packet              22920  6
ndiswrapper           187348  0
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
pcspkr                  2180  0
tsdev                   8000  0
floppy                 62148  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
8139too                26880  0
mii                     5888  1 8139too
psmouse                36100  0
serio_raw               7300  0
i2c_piix4               9104  0
i2c_core               21904  1 i2c_piix4
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33808  0
usbcore               130820  3 ndiswrapper,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```
sudo ifconfig
```

jerome@ubuntu:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:E0:29:72:7C:36
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe72:7c36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:123048000 (117.3 MiB)  TX bytes:53304040 (50.8 MiB)
          Interrupt:10 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4296877 (4.0 MiB)  TX bytes:4296877 (4.0 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:5F:CB:67
          inet6 addr: fe80::214:6cff:fe5f:cb67/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by sumgi on 2007-02-14
Alright next I need you to run these commands.

[LIST]
[*]sudo lshw -C network
[*]sudo lshw -C generic
[*]sudo iwconfig
[/LIST]

Also please post the contents of your /etc/network/interfaces file.

[LIST]
[*]gedit /etc/network/interfaces
[/LIST]

---

### Post by malfist on 2007-02-14
lshw network
```

jerome@ubuntu:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth1
       version: 10
       serial: 00:e0:29:72:7c:36
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1400-14ff iomemory:f0000000-f00000ff irq:10
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:5f:cb:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.37 firmware=NETGEAR Inc.,11/20/2006,5.1254. link=no multicast=yes wireless=IEEE 802.11g

```
lshw generic
```

jerome@ubuntu:~$ sudo lshw -C generic
  *-usb
       description: Generic USB device
       product: NETGEAR WG111v2
       vendor: NETGEAR WG111v2
       physical id: 1
       bus info: usb@1:1
       version: 1.00
       serial: 00146C5FCB67
       capabilities: usb-1.10
       configuration: driver=ndiswrapper maxpower=500mA speed=12.0MB/s

```
sudo iwconfig
```

jerome@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
allow-hotplug wlan0

# The primary network interface


iface wlan0 inet dhcp
wireless-essid hollonet
#wireless-key hollon
wireless-channel 11
wireless-mode managed


auto wlan0

iface eth0 inet dhcp



#auto eth0
#Removed, card lost
#iface eth1 inet dhcp



auto eth1
#second ethernet, the newer card, old card is lost!

```

---

### Post by sumgi on 2007-02-14
Alright enter these commands.

[LIST]
[*]sudo ifdown wlan0
[*]sudo ifup wlan0
[*]sudo ifconfig wlan0
[*]sudo iwconfig wlan0
[*]sudo dhclient wlan0
[*]sudo ifconfig wlan0
[/LIST]

---

### Post by malfist on 2007-02-14
ifdown
```

jerome@ubuntu:~$ sudo ifdown wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:14:6c:5f:cb:67
Sending on   LPF/wlan0/00:14:6c:5f:cb:67
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67

```
ifup
```

jerome@ubuntu:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:14:6c:5f:cb:67
Sending on   LPF/wlan0/00:14:6c:5f:cb:67
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
ifconfig
```

jerome@ubuntu:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:6C:5F:CB:67
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
iwconfig
```

jerome@ubuntu:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
dhclient
```

jerome@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:14:6c:5f:cb:67
Sending on   LPF/wlan0/00:14:6c:5f:cb:67
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
ifconfig (again)
```

jerome@ubuntu:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:6C:5F:CB:67
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by sumgi on 2007-02-14
And you had said there was another driver already loaded that this device was using?

---

### Post by malfist on 2007-02-14
No, originally I the *rt818* driver was using it and it worked but it kept kicking me off the computer and to get it to work again I had to restart the computer (reastering network interfaces didn't always work) and everything seemed to go really slow (internet wise). I followed the instructions to fix it sense blacklisting wasn't stopping the driver from grabbing it, I deleted them. Now it doesn't work, bot I've got (I believe) the ndiswrapper working because it says device present but there is not blue light on the dongle (that may be because it isn't connected).

---

### Post by sumgi on 2007-02-14
Well it sounds like that driver at least allowed you to do basic tasks like search for a signal. We might want to look at using that one and debugging from there.

---

### Post by ittiam on 2007-02-14
Even if ndiswrapper is present in lsmod

try doing the following, it worked for me but am not sure

modprobe -r ndiswrapper
modprobe ndiswrapper
iwconfig wlan0 essid your_id (dont specify key off or channel number)
iwconfig

---

### Post by ittiam on 2007-02-14
Even if ndiswrapper is present in lsmod

try doing the following (it may look lame), it worked for me but am not sure

modprobe -r ndiswrapper
modprobe ndiswrapper
iwconfig wlan0 essid your_id (dont specify key off or channel number)
iwconfig

---

### Post by malfist on 2007-02-14
```

jerome@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:160
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It looks like something is there.

---

### Post by malfist on 2007-02-14
but
```

jerome@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:160
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and scaning is still returning no results.

---

### Post by ittiam on 2007-02-14
"iwlist scanning" is returning nothing for you?

---

### Post by malfist on 2007-02-14
aye
```

jerome@ubuntu:~$ sudo iwlist wlan0 scan
Password:
wlan0     No scan results

```

---

### Post by ittiam on 2007-02-14
Output for
> ndiswrapper -r <your_driver>
ndiswrapper - i <your_driver>
dmesg | grep wlan0

---

### Post by malfist on 2007-02-14
```

jerome@ubuntu:~$ ndiswrapper -l
net111v2 : driver installed
        device (0846:6A00) present
jerome@ubuntu:~$ sudo ndiswrapper -r net111v2
Password:
jerome@ubuntu:~/netgear/wg111v2_2_0_1_beta_crn.zip_FILES/Driver/WinXP_2K$ sudo ndiswrapper -i net111v2.inf
driver net111v2 is already installed
jerome@ubuntu:~/netgear/wg111v2_2_0_1_beta_crn.zip_FILES/Driver/WinXP_2K$ dmesg | grep wlan0
[   75.559740] wlan0: ethernet device 00:14:6c:5f:cb:67 using NDIS driver: net111v2, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:6A00.F.conf
[   75.559853] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   86.205695] wlan0: no IPv6 routers present
[10230.303638] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12488.944130] ndiswrapper: device wlan0 removed
[12494.761083] wlan0: ethernet device 00:14:6c:5f:cb:67 using NDIS driver: net111v2, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:6A00.F.conf
[12494.761201] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[12505.747893] wlan0: no IPv6 routers present
jerome@ubuntu:~/netgear/wg111v2_2_0_1_beta_crn.zip_FILES/Driver/WinXP_2K$

```

iwconfig is back to:
```

jerome@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by malfist on 2007-02-14
sorry, wrong driver given to ndiswrapper, retry.
dmesg | grep wlan0
```

jerome@ubuntu:~/netgear/wg111v2_2_0_1_beta_crn.zip_FILES/Driver/WinXP_2K$ dmesg | grep wlan0
[  509.710592] wlan0: ethernet device 00:14:6c:5f:cb:67 using NDIS driver: net111v2, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:6A00.F.conf
[  509.710723] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  520.172568] wlan0: no IPv6 routers present

```
wlist still returns 'No Scan Results'

NOTE: I SAW A BLUE LIGHT FLASH! still no connection though.
Blue light flashs when I do a modprobe ndiswrapper after modprobe -r ndiswrapper.

---

### Post by malfist on 2007-02-14
Actually, I may have disabled IPv6 a while back but I believe I reenabled it. Could that be a problem?

---

### Post by malfist on 2007-02-14
Now it's saying my ethernet connection is not configured and that my wireless is active but when I disconnect the cable it doesn't work. :(

---

### Post by ittiam on 2007-02-14
Hey am sorry!

Tha actually command to remove the driver is

ndiswrapper -e <driver>

once u do ndiswrapper -e drive, install it again.

Sorry for this wrror again!

And u r sure u have got the proper .inf file of ur driver?

---

### Post by ittiam on 2007-02-14
And no disabling IPv6 is not a problem!

---

### Post by malfist on 2007-02-24
Okay I've fixed it. All who use the NetGear WG111v2 USB Dongle, do not use the WinXP_2K driver from their website, use the Win98se instead (it comes in the same zip) it works perfectly.

---

