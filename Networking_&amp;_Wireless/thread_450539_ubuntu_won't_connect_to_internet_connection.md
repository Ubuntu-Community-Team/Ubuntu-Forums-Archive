---
title: "ubuntu won't connect to internet connection"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by NiviJah on 2007-05-21
hello.
ubuntu shows that the internet is working but nothing is moving....
i don't have a router (as far as i know)...
please help me..

---

### Post by Kobalt on 2007-05-21
Can you please post the output of the following command line : ```
ifconfig
```

---

### Post by NiviJah on 2007-05-21
actually i can't...cause ubuntu doesn't have an internet connection..
to copy the log here i will have to copy it to a page and than copy it to here....

any other idea?
if i will have to do this i will...

---

### Post by NiviJah on 2007-05-21
by the way i have an adsl

---

### Post by Korrontean on 2007-05-21
Using an USB memory card is a good idea ;) to get the output to your isolated ubuntu computer ;)

---

### Post by NiviJah on 2007-05-21
thanks for the offer :)

[PHP]ifconfig

eth0      Link encap:Ethernet  HWaddr 00:20:ED:36:84:20  

          inet addr:172.21.245.164  Bcast:255.255.255.255  Mask:255.255.240.0

          inet6 addr: fe80::220:edff:fe36:8420/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1509 errors:0 dropped:0 overruns:0 frame:0

          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:116436 (113.7 KiB)  TX bytes:4598 (4.4 KiB)

          Interrupt:20 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

[/PHP]

---

