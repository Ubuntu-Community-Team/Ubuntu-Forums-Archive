---
title: "internet  sharing on ubuntu 5.04"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by jrev on 2005-06-22
I tried an Internet sharing :

I connected my desktop to my laptop through a crossover cable and gave fixed addresses to both of them : the ping command is OK both ways

then I did the procedure indicated in the unofficial guide but cannot go further.

My desktop connects OK to the Net but there is no transmission(or very little) on the line

my question : how can I disable my local network at bootup ? (it's on now)

if I suppress networking in init.d I cannot reach the desktop and must switch off to reboot

thanks for your help :-|

---

### Post by jrev on 2005-06-26
Hello guys,

Has anybody succeeded to install a lan on ubuntu 5.04 between two computers ?

Could he tell us which commands he used ...

thanks for the help

---

### Post by Gmrx on 2005-06-27
I'd like some help with this as well

---

### Post by jrev on 2005-06-27
there is a tuto on the french wiki of Ubuntu and I am following it with the author on Line.
Everything seems OK & I am waiting for his diag...

if we succed I can translate it into english for the community...

hope we do... :neutral:

Here is the situation on the connection client laptop then on the gateway PC :

when I type an address in my browser no transmission can be seen on the line monitor ...

the net configuration is as follows :

ean@toshiba:~$ route
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
default         athlon          0.0.0.0         UG    0      0        0 eth0


jean@toshiba:~$ ifconfig -a
eth0      Lien encap:Ethernet  HWaddr 00:A0:D1:BB:32:AB
          inet adr:192.168.10.2  Bcast:192.168.10.255  Masque:255.255.255.0
          adr inet6: fe80::2a0:d1ff:febb:32ab/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:300 (300.0 b)  TX bytes:10082 (9.8 KiB)
          Interruption:18 Adresse de base:0xa000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃŽte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:1012525 (988.7 KiB)  TX bytes:1012525 (988.7 KiB)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

et sur le gateway :

jean@athlon:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1-l-1.tnt05.par *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
default         1-l-1.tnt05.par 0.0.0.0         UG    0      0        0 ppp0
jean@athlon:~$


jean@athlon:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:A7:20:A7:1A
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a7ff:fe20:a71a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1046 (1.0 KiB)  TX bytes:378 (378.0 b)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1601594 (1.5 MiB)  TX bytes:1601594 (1.5 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:213.36.129.62  P-t-P:213.36.81.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:220896 (215.7 KiB)  TX bytes:31406 (30.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by cwaldbieser on 2005-06-27
What firewall are either of you using?

---

### Post by jrev on 2005-06-28
No firewall ...

what exactly is the use of it under Linux ?
We want to start with the simple thing then we can progress at our speed 

I Know now howto build the simplest internet sharing...

if you want to make the next tuto ?

could be how to share your files & folders on Ubuntu samba

---

### Post by cwaldbieser on 2005-06-28
Well, the easy way to do Internet Connection Sharing is to get the Firestarter firewall from the repositories and enable Internet Connection Sharing in its preferences.

Package is "firestarter".
Edit --> Preferences --> Firewall --> Enable Internet Connection Sharing.

This is a convenient from end for Netfilter (which is part of the kernel).  iptables is a command line tool for manipulating Netfilter.  It is more flexible, but requires more setup on the part of the user.  Firewalls like Shorewall are also considered pretty good, but Firestarter has a nice GUI for beginners.

---

### Post by jrev on 2005-07-01
OK I got it working and made a howto in french (2 A4 pages) so that my network is setup at boot time automatically 
my configuration is 2 PC's directly linked together through the ethernet card
 anybody interested can contact me on this site...
 :-P

---

### Post by Havoc on 2005-07-01
Yes please! Do translate it! Many are having problems with Internet Sharing (Between XP and Hoary)!

---

### Post by jrev on 2005-07-02
I did it with one desktop and a laptop both on the same OS : ubuntu 5.04 

may be you can do the next one : same connection but one Ubuntu & the other win XP 

 ;-)

---

### Post by reid on 2005-07-03
[QUOTE=Gmrx]I'd like some help with this as well[/QUOTE]

I set it up with firestarter.  It was fairly easy, except I had to  fiddle with the gateways and what not.  I have the win machine connected with a crossover.  My ubuntu machine is on DHCP from a router but stays at 192.168.100.2.  The second (internal) NIC on the ubuntu box has the static address of 192.168.1.100.  The win machine is set as a static IP on the internal network as 192.168.1.5, with the default gateway as 192.168.1.100 (the IP of the NIC on the ubuntu box it is connected to).  The win DNS is set to my ISP's DNS servers.
In case you want to see it in a table format ---
Here is the ubuntu box:
```
reid@nubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0

``` The gateway on the ubuntu box is the internal IP address of my router (192.168.100.1).

Or if this helps better (wlan0 is external and eth0 is connected to the win box)):
```

reid@nubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:03:1C:A3:60
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe1c:a360/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4282170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6425778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1234243308 (1.1 GiB)  TX bytes:4002740052 (3.7 GiB)
          Interrupt:18 Base address:0xc000

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:D1:4E:0E
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fed1:4e0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:11532568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10013290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3823482875 (3.5 GiB)  TX bytes:827496557 (789.1 MiB)

```
Here is the win box:
```
C:\Documents and Settings\reid>ipconfig
Windows IP Configuration
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.100


```


I am not sure that they need to be seperate networks, this is just how I got it to work.  If anyone has any comments on a different/better way to do this, please enlighten us.

HTH,

Reid

---

