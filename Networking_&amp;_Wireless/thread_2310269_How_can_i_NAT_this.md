---
title: "How can i NAT this?"
date: 2016-01-17
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2016-01-17
I have a Raspbery pi Zero setup to use the USB port as a USB network so it shows up as usb ethernet on my ubuntu system, i would like to NAT my network connection to it so i can install packages over ssh
* the MAC address on usb0 changes every time i connect my pi, i am hopeing i can setup a DHCP server on the PI to assign a address i can use since i can't make a static without a static mac address
```
ifconfig 
eth3      Link encap:Ethernet  HWaddr 00:1b:21:85:2d:8b  
          inet addr:10.0.0.50  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe85:2d8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4218748 errors:0 dropped:40 overruns:0 frame:0
          TX packets:2775622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5186096412 (5.1 GB)  TX bytes:227108065 (227.1 MB)
          Interrupt:19 Memory:ef140000-ef160000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3356544 (3.3 MB)  TX bytes:3356544 (3.3 MB)

usb0      Link encap:Ethernet  HWaddr ae:b1:e6:0f:56:38  
          inet addr:169.254.64.63  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::acb1:e6ff:fe0f:5638/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4750 (4.7 KB)  TX bytes:186917 (186.9 KB)
sudo lsusb -d 0525:a4a2 -vv
Bus 001 Device 020: ID 0525:a4a2 Netchip Technology, Inc. Linux-USB Ethernet/RNDIS Gadget
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0525 Netchip Technology, Inc.
  idProduct          0xa4a2 Linux-USB Ethernet/RNDIS Gadget
  bcdDevice            4.04
  iManufacturer           1 Linux 4.4.0+ with 20980000.usb
  iProduct                2 RNDIS/Ethernet Gadget
  iSerial                 0 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           75
    bNumInterfaces          2
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass          2 Communications
      bFunctionSubClass       6 Ethernet Networking
      bFunctionProtocol       0 
      iFunction               6 RNDIS
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              4 RNDIS Communications Control
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x00
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x00
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              5 RNDIS Ethernet Data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           88
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass          2 Communications
      bFunctionSubClass       6 Ethernet Networking
      bFunctionProtocol       0 
      iFunction              11 CDC ECM
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      6 Ethernet Networking
      bInterfaceProtocol      0 
      iInterface              8 CDC Ethernet Control Model (ECM)
      CDC Header:
        bcdCDC               1.10
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      CDC Ethernet:
        iMacAddress                      9 aeb1e60f5638
        bmEthernetStatistics    0x00000000
        wMaxSegmentSize               1514
        wNumberMCFilters            0x0000
        bNumberPowerFilters              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface             10 CDC Ethernet Data
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by Doug S on 2016-01-18
Hi pq...bla bla,
it has been awhile.

Please clarify, on which side is the gateway to internet? The eth3 side or the usb0 side?

---

### Post by Doug S on 2016-01-19
Try this (untested):
```
#!/bin/sh
FWVER=0.01
#
# test-pq rule set 2016.01.19 Ver:0.01
#     A simple router for pqwoerituytrueiwoq's case.
#     Check the direction for the internet facing I/F.
#
#     References:
#     http://ubuntuforums.org/showthread.php?t=2310269
#
#     run as sudo
#
echo "test-pq rule set version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

# Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth3"
INTIF="usb0"
#EXTIP="10.0.0.50"
# This IP needs to be static so that devices on the LAN can know the gateway
# IP address.
#INTIP="169.254.64.63"  <<< ??? That is one of those weird default link-local IP addresses (RFC 3927)
UNIVERSE="0.0.0.0/0"

echo "  External Interface: $EXTIF  Internal Interface: $INTIF"

#CRITICAL:  Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward

#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to ACCEPT.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
# While my references do not have it, I think this is needed.
$IPTABLES -t nat -Z

#
# FORWARD rules would only be required if the default policy is not ACCEPT
# Included for completeness
echo "FWD: Allow all connections OUT and only existing/related IN..."
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT

#
# Do the actual NAT
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
# The below can be used instead if the EXTIP is static and known.
#$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP

echo test-pq rule set version $FWVER done.

```

---

### Post by pqwoerituytrueiwoq on 2016-01-24
usb0 it not the uplink, eth0 is
i assumed that ip was used in the guide cause no router would use something like that by default

```
chad@Z97K1LLER:~$ sudo sh /tmp/iptabletest.sh
[sudo] password for chad: 
test-pq rule set version 0.01..

  External Interface: eth3  Internal Interface: usb0
Enabling forwarding...
  Clearing any existing rules and setting default policy to ACCEPT..
FWD: Allow all connections OUT and only existing/related IN...
test-pq rule set version 0.01 done.
chad@Z97K1LLER:~$ ssh pi@169.254.64.64
pi@169.254.64.64's password: 

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sat Jan 16 01:43:35 2016 from z97k1ller.local
pi@raspberrypi:~ $ ping 10.0.0.1
connect: Network is unreachable
pi@raspberrypi:~ $ ping google.com
ping: unknown host google.com
pi@raspberrypi:~ $ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21296 (20.7 KiB)  TX bytes:21296 (20.7 KiB)

usb0      Link encap:Ethernet  HWaddr 56:55:ec:95:aa:03  
          inet addr:169.254.64.64  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::1b68:d027:bfaf:f7d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144452 (141.0 KiB)  TX bytes:12663 (12.3 KiB)

pi@raspberrypi:~ $ ping 169.254.64.63 -c 1
ping: icmp open socket: Operation not permitted
pi@raspberrypi:~ $ sudo ping 169.254.64.63 -c 1
PING 169.254.64.63 (169.254.64.63) 56(84) bytes of data.
64 bytes from 169.254.64.63: icmp_seq=1 ttl=64 time=0.215 ms

--- 169.254.64.63 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.215/0.215/0.215/0.000 ms
pi@raspberrypi:~ $ sudo ping 10.0.0.1 -c 1
connect: Network is unreachable
pi@raspberrypi:~ $ sudo ping google.com -c 1
ping: unknown host google.com
pi@raspberrypi:~ $

```
all my ip address are static, also managed to make a static mac address 
[https://gist.github.com/gbaman/50b6cca61dd1c3f88f41](https://gist.github.com/gbaman/50b6cca61dd1c3f88f41) (guide to setup pi as usb ethernet)
[http://linux-sunxi.org/USB_Gadget#Loading_the_driver_.28on_the_device.29](http://linux-sunxi.org/USB_Gadget#Loading_the_driver_.28on_the_device.29) (static mac)

---

### Post by Doug S on 2016-01-30
Where did eth3 go?
And you still need a legal IP address for usb0.

EDIT: Oh. I didn't read thoroughly. I do not know what is wrong. However, I would suggest to try making a real local sub-net. Does "route" on the pi reveal anything?

---

### Post by pqwoerituytrueiwoq on 2016-01-30
[URL="http://i.imgur.com/xSiV1Wl.png"]
  [IMG]http://imgur.com/xSiV1Wll.png[/IMG]
[/URL]
edit:
i  changed my pi's address to 10.1.0.2 and my desktop's usb ip to 10.1.0.1 (aside from being easier to type than my name)
it had no effect
edit: my pi can ping my desktop at eth3, not nothing past that

---

### Post by Doug S on 2016-01-31
Get rid of the link-local stuff. Change that to a real valid local sub-net, say 192.168.213.0/24 (where the 213 part was arbitrarily chosen).

---

