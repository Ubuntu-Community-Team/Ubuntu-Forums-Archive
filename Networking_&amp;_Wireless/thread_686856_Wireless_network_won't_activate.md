---
title: "Wireless network won't activate"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by Im_Original on 2008-02-03
Hello everyone,

I'm using Gutsy on a Packard Bell Easynote R1934W. It has a rt61 wireless card. I'm having some trouble connecting to a home wireless network. The wired network works fine. I tried a bunch of howtos on the forums, no dice. I don't know how to activate the interface. 
Here is the output of  lshw -C network 

 *-network:0 DISABLED    
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wmaster0
       version: 00
       serial: 00:10:60:66:e9:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:95:07:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.102 latency=128 maxlatency=8 mingnt=3 module=via_rhine multicast=yes



So, if I'm reading this correctly, it sees the wireless card, the driver for the card, rt61pci, is installed, the name is wmaster0, and it's disabled. 

So, I tried enabling it with ifconfig

 sudo ifconfig wmaster0 up
 SIOCSIFFLAGS: Operation not supported


What the heck does that mean? I tried a bunch of howtos, as I said, but they all failed for one reason or another. The main problem mustbe that the interface is not enabled, but I've run into this problem. Enabling the interface with the GUI does not affect the above output. 

Does anyone know how to solve this? Thanks in advance.

---

### Post by psyburn on 2008-02-03
Just to make sure please post the output of
```
ifconfig -a
```

---

### Post by neonum6 on 2008-02-03
> sudo ifconfig wmaster0 up
SIOCSIFFLAGS: Operation not supported

it seems a driver problem!

---

### Post by psyburn on 2008-02-03
@neonum

I want to see if it uses a different name and that's what I asked above for

my rt61 would come up as **ra0** or **wlan0** with **wmaster0** as something the driver used but doing any configuration to it would get nowhere until you configured **[the name other than wmaster0]** and** [the name other than wmaster0]** would be the adapter you brought up.

---

### Post by neonum6 on 2008-02-03
> **psyburn said:**
> @neonum

I want to see if it uses a different name and that's what I asked above for

my rt61 would come up as **ra0** or **wlan0** with **wmaster0** as something the driver used but doing any configuration to it would get nowhere until you configured **[the name other than wmaster0]** and** [the name other than wmaster0]** would be the adapter you brought up.

than we need of a ```
ifconfig -a
```

---

### Post by Im_Original on 2008-02-03
Hello again, thanks for teh quick replies. Here's the output of ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:40:D0:95:07:F9  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe95:7f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9324647 (8.8 MB)  TX bytes:398485 (389.1 KB)
          Interrupt:11 Base address:0xe200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:66:E9:38  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-10-60-66-E9-38-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



I have only a partial understanding of what this means.

---

### Post by psyburn on 2008-02-03
Instead of using **wmaster0** use **wlan0** as the name to configure the device

Offhand: Have you tried getting it to work with network-manager yet? And have you had any success?

On topic; Read this: [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")
But subtistute **wlan0** for the **<interface>**

---

### Post by Olog-hai on 2008-02-03
me too i have the same problem

olog-hai@olog-hai-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:B6:9B:AD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:CF:61:89:9B  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)





and 



 *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: BCM4312 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:16:cf:61:89:9b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:b6:9b:ad
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.77 firmw




my wireless wont work

---

### Post by psyburn on 2008-02-03
@Olog-hai: your problem is different as your using a Broadcom chip and he's using a rt61
I can't give usable info to people on equipment about I don't know.

