---
title: "ubuntu doesn't connect to my Linksys wireless adapter"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by z400100500 on 2009-09-22
Hello again. I have successfully reinstalled Ubuntu, but now it doesn't see my Linksys WUSB300N wireless adapter. I have tried ndiswrapper and that didn't work, and i can't find anything else about it. Im on XP right now which sees it fine, gets 65 Mbps. Is there any way to install the driver for it without getting on the internet in Ubuntu cuz it kinda doesn't have Internet? Many thanks in advance.

---

### Post by baltadt on 2009-09-22
I had the same problem with my linksys adapter. Never did get it to work. It's the chipset that is used...not recognized by ubuntu. Might be fixed in karmic but I just sold mine on ebay and bought a new one

---

### Post by cariboo on 2009-09-23
THe driver is probably installed already. Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will ask for your user password, just type it at the prompt, it will not be echoed back to you. The command will create a text file called network.txt that will list all your networking devices, and will tell us if your wireless adapter is detected and the driver loaded.

Copy network.txt to your Windows partition and paste it into your next post.

---

### Post by z400100500 on 2009-09-23
well here it is:

  *-network
       description: Ethernet interface
       product: 190 Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:1e:90:f8:84:a7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:48:a3:6d:ca:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Actually Im hooked up to a Belkin right now. Does that make a difference? I don't get internet on either. It would be better to get the Belkin to work though.

---

### Post by z400100500 on 2009-09-25
Hey if this helps I found that my WEP encryption key shows up under network connections, but nothing is transmitting.

---

