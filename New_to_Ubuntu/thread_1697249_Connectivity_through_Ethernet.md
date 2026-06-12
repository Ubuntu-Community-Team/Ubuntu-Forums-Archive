---
title: "Connectivity through Ethernet?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by davidw101 on 2011-02-28
Hi, everyone. I'm running Ubuntu 10.10 desktop edition on a quite old HP Pavilion. It runs amazingly, by the way. On, my main concern is that since I have no built-in WiFi card, I've plugged an Ethernet cable from the back of my computer into the back of my wireless router. The problem I'm having is that I'm getting no Ethernet or WiFi connectivity. 
Here's my output on ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:e0:18:6b:78:13  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xb000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34560 (34.5 KB)  TX bytes:34560 (34.5 KB)
```
I don't understand how to get it to work, and I've noticed that the main use of Ubuntu revolves around connectivity and commerce, and I really don't know what to do. Could someone please help?

---

### Post by cavh on 2011-02-28
To check before getting too involved:

1. The Ethernet cable is good, i.e. no breaks in it
2. There are flashing lights coming from the NIC (network interface card)
3. Can any other computer get an IP address using this cable?
4. Is your router set up for DHCP?

---

### Post by sandyd on 2011-02-28
> **davidw101 said:**
> Hi, everyone. I'm running Ubuntu 10.10 desktop edition on a quite old HP Pavilion. It runs amazingly, by the way. On, my main concern is that since I have no built-in WiFi card, I've plugged an Ethernet cable from the back of my computer into the back of my wireless router. The problem I'm having is that I'm getting no Ethernet or WiFi connectivity. 
Here's my output on ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:e0:18:6b:78:13  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xb000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34560 (34.5 KB)  TX bytes:34560 (34.5 KB)
```I don't understand how to get it to work, and I've noticed that the main use of Ubuntu revolves around connectivity and commerce, and I really don't know what to do. Could someone please help?
you don't have an IP address.
Check cat cable, dhcp of router.

---

### Post by davidw101 on 2011-02-28
> **cavh said:**
> To check before getting too involved:
 
1. The Ethernet cable is good, i.e. no breaks in it
2. There are flashing lights coming from the NIC (network interface card)
3. Can any other computer get an IP address using this cable?
4. Is your router set up for DHCP?
 
1. Cable's in perfect condition,  it was used with this PC before when it was previously on XP, so yes, it **did **work before, on a previous OS.
2. Doesn't appear to be so, although I'll have to check in a couple min.
3. I'm planning to try 192.168.1.1 to enter on DHCP, hopefully it works.
4. I'd believe so.

---

### Post by cavh on 2011-02-28
1. Have there been any changes to the router config since you had it running okay against your XP install? If the answer is no, time to move to question 2 below ...

2. Have you run the package update tool since you installed Ubuntu? I guess the answer to this question is no, given the lack of internet connectivity - if so, move to question 3 below ...

3. Click System, Administration, Hardware Drivers and post back with whatever comes up once the scan has completed.

---

### Post by TechWiz2100 on 2011-02-28
Try adding auto eth0 to your /etc/network/interfaces file

---

### Post by davidw101 on 2011-02-28
cavh, didn't see that option under System-> Admin, but there is Additional Drivers. Yielded results:
When it starts it says "Downloading package indexes failed, please check your network status... Etc.".

TechWiz, it won't allow me to change anything in those folders.

---

### Post by TechWiz2100 on 2011-02-28
Its owned by root you need to do:
```
gksudo gedit /etc/networking/interfaces 
```

---

### Post by davidw101 on 2011-02-28
Alrite, did it. I added both Auto eth0 and just eth0, just to be safe. Only thing is that both thief information is the same.

---

### Post by Iowan on 2011-02-28
From a terminal (Applications>Accessories>Terminal) check:```
sudo lshw -C network
``` Post results - if possible...

Also - you're not using the uplink port on the router, I hope...

---

### Post by davidw101 on 2011-02-28
sudo lshw -C network Output:
 
```
 
  *-network DISABLED      
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 90
       serial: 00:e0:18:6b:78:13
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:b000(size=256) memory:e5800000-e5800fff memory:40000000-4001ffff

```
And yes, apparently I am using the uplink ports... That's a bad thing?

---

### Post by Chronon on 2011-02-28
Uplink should connect to the network (not your PC).

---

### Post by davidw101 on 2011-02-28
> **Chronon said:**
> Uplink should connect to the network (not your PC).
 I don't exactly understand what you mean... So the cable (connected to the router) is supposed to connect to an ethernet wall port?

---

### Post by davidw101 on 2011-02-28
I must be some kinda idiot... I've never actually set up a router or ethernet myself on any computer, so I have no idea how to do it.

---

### Post by Chronon on 2011-02-28
[IMG]http://www.home-network-help.com/images/connect-wireless-router.jpg[/IMG]

My setup looks like this.

---

### Post by davidw101 on 2011-03-01
Odd, mine's set up the exact same way, yet yeilding absoluetly no results. Also, i just reinstalled Ubuntu 10.10 with the ethernet cord plugged in as main startup/only OS, yet still not working...
[EDIT] Actually, mines setup is slightliy different. I don't have a modem, my route attaches directly to a phone splitter into the phone line.

---

### Post by The Cog on 2011-03-01
Two things I notice here:
> eth0      Link encap:Ethernet  HWaddr 00:e0:18:6b:78:13  
          UP BROADCAST [COLOR="Red"]**RUNNING**[/COLOR] MULTICAST  MTU:1500  Metric:1
          **[COLOR="Red"]RX packets:0[/COLOR]** errors:0 dropped:0 overruns:0 frame:0
          **[COLOR="Red"]TX packets:0[/COLOR]** errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xb000 
RUNNING means that the cable is connected and link signal has been detected.

But 0 packets sent or receieved is a little odd. I wonder if there is a driver problem here. I can't think why else you wouldn't see packets in either direction. Do you have a different make of ethernet card you could plug in and try?

---

### Post by davidw101 on 2011-03-01
Sad to say I only have one, which is built into the CPU. But I wasn't able to get any drivers, could that have something to do with it?

---

### Post by TechWiz2100 on 2011-03-01
[http://www.brownhat.org/sis900.html](http://www.brownhat.org/sis900.html)

Try those drivers. From other posts I've helped in about SiS chipsets, I've noticed a huge lack of support and that their chips are sometimes rebranded chipsets from other companies like Realtek. Good luck!

---

### Post by davidw101 on 2011-03-01
> **TechWiz2100 said:**
> [http://www.brownhat.org/sis900.html](http://www.brownhat.org/sis900.html)
Out of curiosity, where would i want to save these?

---

### Post by davidw101 on 2011-03-02
I thought I was supposed gksudo into usr/src/Linux-headers-2.6.35-22-generic/drivers/net/fs_enet and put them there... Please correct me if I'm wrong.

---

