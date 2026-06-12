---
title: "ubuntu 6.10, Marvell Yukon network card, problem"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by redsax on 2006-11-09
Hi,

I am installing ubuntu 6.10 on a destop with this ethernet card.
When I tried to use pppoeconf to install dsl internet connection,
it complains that no working network card detected.

Using lspci gives: 03:08.0 Ethernet Controller: Marvell Technology
GroupLtd. Unknown devices4364

Does this mean that the ethernet is not identified by ubuntu?
Or it's identified, but I need a driver.

The driver turns out to be, very troublesome, sk98lin in ubuntu's history.
Is this driver problem fixed in current 6.10 version or not?
I mean if I should go get the sk98lin driver?

Thanks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by dbott67 on 2006-11-09
Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
```
ifconfig -a
```
```
lsmod
```
```
sudo lshw -C network
```

Thanks,
Dave

---

### Post by redsax on 2006-11-10
Gosh, I'm in trouble; I cannot connect internet via ubuntu,
so have to write down output by hands.

OK, first thanks for your help here first.

>>ifconfig -a

lo   Link encap:local loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     up LOOPBACK RUNNING MTU:16436 Metric:1
     RX Pachets:898 error:0
     TX .............(the same)
     Collissions:0
     Rx bytes:46676....

Sito Link encap:IPv6-in-IPv4
     NOARP MTU: 1480 Metric:1
     ...............

>>cat interfaces

auto lo
ifaces lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
.........................

auto teh2
iface ...................

auto ath0
iface ...................

auto wlan0
...........................

iface dsl-provider inet ppp
provider dsl-provider

>>sudo lshw -C network

*-netwrok unclaimed
   Description: Ethernet controller
   product: Marvell ...
   vendor: Marvell ...
   Physical id:0
   bus info:pci@03:00.0
   version:12
   width: 64 bits
   clock: 33 MHz
   capabilities:bus-master
   resources: iomemory:fdcfc000 ...(some nubmers and letters)

>>lsmod

lsmod gives a long list of mod, but no sk98lin.
after I run "sudo modprobe sk98lin", it shows in the list.

Thanks!

---

### Post by dbott67 on 2006-11-10
If you've got a USB thumb drive (or floppy) you can always 're-direct' output from commands to a text file.  For example, the commabd:
```
sudo lshw -C network > network_hardware.txt
```
would create a file in your home directory called 'network_hardware.txt'. You could then copy the file to USB or floppy, bring it over to another computer and post the results.

[end_tip_of_the_day]


After running modprobe, does the interface show up in 'ifconfig -a'?

If so, you may just need to enable the interface:
```
sudo ifup dsl-provider
```
(not sure if this is the proper interface name --- it would show up under ifconfig)
```
sudo dhclient dsl-provider
```
To obtain IP address from ISP. 

If it works, edit the /etc/network/interfaces file:
```
gksudo gedit /etc/network/interfaces
```
```
**[COLOR="Red"]auto dsl-provider[/COLOR]**
iface dsl-provider inet ppp
provider dsl-provider
```

-Dave

---

### Post by redsax on 2006-11-10
After reading all the threads related to this topic,
my guess is the following; please help point out if I am 
wrong.

1. lspci=> unknown devices for the Marvell ethernet controller,
suggesting ubuntu could not identify it.

2. pppoeconf => no working network card detected.

3. ifconfig -a => lo and sito, but no eth0/eth1/eth2.

4. sk98lin is the driver for this Marvell device, but not 
automatically loaded, so it's not a surprise that even I loaded
it by using modprobe, it still not working.

Conclusion: 1+2+3+4 => this Marvell Yukon not identified by
ubuntu.

Solution: download a new sk98lin driver from Marvell company
and compile it into kernel.

However, since I am totally new to ubuntu; just realized that
I have to download all the source files from some places.
My internet not working, so I cannot use apt-get?

---

