---
title: "D-Link DWL 120 adapter config with 6.06"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by Metaxa on 2006-07-29
Greetings!

I am currently using Ubuntu 6.06. I completed the install and everything works well except for my internet. It see's my wireless adapter, D-Link DWL 120, it loads a driver for it, which is the current driver avalible. When i use the terminal to look up info about the device it shows the device set to the wrong channel/frequency. Next to Access point it reads: Not associated. I do not know what to do next. I downloaded the wifiDocs/WirelessTroubleShootingGuide found in help.ubuntu.com

I do not see how to set teh channel in the guide using teh gui or the terminal, nor do i see how to set the access point.

I have tried to be as specifi as possible but if more information is req'ed please let me know.

Metaxa

---

### Post by Metaxa on 2006-07-29
Here is some info:

hugo@hugo-desktop:~$ sudo ifconfig wlan0
Password:
wlan0     Link encap:Ethernet  HWaddr 00:05:5D:DA:6A:0A
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Bus 002 Device 002: ID 03eb:7603 Atmel Corp. at76c503a D-Link DWL-120 802.11b Ad apter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          254 Application Specific Interface
  bDeviceSubClass         1 Device Firmware Update
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x03eb Atmel Corp.
  idProduct          0x7603 at76c503a D-Link DWL-120 802.11b Adapter
  bcdDevice            1.00
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol    255
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
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
cannot read device status, Operation not permitted (1)

hugo@hugo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

hugo@hugo-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
search 192.168.0.1
hugo@hugo-desktop:~$ cat /etc/network/interfaces\
>
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid 00-0D-88-9B-92-E2



hugo@hugo-desktop:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
hugo@hugo-desktop:~$
hugo@hugo-desktop:~$

Windows output

Windows IP Configuration

	Host name ...hugo
	Primary Dns Suffix...
	Node Type ...Unknown
	IP Routing Enabled...No
	WINS Proxy Enabled...No
Ethernet adapter Wireless Network Connection 2:

	Connection-specific DNS Suffix..:
	Description...D-Link AirPlus DWL-120 Wireless USB adapter
	Physical Address...00-0D-88-88-E4-03
	Dhcp Enabled...Yes
	Autoconfiguration Enabled...Yes
	IP Address...192.168.0.101
	Subnet Mask ...255.255.255.0
	Default gateway ...192.168.0.1
	DHCP Server...192.168.0.1
	DNS servers...192.168.0.1
	lease Obtained...Sat, July 29, 2006
	lease expires...Sat, August 05, 2006




Anything i may have missed please ask for

---

### Post by adamonduty on 2006-07-30
How about iwconfig wlan0 ? That will tell you if you are associated with the access point. If so, try ping 192.168.0.1 .

---

### Post by jISh on 2006-07-30
Hi, see my guide:
[http://www.ubuntuforums.org/showthread.php?t=209315&highlight=dwl-g122](http://www.ubuntuforums.org/showthread.php?t=209315&highlight=dwl-g122)
Hopefully it will help you get that working.

---

### Post by Metaxa on 2006-07-31
Your Thread was great, turns out right where you said to not use default as my ssid i realized that i entered the Mac address of my router, when i corrected that and did put default, it worked. I know that it makes my wireless network less secure, but i live where most people have a poor knowledge of computers. Thanks for the help!



Metaxa

---

