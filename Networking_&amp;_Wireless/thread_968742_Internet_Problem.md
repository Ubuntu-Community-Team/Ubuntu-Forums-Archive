---
title: "Internet Problem"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by SUBSWISS on 2008-11-02
[SIZE="4"]Hello All..

i post a topic before 2 days ago about make a connection between xp and ubuntu .
and i solved it , but the next problem that I'v got now is i cant use the internet , i mean when i open firefox and write an address cant browsing and also cant make an update or downloading a packeg only  the Pidgin Messenger is working i can make chat normaly and get connect .
so where is the problem i put a pic here about my home network and I'm using ubuntu 8.10

[IMG]http://www.alflash.com/vb/uploaded/67235_01225684819.jpg[/IMG]

plesae need help

Greets
SUB[/SIZE]

---

### Post by cariboo on 2008-11-02
Looking at your diagram is PC4 on a different subnet?

If your network subnet is 192.168.0.1 to 192.168.0.245 then PC4 should be  in the 192.168.1.1 to 192.168.1.254 subnet.

Jim

---

### Post by SUBSWISS on 2008-11-03
> **cariboo907 said:**
> Looking at your diagram is PC4 on a different subnet?

If your network subnet is 192.168.0.1 to 192.168.0.245 then PC4 should be  in the 192.168.1.1 to 192.168.1.254 subnet.

Jim

Hello Jim 
Thanks for your stoping here
the internet line is a dicnamic IP gives only 4 users 
PC1=192.168.1.1
PC2=192.168.1.2
PC3=192.168.1.3(for wireless) and 192.168.0.1 (for Ethernet)
PC4=192.168.0.2 subnet=255.255.255.0
and i cant change the Subnet in PC4 allwasy gives 255.255.255.0 and what is the Broadcast Address in XP mean ? , in ububto BCA is 192.168.0.255

Greets
Sub

---

### Post by SUBSWISS on 2008-11-03
Need help please

---

### Post by superprash2003 on 2008-11-03
in the pc which has the problem.. type ping google.com in the terminal and post output..

---

### Post by SUBSWISS on 2008-11-03
> **superprash2003 said:**
> in the pc which has the problem.. type ping google.com in the terminal and post output..

```
sub@sub-desktop:~$ ping google.com
PING google.com (209.85.171.99) 56(84) bytes of data.


```

this is what i'v got

---

### Post by mips on 2008-11-03
On PC3 go Start->Run and type in 'cmd' and a dos box will open, next type in '**ipconfig /all**' and post the output here.
Have you enabled ICS (Internet connection sharing) on this pc?

On PC4 open a console/cli:
1. Please post output of **ifconfig -a**
2. Please post output of **route -n**
3. Please post output of **cat /etc/resolv.conf**
 4. Please post output of **cat /etc/network/interfaces**
 5. Please post output of **cat /etc/dhcp3/dhclient.conf**

---

### Post by SUBSWISS on 2008-11-03
> **mips said:**
> On PC3 go Start->Run and type in 'cmd' and a dos box will open, next type in '**ipconfig /all**' and post the output here.
first thank you for helping me this is the ifo that you want:


this is the output in PC3

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\acer>ipconfig/all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : xp-1e5bb7c83be8
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Linksys Wireless-G PCI Network Adapt
er with SpeedBooster
        Physical Address. . . . . . . . . : 00-12-17-94-0E-8B
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Sunday, January 04, 2009 8:13:30 AM
        Lease Expires . . . . . . . . . . : Monday, January 05, 2009 8:13:30 AM

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Generic Marvell Yukon Chipset based
Ethernet Controller
        Physical Address. . . . . . . . . : 00-19-21-48-96-91
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :


```

Have you enabled ICS (Internet connection sharing) on this pc?

```
Yes I did 
```

On PC4 open a console/cli:
1. Please post output of **ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 00:30:4f:69:33:d9  
          inet addr:192.168.0.2  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::230:4fff:fe69:33d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:300142 (300.1 KB)  TX bytes:44731 (44.7 KB)
          Interrupt:5 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15980 (15.9 KB)  TX bytes:15980 (15.9 KB)

pan0      Link encap:Ethernet  HWaddr 1a:c8:24:22:60:7c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

2. Please post output of **route -n**
```
sub@sub-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

3. Please post output of **cat /etc/resolv.conf**
```
sub@sub-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1

```

 4. Please post output of **cat /etc/network/interfaces**
```
sub@sub-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

 5. Please post output of **cat /etc/dhcp3/dhclient.conf**
```
sub@sub-desktop:~$ cat /etc/dhcp3/dhclient.conf
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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
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

```

this is the results 
greets
SUB

---

### Post by mips on 2008-11-03
Your configs look good to me.

What happens when you ping 192.168.0.1, 192.168.1.3 & 192.168.1.1 from PC4, output of traceroute would probably show more.

On PC3 have you tried setting the gateway for the Wired interface to 192.168.1.3 or 192.168.1.1 just taking a stab at it.

---

### Post by SUBSWISS on 2008-11-03
> **mips said:**
> Your configs look good to me.

What happens when you ping 192.168.0.1, 192.168.1.3 & 192.168.1.1 from PC4, output of traceroute would probably show more.

On PC3 have you tried setting the gateway for the Wired interface to 192.168.1.3 or 192.168.1.1 just taking a stab at it.

hello again mips

when i ping the IPs allways say (Destination Host Unreachalbe)

and on the PC3 the gateway of the Lan connection is 0.0.0.0 , when i change it to 192.168.1.1 or 192.168.1.3 the internet cant work anymore 
i really dont know what happend :(

---

### Post by superprash2003 on 2008-11-04
open your browser and type 209.85.171.99 in the addressbar.. does google page open?

---

### Post by dbryant32 on 2008-11-04
Hold on...umm..did anyone notice the subnet on the PC4 ifconfig output

 Link encap:Ethernet  HWaddr 00:30:4f:69:33:d9  
          inet addr:192.168.0.2  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::230:4fff:fe69:33d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:300142 (300.1 KB)  TX bytes:44731 (44.7 KB)
          Interrupt:5 Base address:0x3000 

Should it not be 255.255.255.0?

---

### Post by mips on 2008-11-05
> **dbryant32 said:**
> Hold on...umm..did anyone notice the subnet on the PC4 ifconfig output

 Link encap:Ethernet  HWaddr 00:30:4f:69:33:d9  
          inet addr:192.168.0.2  Bcast:192.168.255.255  Mask:255.255.0.0

Should it not be 255.255.255.0?

You are 100% correct, dunno how I missed that. 255.255.0.0 would mean his two networks are actually contigues.

---

### Post by naseemahmadkhan on 2009-02-13
Hi,
I recently installed ubuntu on my dell inspirion. my problem is i am not able to connect to internet using ubuntu. some of ther problem that i can figure out is, there is some sit0 instead of eth0. when i run ./etc/init.d/networking it says 
"Error while getting interface flag".
while if i run lspci |grep -i ethernet it show driver installed. 

i am able to use internet from my vista on the same machine. i have both vista and ubuntu.

i tried to change interface file and made sit0 to eth0 and made it static instead of dhcp. also run networking restart after that.

please someboday tell me what is the problem and how can i run internet or should i simply uninstall unbuntu...i am using ubuntu 6.06

---

