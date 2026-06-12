---
title: "network issues"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Skynet_Beta on 2009-08-27
I am having issues with my network at the moment using the Network Manager that came with this version of unbuntu. The problem is that the Network Manager (or possible I) has deleted the settings that it had created automatically, and won't connect to the internet. It says "Wired Network" and "device not managed". 

before this happened it was a case of going through anywhere between one and five restarts to get it to connect every morning. may have been something I've done, but I am not sure. Either way, I am sure its not the connection itself as I am able to access the internet using an XP virtual machine. 

The details you're surely going to ask for based on my viewings of other forums:

currently using Ubuntu 9.04 Jaunty Jackalope

the lshw -C netowrk command comes up with:

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:19:66:81:62:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.4 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:4c:c6:1b:39:1f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


and /etc/NetworkManager/nm-system-settings.conf file reads:
[main]

plugins=ifupdown,keyfile



[ifupdown]

managed=false


I don't know if any of this is right or wrong, but after i managed to resolve a printer issue I was having I thought I'd try to resolve this network issue and evidently failed misserably

---

### Post by nandemonai on 2009-08-27
Have you got anything in your /etc/network/interfaces file?

---

### Post by sandyd on 2009-08-27
> **nandemonai said:**
> Have you got anything in your /etc/network/interfaces file?
open up a terminal (Applications -> Accessories -> Terminal)
and typt this in. then post the output
```

cat /etc/network/interfaces 

```

---

### Post by nandemonai on 2009-08-27
Thanks Carlee, I was a lil quick with that one. I'm technically supposed to be working >.>

Just for clarification, if you have network settings configured through the /etc/network/interfaces file then that will overide and technically disable network manager ;)

---

### Post by Skynet_Beta on 2009-08-28
Thanks for this...

My network interfaces file contains:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
            address 192.168.2.4
            netmask 255.255.255.0
            gateway 192.168.2.1

---

### Post by Skynet_Beta on 2009-08-28
Cheers guy's, I read in another more recent thread that deleting the auto eth0 details in the interfaces file but keeping the lo settings should fix it, so I did that, then restarted my computer hoping for the best and it works!

I'm impressed by these forums though... If this were a windows forum I would be called an idiot in 20 languages and in 10 different ways, all of which would contain swear words before being given advice which would probably be wrong.... like a problem we had at work where the explorer.exe wasn't displaying so someones first step in their "fix" was to click on the start menu... tangent aside, I'm impressed... thanks :)

---

