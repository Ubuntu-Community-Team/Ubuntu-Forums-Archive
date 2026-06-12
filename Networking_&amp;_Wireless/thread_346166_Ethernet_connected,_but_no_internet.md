---
title: "Ethernet connected, but no internet"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by bugs181 on 2007-01-25
The title pretty much explains it all. I am new to Ubuntu, in fact... I love it. Besides the complexity of it. I will probably stay with Ubuntu once I get the internet successfully working on it. I know nothing about Linux, or w/e platform this runs on. Is Ubuntu its own platform? Anyways, back on topic. I installed Ubuntu, and did some searching on the forums. I tried installing ndiswapper-1.8 & ndiswrapper-1.34 both with no success (too many errors). So, im back to square one. ANY help would be highly appreciated. I already know how to use the terminal. I do beleive im running Ubuntu 6.10 (EDGY EFT??). My ethernet card is located on Eth0.. According to the device manager. Thanks in advanced. -Kenny (AKA Bugz)

---

### Post by chili555 on 2007-01-25
Did you go to System->Administration->Networking and activate eth0? Highlight the eth0 entry and click Properties. Then check the Enable box. What happens?

It should fire right up.

Let us know.

---

### Post by Metaljaz on 2007-01-25
What kind of wireless problem are you having? Is the device detected but not working?
What card are you using and what is the chipset. You said that you installed ndiswrapper
so i guess we should assume that your card was not detected at install. 
Have you tried making sure your card is set to active?

---

### Post by bugs181 on 2007-01-25
To: Chili555,
Yes the connection IS enabled. I do beleive its detected because it has sent/received KB. I have added some DNS servers to the list, but when I try to use the internet (Mozilla Firefox) or the Add/Remove Applications that connects to the internet. On Firefox it replies "Server not found" and on the Add/Remove Apps it replies that it cannot resolve the DNS.

To: Metaljaz,
The eth0 IS a Wired connection.
Im not sure of the chipset, or cardname, or anything. And the ndiswrapper installs were UNSUCCESSFUL. And im not sure if the card is set to active or not..
Keep in mind im an Ubuntu noob and dont know my way around the OS very well.

Thanks for the fast replies.

---

### Post by Johan! on 2007-01-25
First of all:
Please tell us which computer hardware you are using. (Which network card?)
Tell us how you connect to the internet:
ADSL, cable, 56K6 modem?
Do you have a router?

Without this information, we cannot help you, I'm afraid.

---

### Post by bugs181 on 2007-01-25
To Johan,
Im not sure about the network card, how would I get the information?
I connect my pc to the internet through a router, hooked into a modem, that is hooked to a sattalite.. Not sure what this falls under.

---

### Post by Johan! on 2007-01-25
Open a terminal window, copy/paste the following text and press enter after each line:
```
dmesg |grep eth
```
```
dmesg |grep net
```
```
sudo ifconfig eth0
```

Post the results here.

---

### Post by bugs181 on 2007-01-25
To: Johan,

[PHP]kenny@kenny-laptop:~$ dmesg |grep eth
[17179576.640000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179576.900000] forcedeth: using HIGHDMA
[17179577.420000] eth0: forcedeth.c: subsystem: 0161f:205e bound to 0000:00:14.0
[17179602.744000] ADDRCONF(NETDEV_UP): eth2: link is not ready
[17179613.112000] eth0: no IPv6 routers present
[17181849.984000] ADDRCONF(NETDEV_UP): eth2: link is not ready


kenny@kenny-laptop:~$ dmesg |grep net
[17179571.764000] audit: initializing netlink socket (disabled)
[17179576.640000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179590.224000] islusb: suitable configuration found for net2280 + PCI device
[17181846.532000] islusb: suitable configuration found for net2280 + PCI device


kenny@kenny-laptop:~$ sudo ifconfig eth0
Password:
eth0      Link encap:Ethernet  HWaddr 00:03:25:3A:17:C3  
          inet6 addr: fe80::203:25ff:fe3a:17c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44279 (43.2 KiB)  TX bytes:42192 (41.2 KiB)
          Interrupt:209 Base address:0x2000 [/PHP]

And just to clear up some confusion.. Yes this is a laptop, and it IS hard-wired VIA ethernet cable to the router.
If there are any questions about any extra USB devices plugged into the USB drives. Then I have 1 USB mouse and 1 USB Thumb-Drive plugged into the slots. I do NOT have internet on the laptop, so im using a pc next to the laptop, and im sending the results to the forums, via the flash/thumb drive.

---

### Post by Johan! on 2007-01-25
Your computer doesn't get an IP number from your router.

Go to System>Administration>Networking.

Click on the wired connection, then on properties.

Make sure that "Enable this connection" is checked.
Configuration should be Automatic configuration (DHCP)
Close the window.