### Post by NiviJah on 2007-05-21
anyone...?:(

---

### Post by Docter on 2007-05-21
system>admin>network    DNS tab 

Do you have valid dns servers in there?

what is the output of

```
route
```

---

### Post by NiviJah on 2007-05-22
yes there are two servers there

192.168.101.###
192.168.101.###

and this is the output:
[PHP]route
Kernel IP routing table
Destination*     &#8236;Gateway*         &#8236;Genmask*         &#8236;Flags Metric Ref*    &#8236;Use Iface
172.21.240.0*    *               &#8236;255.255.240.0*   &#8236;U*     &#8236;0*      &#8236;0*        &#8236;0* &#8236;eth0
link-local*      *               &#8236;255.255.0.0*     &#8236;U*     &#8236;1000*   &#8236;0*        &#8236;0* &#8236;eth0
default*         &#8236;172.21.240.1*    &#8236;0.0.0.0*         &#8236;UG*    &#8236;0*      &#8236;0*        &#8236;0* &#8236;eth0
[/PHP]

---

### Post by Docter on 2007-05-22
OK here comes some guesswork.

Seeing as your IP address changed between the ifconfig and route commands I can assume that you have a dynamic IP address and that you are connecting to your ISP who is assigning it to you. It seems as if you are connected through some kind of router or perhaps sharing an internet connection with another computer as only eth0 device shows up. In this case I will go out on a limb and ask you to try changing your DNS servers to:

     ```
208.67.222.222
```
    and
     ```
208.67.220.220
```
to see  if that helps. These are the OPENDNS servers. 


If you do not connect over a network, via a router or if the DNS thing doesnt work then there is something wrong with your set up
EDIT: System -> Admin -> Network

Make sure it has a static IP, not DHCP... something like 192.168.0.1 (you may choose it)

. Tell us as much as you can (modem type, syslog from reboot etc)

---

### Post by NiviJah on 2007-05-22
ok well,
up until now it *was* DHCP and not static but, i've changet the DNS and Static ip
and now the browser is going strait to a "server not found" error page
before the changes it still seems as if he's doing something...(loading?) but never got anywhere..
how do i know what IP and DNS addresses are good?

---

### Post by NiviJah on 2007-05-22
my modem by the way is a USB

motorola surfboard sb4200 (cable modem)
tell me how to get the info you want and it's yours...

---

### Post by jacquesvn on 2007-05-22
You mention two machines. The machine that you are currently using to go online with - how does that connect?

If it connects to the same adsl line - give us the details of that: 
----
If its a Ubuntu or linux box:
 ifconfig
 route

if its a windows box:
 ipconfig
 route print

----

---

### Post by NiviJah on 2007-05-22
it is a dual boot winxp/ubuntu

i've post the two logs from the ubuntu boot here before.
i tried to type the them in window "run" but it only "pops" it for a second and then gone.
how to i copy it to post it here? (if needed...)

---

### Post by jacquesvn on 2007-05-22
> **NiviJah said:**
> it is a dual boot winxp/ubuntu

i've post the two logs from the ubuntu boot here before.
i tried to type the them in window "run" but it only "pops" it for a second and then gone.
how to i copy it to post it here? (if needed...)

In windows *click start* then *run* then type in cmd press enter

A dos window will appear - type in ipconfig copy and past the results after this
type in route print    then copy and paste the results here.

---

### Post by NiviJah on 2007-05-22
1.
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.21.17.54
        Subnet Mask . . . . . . . . . . . : 255.255.224.0
        Default Gateway . . . . . . . . . : 172.21.0.1

Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.16.42
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter Netvision Cable Connect:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 85.250.108.132
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 85.250.108.132

2.
C:\Documents and Settings\Gil>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 20 ed 36 84 20 ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - P
acket Scheduler Miniport
0x3 ...00 ff 34 24 00 60 ...... Parallels Host-Guest Virtual NIC - Packet Schedu
ler Miniport
0x20005 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0   85.250.108.132  85.250.108.132       1
          0.0.0.0          0.0.0.0       172.21.0.1    172.21.17.54       21
   85.250.108.128  255.255.255.128   85.250.108.132  85.250.108.132       1
   85.250.108.132  255.255.255.255        127.0.0.1       127.0.0.1       50
   85.255.255.255  255.255.255.255   85.250.108.132  85.250.108.132       50
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      169.254.0.0      255.255.0.0    169.254.16.42   169.254.16.42       20
    169.254.16.42  255.255.255.255        127.0.0.1       127.0.0.1       20
  169.254.255.255  255.255.255.255    169.254.16.42   169.254.16.42       20
       172.21.0.0    255.255.224.0     172.21.17.54    172.21.17.54       20
     172.21.17.54  255.255.255.255        127.0.0.1       127.0.0.1       20
   172.21.255.255  255.255.255.255     172.21.17.54    172.21.17.54       20
   212.143.206.14  255.255.255.255       172.21.0.1    172.21.17.54       20
        224.0.0.0        240.0.0.0    169.254.16.42   169.254.16.42       20
        224.0.0.0        240.0.0.0     172.21.17.54    172.21.17.54       20
        224.0.0.0        240.0.0.0   85.250.108.132  85.250.108.132       1
  255.255.255.255  255.255.255.255   85.250.108.132  85.250.108.132       1
  255.255.255.255  255.255.255.255    169.254.16.42   169.254.16.42       1
  255.255.255.255  255.255.255.255     172.21.17.54    172.21.17.54       1
Default Gateway:    85.250.108.132
===========================================================================
Persistent Routes:
  None

---

### Post by jacquesvn on 2007-05-22
Ok presumptions:

You need to set ubuntu back to DHCP just from looking at the similarities between your windows/linux config you are need to use dhcp as your ISP appears to provide you with the correct details.

Now I am not to familiar with USB DSL modem/routers as such. But I presume it does not create the connection with the ISP for you so presumbly you need some client to create the connection for you.

Try running "pppoeconf" from the terminal - you need to be root if I remember correctly, so sudo it. It is a friendly app if memory serves me correct, will ask you stuff and thats that. 

Let me know how you come along.

---

### Post by NiviJah on 2007-05-22
i already did this one "pppoeconf", searched the ubuntu help...
the output was that it can't find any connection...
any other idea.....?](*,)

---

### Post by jacquesvn on 2007-05-22
Does UBUNTU pick up your modem?

