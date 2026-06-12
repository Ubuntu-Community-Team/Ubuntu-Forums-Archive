---
title: "Need some help getting my wireless working!"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by Soggytoast on 2008-07-22
I installed Ubuntu 8.04 about a week ago, and have been trying to get my wireless internet working ever since.  I have a Dell Inspiron 5150 with a TrueMobile 1300 Mini-PCI card.  Most of the time I have been working from this guide:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

However, I have not had any success.

So far I have:

1.  Installed ndiswrapper 1.50 using synaptic from the instillation CD.  If I try to install by downloading the current version and follow the directions in the guide, I get tons of errors.

2.  Found and loaded the Windows wireless driver into ndiswrapper (bcmwl5.inf).

3.  If I type "ndiswrapper -l in the terminal, I get

```
bcmwl5 : driver installed
         device (14E4:4320) present (alternate driver: bcm43xx)
```

4.  If I type "iwlist scanning" in the terminal I get 
```
lo            Interface doesn't support scanning.

eth0          Interface doesn't support scanning.

wmaster0      Interface doesn't support scanning.

wlan0         Interface doesn't support scanning : Network is down
```

5.  I've tried to mess around with some of the stuff in the network tools, but I could never recognize my network.  I'm pretty sure the wireless card isn't even functioning.  

Help is much appreciated.  Thanks!

---

### Post by sputnikkk on 2008-07-22
Lets see the output from this ...

```
lshw -C network
```

I struggled with the command line and stupid Networkmanager on a fresh install of Hardy Ubuntu for sooooooo long.  The solution came in the form of ditching NWM - the default Ubu 8.04 Hardy Heron Wireless and Wired Netowrk GUI interface, and adding

Wicd software from the repository/Synaptic manager.

[http://www.wicd.net/download.php](http://www.wicd.net/download.php)

Installing Wicd in Ubuntu

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

These threads/guides showed me a bunch before I ended up with Wicd

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by Soggytoast on 2008-07-22
Output from lshw -C network:
```
xxxxx@xxxxx-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1d:5b:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:cc:d5:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

I guess I could try to install Wicd and see if it helps, but I don't have access to the internet on that computer.  Is there an easy way to install without the internet?

---

### Post by Soggytoast on 2008-07-25
I'm still kind of stuck at this point.  When I saw that the output said disabled, I thought that maybe my bios had turned off my wireless card.  I found the keystroke that does this, played with that and also disabled the option to turn off the wireless card in my bios.  None of that made a difference.  

I also tried to use fwcutter to hopefully install drivers, but whenever I try to run it I get something like "input file is invalid".

I don't really know what I should try next. :(

---

