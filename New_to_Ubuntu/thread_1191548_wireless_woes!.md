---
title: "wireless woes!"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by UN1corn on 2009-06-19
hi all,
i need help to set up a wireless repeater. my ubuntu laptop wont see it, but another windows laptop does.

the assorted hardware is this

my ubuntu laptop is a fujitsu seimens amilo li 1705
my wireless repeater is a netgear WNHDE111 5ghz wireless-N HD access point/bridge


ive used ubuntu for 2 years now, but im not too good with any complicated stuff.
i can copy and paste in terminal and mostly download and install correct packages.

i guess the problem is to do with the ''n'' standard.my laptop picks up my oldernetgear router fine. 

ive been reading around this for a couple of weeks but i not competent enough to really understand what needs to be done.

i would really appreciate any helpful suggestions. The absolute last thing i want to do is to install windows on this laptop.

thanks again

---

### Post by Michael.Godawski on 2009-06-19
hi,

some input would be nice:

```
sudo lshw -C network
ifconfig
iwconfig
```

I mean, output from the terminal of course. I start writing in shortcuts. ;)

---

### Post by UN1corn on 2009-06-20
hi thanks for quick reply

i typed what you said into terminal and this is the result

  	 	 	 	 	[FONT=monospace]*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:14:0b:0a:95:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.3 latency=24 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:17:b4:5e:dc:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
steve@steve-laptop:~$ sudo apt-get clean
steve@steve-laptop:~$ 
steve@steve-laptop:~$ 
steve@steve-laptop:~$ 

steve@steve-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:0b:0a:95:d0  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bff:fe0a:95d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1894693 (1.8 MB)  TX bytes:292667 (292.6 KB)
          Interrupt:23 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

steve@steve-laptop:~$ 
steve@steve-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

steve@steve-laptop:~$ 



hope this may help

looking forward to any help you good people can give me!

[/FONT]

---

### Post by UN1corn on 2009-06-22
bump

---

### Post by caravel on 2009-06-22
> **UN1corn said:**
> 
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10





steve@steve-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

steve@steve-laptop:~$

Looks like there's no kernel module installed for the device.  I think it requires a restricted driver.  Have you enabled all of the repos in software sources?  Have a look in "hardware drivers" to see if the device is listed and if so enable it.

---

### Post by UN1corn on 2009-06-22
hi
thanks for quick reply. since first post i reinstalled 9.04 and th erestrited drivers are being used but laptop will still not see the wireless adapter. It does see my main netgear router. 
 
Do i need a newer wireless card for laptop?
 
yours in need of help!

---

### Post by caravel on 2009-06-22
> **UN1corn said:**
> hi
thanks for quick reply. since first post i reinstalled 9.04 and th erestrited drivers are being used but laptop will still not see the wireless adapter. It does see my main netgear router. 
 
Do i need a newer wireless card for laptop?
 
yours in need of help!

If it sees your router, then surely the wireless adaptor must have the kernel module installed? Unless you've plugged in an ethernet cable between the laptop and router?  Did you reinstall since last posting up that info?  If so post it up again.

---

