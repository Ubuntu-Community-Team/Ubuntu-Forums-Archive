---
title: "Network from liveCD ?"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by azmrb on 2006-07-28
I would really like to partition and install Ubuntu but after reading all the networking problems people here are having and my experience with the livecd I have little confidence that I can get the ethernet working.

All of the solutions I have seen posted so far involve editing
files and then rebooting which will obviously not work for anyone
using the livecd.

I have booted both the 32 and 64 bit versions and have the same exact problem with my MCP51 ethernet controller.  I can ping local loopback but cannot ping the router which is 192.168.1.1
I have tried using a static address but still no joy.

Here is the output of ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:17:31:A1:06:1D  
          inet addr:192.168.1.212  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fea1:61d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:49 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79440 (77.5 KiB)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xc000 


Here is the output of lspci | grep Eth

0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)


Here is the routing table

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


Here is output of cat /etc/resolv.conf

No such file or director


Here is the output of cat /etc/network/interfaces

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


Here is the output of cat /etc/dhcp3/dhclient.conf

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
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


Here is the ipconfig /all from WindowsXP



Windows IP Configuration



        Host Name . . . . . . . . . . . . : HProcket

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Hybrid

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller

        Physical Address. . . . . . . . . : 00-17-31-A1-06-1D

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 192.168.1.10

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 68.12.16.25

                                            68.2.16.30



NIC is connected by 4' cable to Linksys WRT54G ( which I am fairly certain is not IPV6 enabled ) connected to
a Motorola surfboard modem on Cox Cable internet.

Thanks for the advice, I would really like to explore ubuntu
but am hesitant to repartition my drive unless I know I will
have network access.  If I am a newbie and having this much
problems should I abandon all hope of installing the 64bit
version and just stick with 32bit?

-Bob-

---

### Post by mibadt on 2006-07-29
Hi,
I think your problem stems from the empty /etc/resolv.conf file.
Try to edit it (using sudo nano from the command line), and enter the following lines:

nameserver 192.168.1.1  # your router
nameserver             # enter here the DNS  server IP address of your ISP

you can open the terminal either from the graphical environment, or open a text terminal (ALT+CTRL+1, ALT+CTRL+F7-returns to graphical environment).

Good Luck !:D

---

### Post by azmrb on 2006-07-29
I have the general issue with Dapper having the 0.48 version of forcdeth and I had to not only unplug the computer but disconnect the ethernet cable as well.  

I was able to download updates that have brought me up to version 0.54 of forcedeth.

:D

---

