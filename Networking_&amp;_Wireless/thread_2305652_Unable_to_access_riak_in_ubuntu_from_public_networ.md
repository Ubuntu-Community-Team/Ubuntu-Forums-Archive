---
title: "Unable to access riak in ubuntu from public network"
date: 2015-12-08
forum: Networking &amp; Wireless
---

### Post by Ayash_Kant_Baral on 2015-12-08
Hi I have installed ubuntu in oracle virtual box.
Then i have installed riak in ubuntu.
After that i have started riak. so when hit [http://127.0.0.1:8098/riak](http://127.0.0.1:8098/riak) in ubuntu it gives back response to me. Since i need riak to be accessed from public ip address how will do that.
because i tried to check the ifconfig command which shows inet address as 10.0.2.15
so when i tried from my windows browser typing [http://10.0.2.15:8098/riak](http://10.0.2.15:8098/riak) it says "[h=1]This webpage is not available[COLOR=#222222][FONT=Verdana]"[/FONT][/COLOR][/h]Even same response when i try for [http://127.0.0.1:8098/riak](http://127.0.0.1:8098/riak) from window.

Your help will be most welcome.

---

### Post by TheFu on 2015-12-08
Use **bridge** networking for the VM, not NAT or Host-only.

---

### Post by Ayash_Kant_Baral on 2015-12-10
Hi ,

When i tried with bridge networking at office, i could not able to connect to internet at all inside virtual box.
But when  tried same at home, i could able to connect to internet. But when i typed ifconfig , i got inet address as 192..168.0.6 , with this when i tried to check [http://192.68.0.6:8098/riak]("http://10.0.2.15:8098/riak") this gives me 504 gateway time out.

so my problem remains same. i couldn't access riak running inside virtual box from windows.

Thanks in advance

---

### Post by TheFu on 2015-12-10
If you want help, we need more facts and data. From both the hostOS and the client.  
* ifconfig/ipconfig
* route print/route
* There are many different networking modes in vbox which is active? 
* firewall settings on host and guest OS?

I don't know anything about riak - is there a built-in web server that should be brought up or is something more needed?  Most DBMS do not have a webserver.

---

### Post by TheFu on 2015-12-10
double post.

---

### Post by Ayash_Kant_Baral on 2015-12-11
Hi, 
So far thanks for your help.
 
here i put my details of the system. By the way virtual box is running in NAT networking mode.

Host system details (i.e. Windows)


Ethernet adapter Bluetooth Network Connection:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


Wireless LAN adapter Wireless Network Connection:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : in-101.lan.philips.com


Ethernet adapter Local Area Connection:


   Connection-specific DNS Suffix  . : in-101.lan.philips.com
   Link-local IPv6 Address . . . . . : fe80::c558:fc72:d5ef:c2cd%13
   IPv4 Address. . . . . . . . . . . : 161.85.103.145
   Subnet Mask . . . . . . . . . . . : 255.255.255.128
   Default Gateway . . . . . . . . . : 161.85.103.129

route details of host system(i.e. windows)

C:\Users\310207513>route print
===========================================================================
Interface List
 16...a0 a8 cd e8 fb d8 ......Bluetooth Device (Personal Area Network)
 14...a0 a8 cd e8 fb d4 ......Intel(R) Dual Band Wireless-AC 7260
 13...64 51 06 a1 08 35 ......Intel(R) Ethernet Connection I218-LM
 27...0a 00 27 00 00 00 ......VirtualBox Host-Only Ethernet Adapter
 23...00 50 56 c0 00 01 ......VMware Virtual Ethernet Adapter for VMnet1
 24...00 50 56 c0 00 08 ......VMware Virtual Ethernet Adapter for VMnet8
  1...........................Software Loopback Interface 1
 18...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter
 22...00 00 00 00 00 00 00 e0 Microsoft 6to4 Adapter
 12...00 00 00 00 00 00 00 e0 Microsoft Teredo Tunneling Adapter
 19...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #2
 20...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #3
 21...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #4
 25...00 00 00 00 00 00 00 e0 Microsoft ISATAP Adapter #5
===========================================================================


IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0   161.85.103.129   161.85.103.145     20
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
   161.85.103.128  255.255.255.128         On-link    161.85.103.145    276
   161.85.103.145  255.255.255.255         On-link    161.85.103.145    276
   161.85.103.255  255.255.255.255         On-link    161.85.103.145    276
      169.254.0.0      255.255.0.0         On-link   169.254.198.220    266
  169.254.198.220  255.255.255.255         On-link   169.254.198.220    266
  169.254.255.255  255.255.255.255         On-link   169.254.198.220    266
      192.168.6.0    255.255.255.0         On-link       192.168.6.1    276
      192.168.6.1  255.255.255.255         On-link       192.168.6.1    276
    192.168.6.255  255.255.255.255         On-link       192.168.6.1    276
     192.168.67.0    255.255.255.0         On-link      192.168.67.1    276
     192.168.67.1  255.255.255.255         On-link      192.168.67.1    276
   192.168.67.255  255.255.255.255         On-link      192.168.67.1    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link    161.85.103.145    276
        224.0.0.0        240.0.0.0         On-link   169.254.198.220    266
        224.0.0.0        240.0.0.0         On-link      192.168.67.1    276
        224.0.0.0        240.0.0.0         On-link       192.168.6.1    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link    161.85.103.145    276
  255.255.255.255  255.255.255.255         On-link   169.254.198.220    266
  255.255.255.255  255.255.255.255         On-link      192.168.67.1    276
  255.255.255.255  255.255.255.255         On-link       192.168.6.1    276
===========================================================================
Persistent Routes:
  None


IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 22   1125 ::/0                     2002:c058:6301::c058:6301
  1    306 ::1/128                  On-link
 22   1025 2002::/16                On-link
 22    281 2002:a155:5d5a::a155:5d5a/128
                                    On-link
 22    281 2002:a155:6791::a155:6791/128
                                    On-link
 13    276 fe80::/64                On-link
 27    266 fe80::/64                On-link
 23    276 fe80::/64                On-link
 24    276 fe80::/64                On-link
 23    276 fe80::8db:7920:547b:784b/128
                                    On-link
 27    266 fe80::5062:da9f:3033:c6dc/128
                                    On-link
 24    276 fe80::a0ff:880a:aed4:5623/128
                                    On-link
 13    276 fe80::c558:fc72:d5ef:c2cd/128
                                    On-link
  1    306 ff00::/8                 On-link
 13    276 ff00::/8                 On-link
 27    266 ff00::/8                 On-link
 23    276 ff00::/8                 On-link
 24    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None



There is not firewall on ubuntu inside virtual box. but in windows , yes i have firewall.

Ifconfig for guest os.(i.e Ubuntu)

[FONT=arial]eth0      Link encap:Ethernet  HWaddr 08:00:27:59:9e:43  [/FONT]
[FONT=arial]          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0[/FONT]
[FONT=arial]          inet6 addr: fe80::a00:27ff:fe59:9e43/64 Scope:Link[/FONT]
[FONT=arial]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=arial]          RX packets:116 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=arial]          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=arial]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=arial]          RX bytes:15334 (15.3 KB)  TX bytes:39292 (39.2 KB)[/FONT]