Do a lsusb? What do you see there? Copy and paste if you can ....

Be warned, I am not to familiar with USB modems but if you have the patience I will try and help u. Also just to double check that the network and that is working correctly after you changed back to dhcp just give me another dump of route and ifconfig.

---

### Post by jacquesvn on 2007-05-22
I have been doing some reading up and does not look like this is gonna be an easy task to set-up. Find stuff for other modems but nothing for Motorola.

Do you know what chipset your modem uses?

---

### Post by NiviJah on 2007-05-22
how do i do lsusb?
and how do i check my chipset?

---

### Post by jacquesvn on 2007-05-22
in ubuntu terminal 

lsusb <ENTER>

The chipset I am not sure, perhaps lsus may mention it else any documentation with it?

---

### Post by NiviJah on 2007-05-22
the isusb tells me that there is no such a command....

this is the ifconfig and route:


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:20:ED:36:84:20  

          inet addr:172.21.242.139  Bcast:255.255.255.255  Mask:255.255.240.0

          inet6 addr: fe80::220:edff:fe36:8420/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2039 errors:0 dropped:0 overruns:0 frame:0

          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:130652 (127.5 KiB)  TX bytes:4798 (4.6 KiB)

          Interrupt:20 Base address:0x6000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



route

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

172.21.240.0    *               255.255.240.0   U     0      0        0 eth0

link-local      *               255.255.0.0     U     1000   0        0 eth0

---

### Post by jacquesvn on 2007-05-22
> the isusb tells me that there is no such a command....

this is the ifconfig and route:

Sorry it is lsusb with a L ( but lower case ) and try sudo lsusb if normal lsusb does not want to work.

---

### Post by jacquesvn on 2007-05-22
Sorry a little confused, you have a network cable plugged into your machine, this is being assigned addresses from somewhere ... where?

What type of network do you have and is it not possible to route through one of the other machines? This may be easier than getting this USB modem working.

---

### Post by NiviJah on 2007-05-22
sorry i wrote "isusb" an no "Lsusb" , this is the output:

lsusb

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 007: ID 10d6:1101 Actions Semiconductor Co., Ltd 

Bus 001 Device 006: ID 03f0:4f11 Hewlett-Packard 

Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical

Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub

Bus 001 Device 005: ID 0c45:600d Microdia 

Bus 001 Device 001: ID 0000:0000

---

### Post by jacquesvn on 2007-05-22
> **NiviJah said:**
> sorry i wrote "isusb" an no "Lsusb" , this is the output:


Bus 001 Device 007: ID 10d6:1101 Actions Semiconductor Co., Ltd 
**Modem?**

Bus 001 Device 006: ID 03f0:4f11 Hewlett-Packard 
**Printer?**

Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
**Mouse**

Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
**Hub**

Bus 001 Device 005: ID 0c45:600d Microdia 
**Webcam?**


No real info there - the top one is probably your modem ... but I was hoping for a bit more information. There are a couple of apps that try and make the integration of a USB modem work easily but none that I find for 
motorola surfboard sb4200. They do however refer to specific chip sets so I was hoping for that info and that we could maybe approach it from that angle.

Sort of out of idea's sorry :( - read up above and see if I am correct regarding you connecting to an ethernet network, if so can you not route through there?

---

### Post by NiviJah on 2007-05-22
sorry i don't understand what do you want me to do....
you are correct about the printer..

the rest of it:

Bus 001 Device 007: ID 10d6:1101 Actions Semiconductor Co., Ltd
Modem?

Bus 001 Device 005: ID 0c45:600d Microdia
Webcam?

i don't know....i do have a webcam but microdia doesn't ring any bells....

---

### Post by Docter on 2007-05-22
Reboot your ubuntu, then immediately copy  the output of:
```

tail -n 50 /var/log/syslog
```

...and post it here.

---

### Post by NiviJah on 2007-05-23
here it is:

tail -n 50 /var/log/syslog