Does your network work now?

---

### Post by bugs181 on 2007-01-25
To Johan,
Everything you told me to do, was already properly configured. Any more ideas?

---

### Post by Johan! on 2007-01-25
post the output of:
```
cat /etc/network/interfaces
```
```
 sudo ifconfig -a -v
```

---

### Post by bugs181 on 2007-01-25
To Johan,

[PHP]kenny@kenny-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp
wireless-essid klrlinksys
wireless-key s:BD1090971D

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
kenny@kenny-laptop:~$ sudo ifconfig -a -v
Password:
eth0      Link encap:Ethernet  HWaddr 00:03:25:3A:17:C3  
          inet6 addr: fe80::203:25ff:fe3a:17c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52877 (51.6 KiB)  TX bytes:53478 (52.2 KiB)
          Interrupt:209 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:900 (900.0 b)  TX bytes:900 (900.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/PHP]

To Clear up some confusion about the wireless part.. This laptop does have a wireless card ALSO. But I figured if I got the Ethernet part of it working, I would be OK with that at least for now. Then I could get some utilities once the internet is on the laptop VIA ethernet. The wireless part does NOT work either.

---

### Post by Johan! on 2007-01-25
try
```
sudo ifup eth0
```

BTW: are you sure the network cable is plugged in, and the router is powered on? ;) 

you could also try to restart the networking after you changed some settings:
```
sudo /etc/init.d/networking restart
```

---

### Post by bugs181 on 2007-01-25
To Johan,

Yes the router IS on. And plugged in correctly, the LED light remains constantly lit. I did notice when I used the command "sudo /etc/init.d/networking restart" the router LED light was flashing as if it were receiving/sending data. Anyways, still no luck after doing the network restart. But here is the info it gave me:

[PHP]kenny@kenny-laptop:~$ sudo ifup eth0
ifup: interface eth0 already configured
kenny@kenny-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4780
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:25:3a:17:c3
Sending on   LPF/eth0/00:03:25:3a:17:c3
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth2 ; No such device.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:03:25:3a:17:c3
Sending on   LPF/eth0/00:03:25:3a:17:c3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/PHP]

Perhaps you have an IM client, since it seems your the person who is mostly helping me.

---

### Post by Johan! on 2007-01-25
You have a PC connected to the router, and it's working fine... so it's a problem in the Ubuntu settings.

The PC is running Windows?


Edit: I do have an IM, but I'm trying to help you here on the forums.
If we find a solution, other users may also find a solution to their problem. :)

---

### Post by bugs181 on 2007-01-25
To Johan,
Yes the PC is running Windows. The laptop is also running Windows in another partition of my hard-drive. When I switch the laptop over to Windows, the Ethernet works fine. Switch to Ubuntu and no luck..

Edit: Perhaps, we can talk via IM and I can post the results on the forums if we succeed?

---

### Post by Johan! on 2007-01-25
Try this on your Windows PC:

Right-click on "My Network Places", click on properties.
Right-click on "Local Area Connection", click on properties.

Click on Internet Protocol (TCP/IP)
Click on Properties.

Post the settings here.

---

### Post by bugs181 on 2007-01-25
To Johan,
IP Address: 192.168.1.100
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1

(I use OpenDNS.org, My ISP's DNS Servers were elcrapo)
Preferred DNS Server: 208.67.220.220
Alternative DNS Server: 208.67.222.222

---

### Post by bugs181 on 2007-01-25
Wait a second.. I fixed it.. 

IMPORTANT: On my router config, I had the maximum number of DHCP users set to 3, I raised this setting to 5 and it started working. Thankyou Johan, for ALLLLLLLL OF YOUR WONDERFUL HELP!!! I really appreciate the art of this forum's help. You have successfuly converted me to a full-time ubuntu user..

Edit: To figure out why Ubuntu did this, ill never know. But is it a possibility that Ubuntu requires more DHCP Connections than Windows?

---

### Post by Johan! on 2007-01-25
OK, now we should know the settings to put in the network-admin applet.

Go to System>Administration>Networking.

Click on Wired Connection, then properties.

Configuration: Static IP address
IP Address: 192.168.1.99
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.1

Click OK

Click on DNS
Enter your DNS addresses

Have fun on the Internet:D

---

### Post by bugs181 on 2007-01-25
Thankyou for all your help.. I really appreciate it.. I would still like your IM because I have many many questions about Ubuntu and you seem like a very nice person.. I only wish to make more friends anyways..

---

### Post by Johan! on 2007-01-25
Congratulations!:KS 

Windows didn't use DHCP, it was configured to use fixed settings, if I understand you correctly.
I tried to help you configure your Ubuntu computer with fixed settings too.
If DHCP works, it's also OK:D

---

