---
title: "No Network manager in pull down menu's"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by JohnPta on 2009-02-02
I do not have Network manager on any of the pull-down menu's on any of my computers but Network manager is installed on all of them, according to Synaptec Package manager. 
How can I get the network manager on the pull down menu's. I need that because nearly every forum I read, about wireless internet, they talk about use the Network manager.

---

### Post by Guille Damke on 2009-02-02
The Network Manager is located in the bar next to the clock, usually in the top-right of the screen.

---

### Post by JohnPta on 2009-02-02
There I only have "Manual Network Configuration" and in that package is not much to configure.

---

### Post by Guille Damke on 2009-02-02
Hi,
I think we need more information. 
What do you need to do? 
Which version of Ubuntu are you running? 
How are you connected to the Internet (wireless or wired connection)? 
It gives you different options if you left or right click on it (try both). Also, if it is detecting wifi connections, they will be listed there. Also it works for wired connections. Do you know if your wireless card is detected and configured in your system?

---

### Post by JohnPta on 2009-02-02
I want to install a wireless connection to my router.
I am running Ubuntu 8.10.
At the moment I am using a wired connection but I would like to get it also going under wireless and this is what I get when I run the command "sudo lshw -C network" 

root@jan-laptop:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:f8:02:31
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=10.0.0.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:f3:fe:c0:fd:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

As you can see Ubuntu recognizes the wireless device but I can not address it or let's say I do not know how to address it.
According to me does the software not detect WIFI connections.

The wireless card is recognized and detected in the software see above. 

Thanx. 


> **Guille Damke said:**
> Hi,
I think we need more information. 
What do you need to do? 
Which version of Ubuntu are you running? 
How are you connected to the Internet (wireless or wired connection)? 
It gives you different options if you left or right click on it (try both). Also, if it is detecting wifi connections, they will be listed there. Also it works for wired connections. Do you know if your wireless card is detected and configured in your system?

---

### Post by Guille Damke on 2009-02-02
Ok, you have an Atheros card, can you choose "enable wireless" if you right click on the Network Manager Icon? If you cannot, probably there are some issues with the driver. I can suggest you to check your file 
```

/etc/network/interfaces

```
it should look like this:
```
auto lo
iface lo inet loopback

```
If you have some extra lines, add a comment (#) at the beginning of them and reboot.

Besides, people sometimes have troubles with this Atheros wifi. The way they solve this is:
1. Disable/Uninstall the ATheros driver, which I think is in 
System>Administration>Hardware_Drivers. 
2. Install Linux Backports Modules. If you are in Intrepid, then do:
```

 sudo apt-get install linux-backports-modules-intrepid-generic

```
3. Reboot.
Then try to connect using the network manager, the networks should be listed there. Be aware that after a kernel update, you probably have to reinstall the backport modules for the new kernel, but the command is the same.

Also, have a look at this similar issue, I think they have your card.

[http://ubuntuforums.org/showthread.php?t=1030653&page=2](http://ubuntuforums.org/showthread.php?t=1030653&page=2)

Good luck.

---

### Post by JohnPta on 2009-02-05
I got finally the Wireless Network card configured but now I am struggling with the connection to the Wireless router.

---

