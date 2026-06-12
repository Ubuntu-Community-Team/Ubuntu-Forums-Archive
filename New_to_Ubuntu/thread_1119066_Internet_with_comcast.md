---
title: "Internet with comcast"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-04-07
I need help setting up the internet with ubuntu. My isp is comcast. I tried doing it with network manager but it doesn't work. Can someone please show me how to do it (I'm pretty sure i'm doing it wrong with network manager)? 

Linux is not in my destiny this is my 15th problem with it (most of the problems were with getting it installed. Don't ask.)

---

### Post by gtr32 on 2009-04-07
Please provide more information about your setup:

Are you connecting with Ubuntu straight into a cable modem?

If no, and there is a router in between, are there any other machines in the network that already are connected?

---

### Post by Poincare101 on 2009-04-07
No router, the modem only has one ethernet port so I only use one computer at a time. At other times, all my other computers connect via a router but its not connected right now because the computer with ubuntu(which doesn't have a wireless card) is connected to the modem.


Wow, that was a seriously fast reply!

---

### Post by Octagonal on 2009-04-07
My experience with comcast is that you'll need to release the dhcp address on your windows? box first.  Start -> Run -> cmd [enter] , ipconfig /release
Then unplug the ethernet from your windows box then plug into your ubuntu box.  This would be a lot easier with a router.

---

### Post by doas777 on 2009-04-07
after you have connected to the Modem, and rebooted, 
what is the output of:
```

sudo ifconfig 
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf
sudo route

```

---

### Post by Poincare101 on 2009-04-07
here's what I got for the first command: 
[sudo] password for dhaivatpandya: 

lo        Link encap:Local Loopback  
 
         inet addr:127.0.0.1  Mask:255.0.0.0
   
         inet6 addr: ::1/128 Scope:Host
          
	 UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
         RX packets:164 errors:0 dropped:0 overruns:0 frame:0
  
         TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
                    collisions:0 txqueuelen:0 
          
         RX bytes:9824 (9.8 KB)  TX bytes:9824 (9.8 KB)



         pan0      Link encap:Ethernet  HWaddr 46:17:b2:4c:ff:65  
                             inet6 addr: fe80::4417:b2ff:fe4c:ff65/64 Scope:Link
                          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
                           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                           TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
                       collisions:0 txqueuelen:0 
          
                   RX bytes:0 (0.0 B)  TX bytes:27534 (27.5 KB)


and for the second one i got:
# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).


# The loopback network interface

auto lo

iface lo inet loopback

and for the third one: 
cat: /etc/resolv.conf: No such file or directory
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

link-local      *               255.255.0.0     U     0      0        0 pan0

default         *               0.0.0.0         U     1000   0       
pan0



(on the last one, the spacing might be a little messed up)

---

### Post by Poincare101 on 2009-04-07
anyone willing to help? I really really really want ubuntu!

---

### Post by abn91c on 2009-04-07
> **Poincare101 said:**
> anyone willing to help? I really really really want ubuntu!
reboot everything, PC modem/router then in ubuntu open terminal and type```
sudo dhclient eth0
```

---

### Post by Poincare101 on 2009-04-07
dhaivatpandya@ubuntu:~$ sudo dhclient eth0



[sudo] password for dhaivatpandya: 



Internet Systems Consortium DHCP Client V3.1.1

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device

eth0: ERROR while getting interface flags: No such device

eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

dhaivatpandya@ubuntu:~$ 

Is what I get when I do that!

---

### Post by abn91c on 2009-04-07
post the output of  lshw -C network

---

### Post by Poincare101 on 2009-04-08
here's the output of that:
WARNING: you should run this program as super-user.

*-network DISABLED      
  
description: Ethernet interface

physical id: 1
       
logical name: pan0

serial: 42:d9:47:04:48:df
       
capabilities: ethernet physical
       
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

dhaivatpandya@ubuntu:~$ 

Please help me!

---

### Post by gtr32 on 2009-04-08
Short answer...you don't have network card installed/enabled. pan0 is Bluetooth adapter. What type of network card do you have, or if you don't know, what is your computer model?

---

### Post by Poincare101 on 2009-04-08
how would I find out my model number?

---

### Post by MrWES on 2009-04-08
You need to 'reset' the comcast modem when switching from one computer to the other. Unplugging the modem will not do it. There should be a small black button, and may be ressessed. Use a pen or point from a paper clip to reset it. Turn it back on, wait two mintues and then reconnect the computer you want it to work on. Should work fine. My son had to do this between his PS3 and computer -- he didn't have a router either.

Bill

---

### Post by gtr32 on 2009-04-08
> **Poincare101 said:**
> how would I find out my model number?

I think the easiest way would be to boot it into Windows and open network connections. Your adapter model should be right there, f.e.:

Local Area Network
Connected
Broadcom NetXtreme 57xx Gigabit Controller

---

### Post by Poincare101 on 2009-04-08
The thing is, ubuntu is taking up the whole drive. No more windows :(

---

### Post by gtr32 on 2009-04-08
> **Poincare101 said:**
> The thing is, ubuntu is taking up the whole drive. No more windows :(

Oh, I got confused with another thread. :)

What's the output of this:

sudo lshw -C bridge | grep -C 3 Ethernet

or this

sudo lshw | grep -C 3 Ethernet

---

### Post by Poincare101 on 2009-04-09
dhaivatpandya@ubuntu:~$ sudo lshw -C network

*-network DISABLED      

description: Ethernet interface
       
physical id: 1
       
logical name: pan0
       
serial: d6:ce:3b:45:bf:db
       
capabilities: ethernet physical
       
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

dhaivatpandya@ubuntu:~$ 


that's what I get. Please help! I want to get this working since the past two weeks!

---

### Post by gtr32 on 2009-04-09
> **Poincare101 said:**
> 
that's what I get. Please help! I want to get this working since the past two weeks!

You ethernet card is not either working or isn't recognized by Ubuntu installation. Is it a brand name computer (Dell, HP etc)? If so, what model? If not, open it up and look either what model motherboard you have (if it is integrated ethernet) or what model the ethernet card is.

---

### Post by Poincare101 on 2009-04-09
Its a dell computer. how would I find out the model number of my computer in ubuntu?

---

### Post by gtr32 on 2009-04-09
> **Poincare101 said:**
> Its a dell computer. how would I find out the model number of my computer in ubuntu?

It should be printed somewhere on the computer. Try looking at the rear panel (if it is a desktop) or bottom (laptop). Most likely next to a serial number.

---

### Post by Poincare101 on 2009-04-09
I said dell by mistake. Does anyone know where I would find it if it were a sony?

---

### Post by Poincare101 on 2009-04-09
ok so the product code is: 28550930

---

### Post by dmizer on 2009-04-09
Doesn't matter what the make or manufacture is, the model should be written on the machine somewhere.

Do you actually have an ethernet card installed? If so, are you sure it works?

---

### Post by Poincare101 on 2009-04-10
I've installed it. I don't whether it works or not though.

EDIT: corrected grammar

---

### Post by kpatz on 2009-04-10
> **Poincare101 said:**
> I've installed it. I don't whether it works not though.So you installed an actual ethernet *card* in your computer?  A PCI card that goes into one of the slots on the motherboard?  What make/model of card is it (do you have the box it came in)?

Or did you connect the modem to an ethernet jack that's built-in to the motherboard (on the back panel of the PC)?

---

### Post by Poincare101 on 2009-04-10
I haven't installed it myself (I got this computer free from a senior center, some computer scientist gave it to me). But there is a card with a jack in a *slot*.

---

