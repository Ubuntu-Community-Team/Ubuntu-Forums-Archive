---
title: "Internet frequently disconnecting"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by weirdAbacist on 2011-08-30
Hello! I apologize if this question is redundant, but the other threads I looked at didn't seem to solve my problem.

I have a laptop (Lenovo Y510) and a netbook (Acer Aspire One), both running Ubuntu 11.04. I can connect to the internet on either machine, but the laptop seems to be disconnecting every 5 minutes. If I check the connection, it says it is still connected, even though I cannot access any website on Firefox or log into Skype. If I reconnect to the internet it resumes functionality, albeit just for another 5-10 minutes.

My netbook on the other hand works just fine. I am using it right next to my laptop with no troubles, and the other people I reside with have expressed no difficulty with connecting to the internet here. As a result I am forced to conclude that it is my laptop that is problematic, and not the internet.

Since I am still a newbie to Ubuntu (and not very tech savvy to begin with) I have absolutely no idea what the problem is or even how to determine the problem, let alone find a solution. Any help is appreciated.

---

### Post by duke.tim on 2011-08-30
Start by trying to update the computer

(in case you don't know unity has a navigation bar/panel on the left, gnome has a panel on the top and bottom of the screen)

in unity search for update
in gnome it is System -> Administration -> Update Manager

Also you might need to enable restricted drivers
in unity search for drivers
in gnome it it System -> Administration -> Additional Drivers


Afterwards take a look at these threads *they show fixes for ubuntu 9.04*:
[http://ubuntuforums.org/showthread.php?p=7363642&highlight=wifi#post7363642](http://ubuntuforums.org/showthread.php?p=7363642&highlight=wifi#post7363642)
[http://ubuntuforums.org/showthread.php?p=7359462&highlight=wifi#post7359462](http://ubuntuforums.org/showthread.php?p=7359462&highlight=wifi#post7359462)

These may not work for Ubuntu 11.04

The great thing is that there is some great threads to look through in case you have problems with your laptop model *Note these threads are quite old, but one seems fairly active still

[http://ubuntuforums.org/showthread.php?t=870681](http://ubuntuforums.org/showthread.php?t=870681)
[http://ubuntuforums.org/showthread.php?t=687663](http://ubuntuforums.org/showthread.php?t=687663)

---

### Post by decoherence on 2011-08-30
Could be the driver for your network adapter. What kind is it? You can check by running the following and posting the output here.

```
sudo lshw -C network
```

---

### Post by weirdAbacist on 2011-08-30
> **decoherence said:**
> Could be the driver for your network adapter. What kind is it? You can check by running the following and posting the output here.

```
sudo lshw -C network
```

PCI (sysfs)
*-network
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
vendor: ntel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 61
serial: 00:1d:e0:40:9e:2f
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic-pae firmware=228.61.2.24 ip=129.64.216.142 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
resources: irq:48 memory:fe0fe000-fe0fffff

The computer seems to work better when I move it to other rooms, so I suspect that the problem is related to a weak wireless signal, but I am still confounded as to why my netbook runs fine while my laptop is more selective.

---

### Post by weirdAbacist on 2011-09-01
Since I'm dualboot Windows/Linux, I tried booting up Windows and the internet connects just fine, so it's probably a driver/software issue, but whenever I go to the Update Manager it says I am up to date.

---

### Post by duke.tim on 2011-09-01
Did you check to see if restricted drivers were enabled?


in unity search for drivers

in gnome it it System -> Administration -> Additional Drivers

---

### Post by weirdAbacist on 2011-09-03
> **duke.tim said:**
> Did you check to see if restricted drivers were enabled?


in unity search for drivers

in gnome it it System -> Administration -> Additional Drivers

There are three drivers available: Two types of NVIDIA graphics cards (one of which was activated but not in use) and a software modem, which was not activated. I just activated the software modem now, and it is currently in use. Could this have been the cause of the internet problem?

---

### Post by duke.tim on 2011-09-03
Could be if you were using some other driver before, but it doesn't sound like it is a wireless driver you just enabled. The likely hood is that it is just a weak wireless signal (or interference)

---

### Post by devanson on 2011-10-02
> **weirdAbacist said:**
> Hello! I apologize if this question is redundant, but the other threads I looked at didn't seem to solve my problem.

I have a laptop (Lenovo Y510) and a netbook (Acer Aspire One), both running Ubuntu 11.04. I can connect to the internet on either machine, but the laptop seems to be disconnecting every 5 minutes. If I check the connection, it says it is still connected, even though I cannot access any website on Firefox or log into Skype. If I reconnect to the internet it resumes functionality, albeit just for another 5-10 minutes.

My netbook on the other hand works just fine. I am using it right next to my laptop with no troubles, and the other people I reside with have expressed no difficulty with connecting to the internet here. As a result I am forced to conclude that it is my laptop that is problematic, and not the internet.

Since I am still a newbie to Ubuntu (and not very tech savvy to begin with) I have absolutely no idea what the problem is or even how to determine the problem, let alone find a solution. Any help is appreciated.


Hi, I am facing the same Issue. Need help.. My PC is Updated and the Restricted driver is enabled.

I issued this command : sudo lshw -C network

Output:
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: e0:69:95:c9:63:8f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.13-4 ip=1.23.228.71 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f7100000-f711ffff memory:f7128000-f7128fff ioport:f040(size=32)


Why my internet is often disconnecting?

---

### Post by duke.tim on 2011-10-04
devanson it would be a good idea to start a new thread, you are more likely to get the help you need.


I apologize beforehand if you already know how to start a thread, but just in case.
At the home page of the forms click on the section that seems most relevant (probably [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) )
and look in the upper left hand corner.

---

