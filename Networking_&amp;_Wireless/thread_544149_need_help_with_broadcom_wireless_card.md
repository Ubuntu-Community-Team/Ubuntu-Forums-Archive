---
title: "need help with broadcom wireless card"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by decrot on 2007-09-06
im a total noob at this so bear with me
i have a mn-720 card from microsoft and found 2 files, mn720-ankh.inf and bcmwl5.sys and im using 6.06

first, i installed ubuntu cleanly and then i installed ndiswrapper-utils from the cd 
then i did
ndiswrapper -i ***.inf from the driver folder
did the modprobe and everything

when i type ndiswrapper -l    it says
mn720.inf   driver installed and hardware detected.

from the network manager i can see may card and has all the right info.

i even modified files so the logical name is wlan0

my problem is that the card won turn on. the lights simply dont come on and i still cant connect to the web
i know that the card works since i used it for win2k

any help?

---

### Post by tgalati4 on 2007-09-06
What is the output of:

>ifconfig

and

>iwconfig

---

### Post by kevdog on 2007-09-06
Sounds like a tough one.

I dont know what you mean by not turn on, since you say Network Manager sees the card.

If after a reboot, you type

lshw -C network

Does you card show up, and is the driver listed ndiswrapper??  Something like the following
```

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [SIZE="4"]**driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys**[/SIZE] ,LLC.,02/1 ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

---

### Post by decrot on 2007-09-06
no
when i do lshw -C network the driver says

bcm48xx 

and no ndiswrapper

also when i try modprobe ndiswrapper, it says
FATAL: Module ndiswrapper not found

and when i do: ndiswrapper -v,  it says
utils version: 1.7
driver modinfo: could not find module ndiswrapper


any help?

---

### Post by kevdog on 2007-09-06
Do the following:

echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist

Reboot.

Then recheck lshw -C network and post ndiswrapper -l

---

### Post by decrot on 2007-09-06
when i hit lshw -C network it reads

*-netowrk UNCLAIMED
         description: Network Controller
         product:  BCM43xG 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@02:00.0
         version: 02
         width: 32 bits
         clock: 33MHz
         capabilities: cap_list
         resources: iomemory:12000000-12001fff irq:9


and when i do ndiswrapper -l

mn720-ankh : driver installed
               device (14E4:4325) persent (alternate driver: bcm43xx)

---

### Post by kevdog on 2007-09-06
Did you insert the module into the kernel?

sudo modprobe ndiswrapper

Do that and then recheck
lshw -C network looking for a driver statement

---

### Post by decrot on 2007-09-06
omg my wireless card works now
big thaks for the help

---

### Post by decrot on 2007-09-06
i have one more problem now
my network card doesnt automatically start when i boot up ubuntu
i have to always go to terminal and do
sudo modprobe ndiswrapper  to get it started

anyway to fix this?

---

### Post by kevdog on 2007-09-06
Just type this at command line to add it to the modules loaded at boot

echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by regan fin on 2007-10-05
I would like to say thanks also.  I just installed an mn720 on an acer travelmate 200 using these instructions and am almost done.  I hope that this in not considered hijacking, if so I apologize.

However, after following these threads I was able to install the card and can see it.  The network manager shows my home network but the card will not connect.  I have a very good signal.  It seems to be attempting a connection but then times out.  Do you have any suggestions.

---

### Post by kevdog on 2007-10-06
You are not hijacking the thread since it basically came to a resolution.

Couple things I need to know:
#1) Are you connecting to a network with any encryption?? If WPA/WEP, turn off for now until we can make a basic connection.  We can then fine tune the process!
#2) Do you see your network with :
iwlist scan
#3)Network Manager frankly is sometimes just stubborn, so to verify that all your drivers are set up correctly I usually just make a manual connection first, then screw around with any GUI such as Network Manager or WICD.

Here is how to make an unencrypted manual connection from the command line assuming your wireless interface is wlan0 (it might be wlan0, eth1, or something else -- lshw -C network will tell you under the heading of your wireless card -- look for the line logical name)

sudo ifdown wlan0
sudo ifup wlan0
sudo iwconfig wlan0 essid "NAME_OF_NETWORK_IN_QUOTES"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0


This should give you an IP address.  If it does than all drivers are working and we can move onto bigger and better things.

---

