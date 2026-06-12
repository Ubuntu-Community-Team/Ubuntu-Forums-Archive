---
title: "PLS Help: ubuntu installed But NOT finding wireless Connection"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Unhubbed on 2010-01-05
[B][COLOR=#008000][COLOR=black]I was able to download and instal ubuntu 9.10 useing[/COLOR] [COLOR=red]_Unetbooting.com_[/COLOR] [/COLOR][COLOR=black],also I was able to install it to my computer, everything seemed ok but ubuntu wont find my wireless connecton, so i added my Belkin manualy in settings to ssid, saved restarted and still NO connectivity, CAN ANYONE HELP?[/COLOR]

Edit: My computer is a brand new Acer Aspire One netbook Model D250-1842
[/B]

---

### Post by warfacegod on 2010-01-05
Go to System> Administration> Hardware drivers and look to see if you have a driver for it and if it is activated.

---

### Post by Unhubbed on 2010-01-05
Ok...I went were u said and it searched and said, "No proprietar drivers are in use on this computer"... anything else that can help?

---

### Post by Ubunt24me on 2010-01-05
have the same computer and the same issue.  Running Ubuntu 9.04 for now.

---

### Post by Unhubbed on 2010-01-05
Ok, well how do I uninstall ubuntu 9.10 and partition?

---

### Post by warfacegod on 2010-01-05
This is part of what helped me a few years ago. You probably don't have the same wireles card I do but it's a good place to start.

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/")

---

### Post by warfacegod on 2010-01-05
Here's another. Don't give up on Linux too quick, Windows has allot of wireless issues as well and their support isn't nearly as good.

[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by bkratz on 2010-01-05
It would be helpful if you would go to the Terminal

Applications>>Accessories>>Terminal
and type in 
sudo lshw -C network   (that is LSHW in lowercase)
copy/paste the output received back here.


By the way your password will be required, but nothing will show on the screen when you do--just hit enter

---

### Post by Unhubbed on 2010-01-06
Thanks for all the help. I installed 9.04 with the Unetbooter program...works great

---

### Post by BigPoppaMafia on 2010-01-21
> **bkratz said:**
> It would be helpful if you would go to the Terminal

Applications>>Accessories>>Terminal
and type in 
sudo lshw -C network   (that is LSHW in lowercase)
copy/paste the output received back here.


By the way your password will be required, but nothing will show on the screen when you do--just hit enter
Here is the output please help
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mrwashington@ubuntu:~$ sudo lshw -C network
[sudo] password for mrwashington: 
Sorry, try again.
[sudo] password for mrwashington: 
Sorry, try again.
[sudo] password for mrwashington: 
Sorry, try again.
sudo: 3 incorrect password attempts
mrwashington@ubuntu:~$ sudo lshw -C network
[sudo] password for mrwashington: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:55:fa:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e1:06:f3:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f6000000-f600ffff
mrwashington@ubuntu:~$

---

### Post by lkraemer on 2010-01-21
If I remember correctly 9.10 uses the ath5 driver.  To find out you can post the output of the commands below.

My Compaq has the Atheros (AR5007) AR242x Wifi card, and I am using the
madwifi drivers. They seem to work good. I am not sure your card is
supported by madwifi. I'd search the forum and see what you find
after you find the exact card.  Copy & paste the following commands:
```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig

```
will give you more information.

madwifi - if yours is supported:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
Then go to the hal-0.10.5.6 at
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

lk

---

### Post by bkratz on 2010-01-21
> **BigPoppaMafia said:**
> Here is the output please help
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mrwashington@ubuntu:~$

Actually this thread especially post #5 should help, if not post the output of 

sudo iwlist scan 

Also do you have some switch that needs to be turned on?

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR5001](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR5001)

You probably should start a new thread to be better seen!

---