[FONT=arial]lo        Link encap:Local Loopback  [/FONT]
[FONT=arial]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=arial]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=arial]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=arial]          RX packets:715 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=arial]          TX packets:715 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=arial]          collisions:0 txqueuelen:0 [/FONT]
[FONT=arial]          RX bytes:57822 (57.8 KB)  TX bytes:57822 (57.8 KB)[/FONT]

[FONT=arial]lxcbr0    Link encap:Ethernet  HWaddr f2:63:bf:7f:67:df  [/FONT]
[FONT=arial]          inet addr:10.0.3.1  Bcast:0.0.0.0  Mask:255.255.255.0[/FONT]
[FONT=arial]          inet6 addr: fe80::f063:bfff:fe7f:67df/64 Scope:Link[/FONT]
[FONT=arial]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=arial]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=arial]          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=arial]          collisions:0 txqueuelen:0 [/FONT]
[FONT=arial]          RX bytes:0 (0.0 B)  TX bytes:9319 (9.3 KB)


route details in ubuntu
[/FONT][FONT=arial]osboxes@osboxes:~$ route [/FONT]
[FONT=arial]Kernel IP routing table[/FONT]
[FONT=arial]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT]
[FONT=arial]default         10.0.2.2        0.0.0.0         UG    1024   0        0 eth0[/FONT]
[FONT=arial]10.0.2.0        *               255.255.255.0   U     0      0        0 eth0[/FONT]
[FONT=arial]10.0.3.0        *               255.255.255.0   U     0      0        0 lxcbr0[/FONT]
[FONT=arial]link-local      *               255.255.0.0     U     1000   0        0 eth0


[/FONT][FONT=arial]Thanks in advance.....

[/FONT]

---

### Post by TheFu on 2015-12-11
**Do not** use NAT for the VM networking.
**Do**       use Bridged for the VM networking.

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html) explains.

BTW, when posting output like that, please, please use "code tags", so thing line up. Too hard to read otherwise. Please edit the post above to add "code tags" from the "Adv Reply" options.

---