May 23 08:14:37 nivijah kernel: [   67.902559] input: Sleep Button (CM) as /class/input/input6

May 23 08:14:37 nivijah kernel: [   67.902964] ACPI: Sleep Button (CM) [SLPB]

May 23 08:14:37 nivijah kernel: [   68.061825] pcc_acpi: loading...

May 23 08:14:40 nivijah kernel: [   72.315265] eth0: no IPv6 routers present

May 23 08:14:41 nivijah dhcdbd: Started up.

May 23 08:14:41 nivijah NetworkManager: <information>^Istarting... 

May 23 08:14:41 nivijah avahi-daemon[4773]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).

May 23 08:14:41 nivijah avahi-daemon[4773]: Successfully dropped root privileges.

May 23 08:14:41 nivijah avahi-daemon[4773]: avahi-daemon 0.6.17 starting up.

May 23 08:14:41 nivijah avahi-daemon[4773]: Successfully called chroot().

May 23 08:14:41 nivijah avahi-daemon[4773]: Successfully dropped remaining capabilities.

May 23 08:14:41 nivijah avahi-daemon[4773]: No service found in /etc/avahi/services.

May 23 08:14:41 nivijah avahi-daemon[4773]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.21.247.183.

May 23 08:14:41 nivijah avahi-daemon[4773]: New relevant interface eth0.IPv4 for mDNS.

May 23 08:14:41 nivijah avahi-daemon[4773]: Network interface enumeration completed.

May 23 08:14:41 nivijah avahi-daemon[4773]: Registering new address record for fe80::220:edff:fe36:8420 on eth0.*.

May 23 08:14:41 nivijah avahi-daemon[4773]: Registering new address record for 172.21.247.183 on eth0.IPv4.

May 23 08:14:41 nivijah avahi-daemon[4773]: Registering HINFO record with values 'I686'/'LINUX'.

May 23 08:14:42 nivijah avahi-daemon[4773]: Server startup complete. Host name is nivijah.local. Local service cookie is 3032696904.

May 23 08:14:43 nivijah kernel: [   75.230034] ppdev: user-space parallel port driver

May 23 08:14:43 nivijah hpiod: 1.7.3 accepting connections at 2208... 

May 23 08:14:44 nivijah kernel: [   76.195283] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)

May 23 08:14:44 nivijah kernel: [   76.195291] apm: overridden by ACPI.

May 23 08:14:44 nivijah hcid[5010]: Bluetooth HCI daemon

May 23 08:14:44 nivijah kernel: [   76.459263] Bluetooth: Core ver 2.11

May 23 08:14:44 nivijah kernel: [   76.459365] NET: Registered protocol family 31

May 23 08:14:44 nivijah kernel: [   76.459369] Bluetooth: HCI device and connection manager initialized

May 23 08:14:44 nivijah kernel: [   76.459374] Bluetooth: HCI socket layer initialized

May 23 08:14:44 nivijah hcid[5010]: Starting SDP server

May 23 08:14:44 nivijah kernel: [   76.532997] Bluetooth: L2CAP ver 2.8

May 23 08:14:44 nivijah kernel: [   76.533005] Bluetooth: L2CAP socket layer initialized

May 23 08:14:44 nivijah NetworkManager: <debug info>^I[1179897284.604684] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 

May 23 08:14:44 nivijah kernel: [   76.828885] Bluetooth: RFCOMM socket layer initialized

May 23 08:14:44 nivijah kernel: [   76.828909] Bluetooth: RFCOMM TTY layer initialized

May 23 08:14:44 nivijah kernel: [   76.828913] Bluetooth: RFCOMM ver 1.8

May 23 08:14:45 nivijah anacron[5054]: Anacron 2.3 started on 2007-05-23