This thread is relevant to your interests:
[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

---

### Post by Im_Original on 2008-02-03
psyburn, thanks for the reply. 

I did try using the GUI, didn'twork. It didn't connect, I couldn't make it seeany networks, and it had no effect on the command line output above. 

When I try wlan0

sudo ifconfig wlan0 up
SIOCSIFFLAGS: No buffer space available


Which is similar to the output for wmaster0. Another driver problem? "No buffer space available" sounds like a solvable problem.

---

### Post by Im_Original on 2008-02-03
Olog-hai, I wish I could help but I'm just as lost as you.  :lolflag:

---

### Post by Im_Original on 2008-02-03
Sorry for everyone posting, but I'm off, I 'll check in tommorrow. 

Cheers.

---

### Post by psyburn on 2008-02-03
You really should try this page first if anything 'cause this one is getting weird:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61")
Following that solved my problems with the given rt61 drivers...

please copy and paste the output of:
```
cat /etc/network/interfaces
```
For network-manager to work with the wlan0 adapter there should be nothing more than "auto wlan0" in the above file. 
However I wonder how much you have done to your Ubuntu install to get it to work.

---

### Post by Im_Original on 2008-02-05
psyburn, sorry for the late reply. Here's the output of cat/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#iface eth0 inet dhcp




As for how much I did to my system, I don't think I did much. I tried installing new drivers, but that failed since drivers were already installed and shouldn't have changed anything. I tried some other things, but saved original copies of any files I modified (a while ago, I learned the hard way that that's a good idea) and restored the originals after whatever I was trying didn't work. Maybe I messed something up, but I don't think so. 

Thanks for the link, I'll try it.

---

### Post by Im_Original on 2008-02-05
Ok, so I went to [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61), and there are 2 problems. 

The site says to run

sudo apt-get install linux-headers build-essential gcc

I know what this does, it installs three packages. This command returns

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.22-14-xen 2.6.22-14.51
  linux-headers-2.6.22-14-virtual 2.6.22-14.51
  linux-headers-2.6.22-14-ume 2.6.22-14.51
  linux-headers-2.6.22-14-server 2.6.22-14.51
  linux-headers-2.6.22-14-rt 2.6.22-14.51
  linux-headers-2.6.22-14-generic 2.6.22-14.51
  linux-headers-2.6.22-14-386 2.6.22-14.51
  linux-headers-2.6.22-14 2.6.22-14.51
You should explicitly select one to install.
E: Package linux-headers has no installation candidate




I know that if I install the wrong headers, it could mess up my computer, so I want to make sure. I should be installing   linux-headers-2.6.22-14-386 2.6.22-14.51, on my computer, which has an intel celeron M, which is i386. Right? Also, shouldn't the right headers be automatically downloaded by the update manager on ubuntu?

The next problem is that the driver download link on the ralink website is broken, the download does not start. I don't want to download whatever I find on a google search, so can anyone suggest an alternate site where I can download drivers?   

Thanks in advance.

---

### Post by satkus on 2008-02-06
I am successfully using my rt61 chip linksys card for the first time. This was a real headache and i have been struggling with it for at least a week. All of my problems were driver related. I finally got it working by downloading the rt61-CVS drivers from here:
[URL="http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads"]
[COLOR="Blue"]http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads[/COLOR][/URL]

and following these instructions...
[URL="http://rt2400.cvs.sourceforge.net/rt2400/source/rt61/Module/README?view=markup"]
[COLOR="Blue"]http://rt2400.cvs.sourceforge.net/rt2400/source/rt61/Module/README?view=markup[/COLOR][/URL]

...instead of the still out of date instructions that come in the drivers read-me file.

also, I used the GUI app RutilT _AFTER_ configuring the rest of the settings using iwconfig, to change to DHCP and finalize the connection

I hope this helps.

---

### Post by Im_Original on 2008-02-10
Ok, I downladed drivers from serialmonkey, and followed the instructions at [http://rt2400.cvs.sourceforge.net/rt2400/source/rt61/Module/README?view=markup](http://rt2400.cvs.sourceforge.net/rt2400/source/rt61/Module/README?view=markup). When I try to make, I get this:

$make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `Stuff/rt61-cvs-2008021009/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt61.ko failed to build!
make: *** [module] Error 1



"No rule to make target" does this mean the makefile is improperly written, or that my computer is set up in a way that the make file did not predict? Do I need to uninstall the old drivers before continuing? If so, how?

I'll look around on google and serial monkey for any ideas, any help would be appreciated.

---

