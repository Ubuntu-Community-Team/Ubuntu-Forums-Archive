---
title: "No wireless for bcom 4312. Moving on."
date: 2009-12-17
forum: New to Ubuntu
---

### Post by rs422 on 2009-12-17
Hi:

I am new to Ubuntu. Have installed 9.10 on a clean Dell E5500 with bcom 4312 wl adapter. Cannot get it to work. Well I mean it sees my airport express but cannot ping and not connecting to the net. Tried everything for 4 days now and no joy. Never could get it to work in Opensuse either. So I went and dug up a Linksys WPC54G PCMCIA card hoping this might help. I tried this card in Opensuse but couldn't get the power save to work and my battery lasted like 25 minutes (never could get suspend to disk to work anyway).

Since I am new to Linux and teaching myself, I don't understand alot of the syntax. Could someone provide me with a command line to instruct Ubuntu to download and install the Linksys firmware drivers? I know I sound like uber wussy but I know the power of sudo from screwing up my Powerbook G4 and; yes, I am afraid of the dark.

Thanks

Oh and Ubuntu works wonderfully in every other respect.

---

### Post by northern lights on 2009-12-17
Not so certain that your original wireless adapter can't be made functional.

Please post the output of```
sudo lshw -C network && ifconfig && iwconfig
```

Thank you.

Further, please elaborate which exact firmware you're in need of.

---

### Post by spcwingo on 2009-12-17
On the Broadcom card, did you try to install the package "b43-fwcutter" while connected to your router by ethernet cable?  If not, this may just be the ticket to getting it going.  To install just run this command from a terminal:

```
sudo apt-get install b43-fwcutter
```

Let me know either way how it turns out.

---

### Post by rs422 on 2009-12-17
Here is my output:

 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth2
       version: 01
       serial: 00:22:69:a4:58:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.12 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:21:9b:f3:e4:b3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5756m-v3.11 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68f0000-f68fffff
eth0      Link encap:Ethernet  HWaddr 00:21:9b:f3:e4:b3  
          inet6 addr: fe80::221:9bff:fef3:e4b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62249159 (62.2 MB)  TX bytes:1644764 (1.6 MB)
          Interrupt:16 

eth2      Link encap:Ethernet  HWaddr 00:22:69:a4:58:c2  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fea4:58c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1017 errors:0 dropped:0 overruns:0 frame:544
          TX packets:865 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:707825 (707.8 KB)  TX bytes:131933 (131.9 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
NOTE: i TRIED THE B43 INSTALL AND THE UNIT IS NOW OPERATIONAL FOR 3 MINUTES OR SO THEN DROPS THE CONNECTION. IT THEN TRIES TO RECONNECT AND SOMETIMES IT DOES BUT THEN DROPS IT AGAIN. i'M SITTING RIGHT NEXT TO THE TRANSMITTER.


Thanks again:P

---

### Post by spcwingo on 2009-12-17
The one laptop I installed Ubuntu on that had a Broadcom card had this same problem.  To correct this I just installed WICD (another network manager).  According to which release you're using it should be in the repositories.  To determine which release you're using run this command from a terminal:

```
lsb_release -a
```

If the output says 9.04 or above just run this command in a terminal to install WICD:

```
sudo apt-get install wicd
```

Let me know if that gets the job done.

---

### Post by rs422 on 2009-12-18
After 8 hours of fiddling and faddling I got the bcom 4312 in my Dell E5500 to reliably see my Airport. Running the Broadcom STA driver - the B43 does not work at all. Anyway, the Network Manager gives me full strength bars BUT I can't seem to stay connected. I tried Wicd and it said it couldn't resolve the IP address. Went back to Network Manager which didn't say anything about the IP but does the connect/disconnect thing. I can't surf past one page.

I shut down the Airport and activated the wireless transmitter in my DSL modem with WEP and the puter does the same thing so I'm pretty sure it isn't the Airport (got 3 Macs on it all the time) 

So, I'm really close but still no cigar. One good thing: I know Terminal a whole lot better than yesterday.

Thoughts?

---

### Post by spcwingo on 2009-12-18
Sorry, I'm all out of ideas.  Hopefully someone will pop in soon with a solution.

---

### Post by Cypher1101 on 2009-12-20
This is what I did to fix wifi on my 2004 laptop's ancient bcom card. It's also a 43xx card so this should work for 4312 as well.

First, open synaptic and make sure the package b43-fwcutter is installed. You may already have it because its the driver ubuntu recommends in the hardware drivers menu. edit: i saw that you have it.

Next, open a terminal and run this:
```
/usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```It's a script included by the above package edit: it should have been run when you installed it but running it again can't hurt

Next make a startup script to blacklist ssb and other problematic wifi modules
```
sudo gedit /etc/init.d/wirelessfix.sh
```and put the following in:```

#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe b44
```next set it up to run at startup:
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

sudo update-rc.d wirelessfix.sh defaults

```now reboot and you should be ready to go. I should point out that this process is a combination of two guides on the mintwifi wiki over at the linuxmint site.
Also you don't *have* to use wicd, it's just a little nicer. I only use it on machines that use wifi most of the time.

edit: I had similar results to yours without blacklisting (Connection drops and hangs etc)

---