May 23 08:14:46 nivijah anacron[5054]: Will run job `cron.daily' in 5 min.

May 23 08:14:46 nivijah anacron[5054]: Jobs will be executed sequentially

May 23 08:14:46 nivijah /usr/sbin/cron[5081]: (CRON) INFO (pidfile fd = 3)

May 23 08:14:46 nivijah /usr/sbin/cron[5082]: (CRON) STARTUP (fork ok)

May 23 08:14:46 nivijah /usr/sbin/cron[5082]: (CRON) INFO (Running @reboot jobs)

May 23 08:14:53 nivijah gconfd (nivijah-5220): starting (version 2.18.0.1), pid 5220 user 'nivijah'

May 23 08:14:53 nivijah gconfd (nivijah-5220): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

May 23 08:14:53 nivijah gconfd (nivijah-5220): Resolved address "xml:readwrite:/home/nivijah/.gconf" to a writable configuration source at position 1

May 23 08:14:53 nivijah gconfd (nivijah-5220): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

May 23 08:14:53 nivijah gconfd (nivijah-5220): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

May 23 08:14:53 nivijah gconfd (nivijah-5220): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

May 23 08:14:59 nivijah gconfd (nivijah-5220): Resolved address "xml:readwrite:/home/nivijah/.gconf" to a writable configuration source at position 0

May 23 08:15:03 nivijah NetworkManager: <information>^IUpdating allowed wireless network lists. 

May 23 08:15:03 nivijah NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by Docter on 2007-05-23
As far as I can see you have no modem installed. USB ADSL modems generally use the pppd module which can be called at start up. The IP address that you see is your internal network address which has been assigned via DHCP (static would be better for you). Then username and password is loaded from a chap or pap file (depending on your ISP) which allows your broadband connection to function. All modems are different and some USBs can be a little tricky. I'll try and find a tute for you.

Ubuntu help document:
> 
1.3.2.&#8195;USB ADSL Modems

Often parts of ADSL USB modem drivers are proprietary, closed source software, with a restrictive licence, and so the whole driver cannot be supplied with Ubuntu. To get a modem to work with these drivers, you will need to download files from the Internet with a computer having a working connection, then transfer the downloaded files to you Ubuntu installation.

				

USB is far from the ideal medium for network access, if you have a modem that can connect both via USB and ethernet or a ethernet router, you should use the ethernet connection instead of the USB modem.

			

Since any USB modem installation will require Internet access to download the necessary proprietary drivers, as well as extensive configuration which is beyond the scope of this guide, all we can do here is to list the USB Modem models known to work with Ubuntu with links to the relevant installation instructions on the Ubuntu community help site.

The installation procedure of USB modems differs depending on the specific make and model of your modem. To identify model of your modem, Note the name and number on the front. Occasionaly you may have to look for a label to discover the exact model. Consult the list below to see which driver your modem requires and note the link.

When you go online to download the necessary drivers, you can access the relevant driver download links from the page with the installation instructions relevant to that model of USB modem.

Looking at your lsusb output I might suggest that it is one of these eagle modems but you may have to find out which... good luck, I'll help how I can.


[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)

[https://help.ubuntu.com/community/UsbAdslModem/EagleUsb](https://help.ubuntu.com/community/UsbAdslModem/EagleUsb)

---

### Post by NiviJah on 2007-05-23
thank you all very very much!!
i'll be gone for a few days,  so i will check if this solution works only then...
thank you all again so much for the help.

---

### Post by NiviJah on 2007-05-28
guys thank you very much for all the help! you were great!
but nothing seems to work for me, what i'm going to do if simply replace my usb modem with a Network Modem that suppose to work better not just in ubuntu but  also with everything else...
thank you again!
NiviJah

---

### Post by gefenm11 on 2007-12-17
Bus 001 Device 007: ID 10d6:1101 Actions Semiconductor Co., Ltd
i got an MP4 player that is recognized in this way

Bus 001 Device 006: ID 03f0:4f11 Hewlett-Packad
Definitely a printer

Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Mouse

Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
????

Bus 001 Device 005: ID 0c45:600d Microdia
Camera


try to find the device by disconnecting it, running lsusb and then connecting and running lsusb again, the difference is your modem.

---

