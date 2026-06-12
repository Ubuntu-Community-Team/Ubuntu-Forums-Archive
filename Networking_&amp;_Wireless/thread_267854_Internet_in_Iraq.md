---
title: "Internet in Iraq"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by tsarscott on 2006-09-29
This might be an unusual problem. I have internet in my room here in the FOB. I have managed to get Windows online. In windows I had to add a broadband connection and have LAN running to get out. The Broadband conn. is PPPoE which I am assuming is to their router. The LAN has all the DNS and IP addresses. I am wondering what I am going to have to do to get Ubuntu online. I am pretty much a noob.

---

### Post by mips on 2006-09-29
What hardware are you using, modem/router model etc ???
How is the above hardware configured ??? Physical diagram, with connection types (USB/Ethernet etc) and IP addresses etc always help.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by DirtDawg on 2006-09-29
Have you tried the live cd to see how it reacts?

Sorry if this is obvious, but I thought I would suggest.

---

### Post by tsarscott on 2006-09-30
Between a slow connection and running missions here, this may take a while. I appreciate any help I can get. I have used several versions of Ubuntu but for the last 5-6 months haven't, now that I'm in my new home for the next year it is time to use it again.
 
Here is my Windows ipconfig:
Windows IP Configuration

        Host Name . . . . . . . . . . . . : dell
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-14-22-F0-BD-86
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.20.0.21
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 10.20.0.1
        DNS Servers . . . . . . . . . . . : 10.20.0.1
                                            4.2.2.2
                                            195.146.32.1
        Lease Obtained. . . . . . . . . . : Saturday, September 30, 2006 10:48:2
8 AM
        Lease Expires . . . . . . . . . . : Tuesday, October 03, 2006 10:48:28 A
M

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-16-CE-27-D0-3C

PPP adapter Fox:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.105
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 192.168.1.105
        DNS Servers . . . . . . . . . . . : 192.168.0.1
                                            4.2.2.2
        NetBIOS over Tcpip. . . . . . . . : Disabled


**Hopefully this will give you some ideas.Below is some of my system info.**



System
Host Name : DELL
User : Scott
Workgroup : MSHOME

Processor
Model : Genuine Intel(R) CPU           T2300  @ 1.66GHz
Speed : 1.66GHz
Cores per Processor : 2 Unit(s)
Threads per Core : 1 Unit(s)
Type : Mobile, Dual-Core
Internal Data Cache : 2x 32kB Synchronous, Write-Thru, 8-way set, 64 byte line size
L2 On-board Cache : 2MB ECC Synchronous, ATC, 8-way set, 64 byte line size, 2 threads sharing

Mainboard
Bus(es) : ISA X-Bus PCI PCIe USB FireWire/1394 i2c/SMBus
MP Support : No
MP APIC : No
System BIOS : AT/AT COMPATIBLE DELL   - 27d50c11
Mainboard : Dell Inc. 0YD479
Total Memory : 1023MB DDR2-SDRAM

Chipset 1
Model : Dell Computer Corp Mobile Memory Controller Hub
Front Side Bus Speed : 4x 166MHz (664MHz data rate)
Total Memory : 1GB DDR2-SDRAM
Memory Bus Speed : 4x 132MHz (528MHz data rate)

Video System
Monitor/Panel : Default Monitor
Monitor/Panel : Default Monitor
Monitor/Panel : Default Monitor
Monitor/Panel : Default Monitor
Monitor/Panel : Default Monitor
Monitor/Panel : Default Monitor
Adapter : ATI Mobility Radeon X1400 
Imaging Device : USB PC Camera (SN9C103) #2

Physical Storage Devices
Hard Disk : TOSHIBA MK8032GSX (73GB)
Hard Disk : Secure Digital Storage Device
Hard Disk : Fujifilm USB Drive USB Device
CD-ROM/DVD : SONY DVD+-RW DW-Q58A (CD 63X Rd, 63X Wr) (DVD 8X Rd, 8X Wr)

Logical Storage Devices
Hard Disk (C:) : 68GB (41GB, 60% Free Space) (NTFS)


Peripherals
USB Controller/Hub : Intel(R) 82801G (ICH7 Family) USB Universal Host Controller - 27C8
USB Controller/Hub : Intel(R) 82801G (ICH7 Family) USB Universal Host Controller - 27C9
USB Controller/Hub : Intel(R) 82801G (ICH7 Family) USB Universal Host Controller - 27CA
USB Controller/Hub : Intel(R) 82801G (ICH7 Family) USB Universal Host Controller - 27CB
USB Controller/Hub : Intel(R) 82801G (ICH7 Family) USB2 Enhanced Host Controller - 27CC
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Root Hub
USB Controller/Hub : USB Composite Device
USB Controller/Hub : USB Mass Storage Device
USB Controller/Hub : USB Composite Device
USB Controller/Hub : Generic USB Hub
FireWire/1394 Controller/Hub : OHCI Compliant IEEE 1394 Host Controller
Keyboard : Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse : Synaptics PS/2 Port Pointing Device
Mouse : Logitech HID-compliant Cordless Mouse
Human Interface : HID-compliant consumer control device
Human Interface : HID-compliant device
Human Interface : HID-compliant device
Human Interface : USB Human Interface Device
Human Interface : USB Human Interface Device

Communication Device(s)
Device : Conexant HDA D110 MDC V.92 Modem


Power Management
AC Line Status : On-Line
Battery No 1 : 100%

Operating System(s)
Windows System : Microsoft Windows XP/2002 Professional Media Center 5.01.2600 (Service Pack 2)

Network Services
Adapter : Broadcom 440x 10/100 Integrated Controller
Adapter : Dell Wireless 1390 WLAN Mini-Card

---

### Post by tsarscott on 2006-09-30
b

---

### Post by tsarscott on 2006-09-30
Here is my Ubuntu info:
eth0      Link encap:Ethernet  HWaddr 00:14:22:F0:BD:86
          inet addr:10.20.0.21  Bcast:10.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::214:22ff:fef0:bd86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5258 errors:6 dropped:2 overruns:0 frame:3
          TX packets:1119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:656137 (640.7 KiB)  TX bytes:72486 (70.7 KiB)
          Interrupt:177


0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.20.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth0

nameserver 10.20.0.1
nameserver 4.2.2.2
nameserver 195.146.32.1

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

cott@scott-laptop:~$ cat /etc/dhcp3/dhclient.conf
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

---

### Post by tagra123 on 2006-09-30
This might help.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29)

Thank you for your service. Two of my cousins are in Iraq and one in Afghanistan.

---

