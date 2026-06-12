---
title: "No Ethernet Connection Except when starting Admin&gt;networking"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by JimPennell on 2006-11-24
This is a new install of Ubuntu 6.06 LTS

I am not able to connect to my ethernet router like quite a few posts I have seen here.  I have tried disabling ipv6.  DHCP does not discover my router.

I use this exact hardware under windows and it works. 

So, I set for static IP and verified the IP address and configuration to connect to my router.  I also checked the route IP address and I manually added my router IP to the route table.

I did notice one very strange clue.  I happened to leave the computer attempting to download updates while I went to ADMINISTRATOR>NETWORKING and, for perhaps 1 second, I got a great connection and downloaded one or two of the update files.

However, once the networking control program finished starting, I lost the internet again.

This is repeatable, and it all seems as if there is some other program actively blocking the ethernet connection, but it is temporarily suspended while the networking gui is starting.

The same behavior shows if I run the liveCD and attempt to use firefox to connect to the internet.  It works only for a second, at most, while the networking GUI is setting up.

At this stage, I am stuck.  Any suggestions ?

  Thanks, Jim Pennell

22:25 Pacific Time Zone
Nov 23 2006

International Time
06:25 UTC
24.11.2006

---

### Post by gosh on 2006-11-24
what does your /etc/network/interfaces looks like?

---

### Post by JimPennell on 2006-11-24
I do apologise.  I should have added the Linux configurations to my first message.  Ah well....

I do have one more possible clue.   Linux DID know I needed updates, and it got my Internet hosts name and name servers so, at least at bootup, it tlaked to the internet for a few seconds.  That puzzled me, since I also saw that ALL DHCPoffers did not find the DHCP server.





jim@jim-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:D4:D3:54:90
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1166 (1.1 KiB)  TX bytes:1358 (1.3 KiB)
          Interrupt:161 Base address:0x8000


jim@jim-desktop:~$ lspci | grep Eth
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


jim@jim-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


jim@jim-desktop:~$ cat /etc/resolv.conf
search hsd1.ca.comcast.net.
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 68.87.76.178
nameserver 68.87.78.130



jim@jim-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0




jim@jim-desktop:~$ cat /etc/dhcp3/dhclient.conf
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
#send dhcp-client-identifier 1:0:
a0:24:ab:fb:9c;
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
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;




===========================================================

Windows IP Configuration



        Host Name . . . . . . . . . . . . : Jim-Home
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : hsd1.ca.comcast.net.



Ethernet adapter Local Area Connection:


        Connection-specific DNS Suffix  . : hsd1.ca.comcast.net.
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-13-D4-D3-54-90
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 68.87.76.178
                                            68.87.78.130

        Lease Obtained. . . . . . . . . . : Thursday, November 23, 2006 12:41:13 PM
        Lease Expires . . . . . . . . . . : Monday, January 18, 2038 7:14:07 PM










-- 

10:00 Pacific Time Zone
Nov 24 2006

International Time
18:00 UTC
24.11.2006

---

### Post by Metaljaz on 2006-11-24
Also running Ubuntu 6.06 LTS Dapper
i am having the same problem. I was connected fine last night but can't do anything today. the settings seem to be the same. I manually set static ip still nothing. switched back to DHCP nothing. pinged router had results. In internet properties i see lo, wlan and eth0. wlan and eth0 are active. 
totally confused to the point that i did a reinstall..still nothing...Help needed here to,

---

### Post by r.cannell on 2006-11-26
I am also having similar problems. I have a static IP address and am connecting via a router. Sometimes, usually when coming out of hibernate, the ethernet card does nothing (the router LED not lit). Rebooting in XP proves that the card is OK. Reboot again in Ubuntu and nothing. I removed the card and rebooted in Ubuntu, then shut down, refitted the card and rebooted Ubuntu - the card now works. Could there be a driver problem that is overcome by reinstalling the card? 
I have two ethernet cards, one is on the motherboard so can't be removed and refitted and I can no longer get it to work in Ubuntu - I have disabled it. The other is in a PCI slot.

Can anyone help, please?

---

### Post by Iowan on 2006-11-26
Jim:
Make a backup copy of your **/etc/network/interfaces** file...
```
cp /etc/network/interfaces /etc/network/interfaces.bak
```
Remove (or comment out - #) any interfaces your machine does not have - eth1, eth2, wlan0 ath0...). Try setting eth0 for DHCP again, see if it makes any difference.

If **ifconfig** shows no ip address, try ```
dhclient
``` then see if **ifconfig** shows an ip address.

---

### Post by JimPennell on 2006-11-27
I commented out the other interfaces, but I am sorry to say that did not fix the problem.   I even tried a complete reboot.

Using my original interfaces file, I do see that ethtool shows the link is up and that there have been both outgoing and incoming packets.

Why the rest of Ubuntu does not like the Rx packets is a mystery to me.  

I will have access to my work computer tomorrow and I will examine it's various network configuration files.  Since that system is working, it might give me some ideas for things to try.


        Jim
-- 

22:57 Pacific Time Zone
Nov 26 2006

International Time
06:57 UTC
27.11.2006

---

