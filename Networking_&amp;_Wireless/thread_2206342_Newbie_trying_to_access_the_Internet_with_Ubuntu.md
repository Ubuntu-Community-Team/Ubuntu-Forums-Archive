---
title: "Newbie trying to access the Internet with Ubuntu"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by mihnea2 on 2014-02-18
Hey guys, 

I am extremely new to Ubuntu, i don't know anything about Terminal Commands, because I have been using Windows, and now i decided to install Ubuntu.

But I am facing some issues with my Belkin f7d4101v2 USB Network adapter.
My Ubuntu installation does not recognize the adapter, because of missing drivers.

Could someone help me with an idiot proof installation guide for absolute beginners?

Thanks in advance.

---

### Post by send2 on 2014-02-18
Hi, intro to terminal here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal), here is a thread on useful links about the terminal: [http://ubuntuforums.org/showthread.php?t=819691](http://ubuntuforums.org/showthread.php?t=819691), there are of course many more links, another page with some info: [http://askubuntu.com/questions/151488/what-is-the-best-way-to-learn-how-to-use-ubuntu-with-terminal](http://askubuntu.com/questions/151488/what-is-the-best-way-to-learn-how-to-use-ubuntu-with-terminal), another page: [http://www.tuxarena.com/static/intro_linux_cli.php](http://www.tuxarena.com/static/intro_linux_cli.php), another page here: [http://www.distrogeeks.com/using-terminal-ubuntu/](http://www.distrogeeks.com/using-terminal-ubuntu/). 


Seems like some Belken drivers are not compatible with Ubuntu, I don't know if this has changed because I don't use that particular brand, here is a forum thread on that issue: [http://ubuntuforums.org/showthread.php?t=1927739](http://ubuntuforums.org/showthread.php?t=1927739), here is a list of harware support components listing info on Belken: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin), I will defer to someone else who can help further...

Welcome to Linux and Ubuntu!

---

### Post by oldos2er on 2014-02-18
With the adapter plugged in, open a terminal (Ctrl-Alt-t) and run ```
lsusb
``` Please copy and paste the output here.

---

### Post by Bucky Ball on 2014-02-18
*Thread moved to **Networking & Wireless**.*

You may have better luck here. People will be gentle as you make it clear you're new here. And welcome! ;)

Post the output of oldos2er's command, and you also might like to post the result of this, with the USB plugged in:
```

sudo lshw -C network
```

That will show us the current state of affairs, whether Ubuntu has attempted to install a driver and if there is any action.

---

### Post by mihnea2 on 2014-02-19
Thanks for the repiles,

here i have the logs for both of the Terminal commands.
First one:

Bus 003 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 003 Device 004: ID 050d:110a Belkin Components 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 004: ID 0e5e:6622 Conwise Technology Co., Ltd. CW6622
Bus 006 Device 003: ID 046d:c066 Logitech, Inc. 
Bus 006 Device 005: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 006 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Second one:
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:70:29:44
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s

---

### Post by Bucky Ball on 2014-02-19
Thanks, but could you give that info again, with the Belkin plugged in? It's not showing in your output of 'sudo lshw -C network'. ;)

---

### Post by mihnea2 on 2014-02-20
Here i have the output of the sudo lshw -c network:
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:70:29:44
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:77 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
mihnea@Mihnea-desktop:~$


I think it isn't showing up because even the light on the Wireless Adapter istn't lighting up.
But in the other command it is showing as Belkin components.

---

### Post by Bucky Ball on 2014-02-20
Ok, try this. It looks like you're online with a cable fine so follow chilli's advice here:

[http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576](http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576)

... and see post 8# for some ways of checking everything went ok and things are as they should be. The link is from post #6 here:

[http://ubuntuforums.org/showthread.php?t=2157571](http://ubuntuforums.org/showthread.php?t=2157571)

Looks like this card has been working for a year, but before that, a nightmare. Perhaps that's why there's not many around the community.

---

