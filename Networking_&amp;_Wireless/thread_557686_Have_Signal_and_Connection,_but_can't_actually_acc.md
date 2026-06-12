---
title: "Have Signal and Connection, but can't actually access the internet!"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by AlchemyMan on 2007-09-23
Well, 

I've been using feisty for a few months on my laptop and have been connecting just fine using a USB network card. I just recent gotten ahold of a desktop, however, and thought that it would be neat to set it up in my studio. I set it up and installed Feisty. Then plugged in the network card, the same one which has worked before. Now it gets a signal (never more than 63% and never less than 30% unless I mess with the settings and cause it to die again). 

It seems to recognize the network (its a public, unsecured wireless network), but for the life of me I can't actually get onto the internet, or use synaptic, or anything. The network monitor tells me I am connected on eth1, and it's sending and receiving back and forth! But the whole machine acts as though there is no connection. 

Anyone know what might be up? If you can help me in layman's terms, I would be even more grateful, but I will appreciate any and all help!

Thanks in advance!

---

### Post by kevdog on 2007-09-23
Can you describe your problem more, it sounds like either a gateway or dns problem.

Can you post the following:

route -n
cat /etc/resolv.conf
dig -x 72.14.207.99
ifconfig
lshw -C network
iwlist scan

Lotta stuff but it will help

---

### Post by AlchemyMan on 2007-09-23
Hey, here's the stuff:

```

aleksandr@stud-monkey:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 eth1

******

aleksandr@stud-monkey:~$ cat /etc/resolv.conf
nameserver 10.0.1.1

******

aleksandr@stud-monkey:~$ dig -x 72.14.20.99

; <<>> DiG 9.3.4 <<>> -x 72.14.20.99
;; global options:  printcmd
;; connection timed out; no servers could be reached

******

aleksandr@stud-monkey:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:A3:03:27:DF  
          inet addr:10.0.1.3  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe03:27df/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:655 errors:0 dropped:82 overruns:0 frame:0
          TX packets:844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73440 (71.7 KiB)  TX bytes:59096 (57.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1646 (1.6 KiB)  TX bytes:1646 (1.6 KiB)

******

aleksandr@stud-monkey:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:13:d4:43:9a:e2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.59 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: iomemory:e2001000-e2001fff ioport:d000-d007 irq:16
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:a3:03:27:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.1.3 multicast=yes wireless=IEEE 802.11b/g

********

aleksandr@stud-monkey:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0D:93:7D:49:A7
                    ESSID:"MICA - Wireless - Bank"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=5/100  
                    Extra: Last beacon: 528ms ago

```

I am not too sure what much of it means, of course, as I am still a relatively new Linux user, but hopefully you can make a bit of sense out of it? Thanks very much for replying, by the way.  Sadly, those are probably all the results I can post up at the moment, since I am far from any inhabited territory and that was my only CD. I hope it helps.

---

### Post by kevdog on 2007-09-23
Cant say that anything looks out of the ordinary on what you posted!!

Couple of more things

Can you ping the router, I think it would be the following
ping 10.0.1.1

Do you have access to the router -- is any MAC filtering taking place??

Did you have to install a driver to get your USB wireless dongle to work??
I dont know what to make of this:
Quality=100/100  Signal level=5/100

---

### Post by AlchemyMan on 2007-09-23
Hey.

I pinged the address and it says the Host is unreachable. I don't actually have physical access to the router (well, I may, but I don't really know where it is in the building :) ). What's MAC filtering, by the way?

---

### Post by AlchemyMan on 2007-09-23
Hmm...I read up on MAC filtering, and I doubt that's what they have here. People use wireless here all the time, and we were never told on any restrictions based on device. However, I could be wrong. I am just guessing, but it would seem to make sense.

---

### Post by kevdog on 2007-09-23
Just an idea, b/c this problem is strange, can you connect to any other public wireless network??  I dont know if you have access to another network, but this would tell us a lot -- ie if your drivers, network cards etc are setup appropriately.  You dont happen to be running a firewall on the new computer???  If you are, turn it off.

---

### Post by AlchemyMan on 2007-09-23
Hmm, well, generally I have no access to other networks. There was one last night that faded in and out (it was called apple network or some such thing), and I was connected to it briefly (it was also unsecured, or so it said), but ran into the same problem.

My wireless card usb thingy worked out of the box for my laptop and I bought it specifically because it was on the list of those that "just work" with ubuntu. I never had to install drivers for it or anything. 

As for firewall, I don't think one should be running. This is a fresh installation of Feisty, and I haven't really done anything much to it yet other than tinkering with the network settings trying to get the internet to work.

I hope that info helps a bit. Thank you so much for helping so far!

---

### Post by AlchemyMan on 2007-09-23
A strange development in the case! It's all working now! However, I am still baffled as to the cause, and am therefore reduced to burning votive offerings before the altar of the computer gods...

All I did was move the card to a different USB port (to make room for a thumb drive), and reboot. After reboot, I suddenly had internet? It couldn't have bee the port, could it have?

Its also possible that this was a building wide issue and I was harping about nothing, but I was relatively certain that some people had been able to use wireless just fine last night. Ah well, I am going to hope it stays steady enough for my purposes, I have had enough computer use in my day to know that its probably a bit too early to celebrate...I'll let you know if it dies again under suspicious circumstances, and if you have any clues or theories, I would be very grateful to hear them.

Once again, thanks very much.

---

