---
title: "Ralink wireless lan card v2 =C"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by joffal on 2007-07-06
Anyone know how i can get it to work? I'm new to all this and i really love Ubuntu (which im using) just cant get to the internet, i detect my wireless network and when i click on it...it doesnt...

---

### Post by kevdog on 2007-07-06
Ok, I need to know more about your card.  Please type at the command prompt the following commands and cut and paste the output

lspci -nn (if pci/pcmcia card, if USB, lsusb)
lshw -C network

---

### Post by joffal on 2007-07-06
Think i did something wrong :C 



jonny@ubuntu:~$ lspci -nn 
00:00.0 Host bridge [0600]: ATI Technologies Inc Unknown device [1002:5a31] (rev 01) 
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f] 
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80) 
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80) 
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80) 
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82) 
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (rev 80) 
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01) 
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80) 
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80) 
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62] 
09:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
09:04.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302] 
jonny@ubuntu:~$ LSHW -C network 
bash: LSHW: command not found 
jonny@ubuntu:~$

---

### Post by joffal on 2007-07-06
Oh! I'm using 'Wubi' by the way-apologies

---

### Post by kevdog on 2007-07-06
Ok I see your card uses the ra61 drivers.  Im no expert in this field since I dont own a ra card, however although these are supposed to be supported out of the box with linux, Ive found with Fiesty that often times the drivers need to be updated to the newest version in order to work.  SerialMonkey drivers are what you want.  Also operation of this card will not work well with network manager.  I dont know about other programs such as wicd, however most of the setup can be done manually with editing of the /etc/network/interfaces file once the new driver is installed.   I think another "network manager" utility known as rutil can be used if this is a notebook computer where roaming on different networks is a requirement.

Anyway I can help you for most of the way through the process.  Are you set up to compile from source files??  -- have you installed the build-essential package??  Do you have an internet connection now??

---

### Post by joffal on 2007-07-07
I can use a wired internet connection on it, dont think ive installed a 'build essential package' it did it all automatically the first time i selected Ubuntu for my OS (thats installing open office, gimp etc.) And, at risk of sounding a complete idiot-compile from source files? I should be able to work it out if you can describe it :P sorry

---

### Post by joffal on 2007-07-10
Bump?

---

### Post by imdano on 2007-07-10
Does your wireless network use encryption?  If you remove it are you able to connect?

---

### Post by kevdog on 2007-07-10
I want you to read through this thread first.  It specifically for the ra73 card (you have ra61 card), but the installation instructions are exactly the same for you --- except everywhere 73 is listed, you have to use 61.  Please read this post -- its excellent, it should be a sticky --- and then ask me anymore questions if you have any!

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by joffal on 2007-07-11
Cheers, I'll have a look and i dont have a key on my wireless-don't know how... =C

---

### Post by Austin_KW on 2007-07-11
Post the output of the following terminal commands

lsmod | grep rt
ifconfig -a

---

### Post by joffal on 2007-07-11
jonny@ubuntu:~$ lsmod | grep rt
parport_pc             36388  0 
parport                36936  3 ppdev,parport_pc,lp
rt61                  245128  1 
agpgart                35400  1 ati_agp


jonny@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:36:B8:2E:F9  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feb8:2ef9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8596476 (8.1 MiB)  TX bytes:383421 (374.4 KiB)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0D:F0:31:4F:91  
          inet6 addr: fe80::20d:f0ff:fe31:4f91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:1 dropped:1 overruns:0 carrier:0
          collisions:4 txqueuelen:1000 
          RX bytes:399381 (390.0 KiB)  TX bytes:1680 (1.6 KiB)
          Interrupt:18 

I'm getting...somewhere with this other thread though :P

---

### Post by Austin_KW on 2007-07-11
Yes, you already have the rt61 legacy driver installed. You probably just need to configure it. You can configure the ra0 interface by editing /etc/network/interfaces with "gksudo gedit /etc/network/interfaces"
add the lines (assuming you dont use encryption, just replace your network name)
```
auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid ***YourNetworkname***

```

Save the changes, then enter "sudo ifup --f ra0" in a terminal and hopefully you will get an ip address.

---

### Post by joffal on 2007-07-11
I'm just getting 

jonny@ubuntu:~$ sudo ifup --f ra0
mode: Unknown host
ifconfig: `--help' gives usage information.
Failed to bring up ra0.
jonny@ubuntu:~$ --help
 

in reply

---

### Post by joffal on 2007-07-11
Typed it wrong i think, i tried again and copied and pasted and got:

jonny@ubuntu:~$ gksudo gedit /etc/network/interfaces
(gedit:8836): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
jonny@ubuntu:~$ sudo ifup --f ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 8966
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:0d:f0:31:4f:91
Sending on   LPF/ra0/00:0d:f0:31:4f:91
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPOFFER from 192.168.2.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.5 -- renewal in 946080001 seconds.
jonny@ubuntu:~$ 


I think it did work for a second, i got onto google images which i hadnt previously been on

SO CLOSE

---

### Post by Austin_KW on 2007-07-11
You have a typo, you put ifconfig for the **iwconfig** r0 mode ...

---

### Post by joffal on 2007-07-11
Is it resolved though with the above?

---

### Post by Austin_KW on 2007-07-11
Cross post on the last ;)

It did work, you got an ip address from your router. ```
DHCPACK from 192.168.2.1
bound to 192.168.2.5 -- renewal in 946080001 seconds.
```


Try bringing your ethernet interface down with "sudo ifdown --f eth0"
and then bring up the wireless with "sudo ifup --f ra0"

then check for connectivity to your router by pinging with "ping -c 3 192.168.2.1"

---

### Post by joffal on 2007-07-11
When it asks me for my password the keyboard wont respond :/

---

### Post by joffal on 2007-07-11
jonny@ubuntu:~$ sudo ifdown --f eth0
Password:
Sorry, try again.
Password:
jonny@ubuntu:~$ sudo ifup --f ra0
There is already a pid file /var/run/dhclient.ra0.pid with pid 10065
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:0d:f0:31:4f:91
Sending on   LPF/ra0/00:0d:f0:31:4f:91
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.2.5
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.241/1.241/1.241/0.000 ms
bound: renewal in 946078310 seconds.
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
jonny@ubuntu:~$ 


Goddamnit charles :P Why wont it work :C

---

### Post by Austin_KW on 2007-07-11
Did you manage to edit /etc/network/interfaces and add the lines, or did the GnomeUI-WARNING stop you. 


Your ping is working? you can get to the router. But I am not sure why the dhcp did not work, if it did not work you may not be able to get to the internet as you will not have a default route on dns.

---

### Post by joffal on 2007-07-11
I did insert the lines, then on the first go i got to go on google images, so i can access the internet...i just cant :P:(

---

