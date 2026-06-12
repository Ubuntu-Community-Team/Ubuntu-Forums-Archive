---
title: "No  internet"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Farharbour on 2011-06-17
I have a Dell  Latitude D610 that will  no longer connect to the   Internet. I have tried  reinstalling network manager but it  simply   does not  work .  I let the  computer  die from lack of  battery power   once before and the re-installation  restored  the Internet,  but no  this is  not working  at all. Does anyone have an  idea how  I might fix  this? For somereason  the internet icon  is not  shoing up so I  cannot right-click the internet icon in the upper right, to  "enable networking" checked?

---

### Post by jsgosselin on 2011-06-17
Hi Farharbour,
first thing first, can you do this 
```
sudo lshw -C network
```
,from a terminal and post back the result please.

---

### Post by shibu_sawyer on 2011-06-17
Wired dsl connection or wireless..

---

### Post by jsgosselin on 2011-06-17
Also, are you running on Natty or on Maverick?

---

### Post by Farharbour on 2011-06-17
Neither  wired nor wireless fuunctiion

---

### Post by Farharbour on 2011-06-17
Since the computer does not  connect to the internet, I cannot  paste the out put from the command above,  but it does  say " network  disabled " for both the  Ethernet (NetExtreme BCM5751)and and the wireless interface ( wlan0). All of the solutions  seem to reuire that the computer  be online ..  but that is the problem

---

### Post by Farharbour on 2011-06-17
I am  running Ubuntu  10.04 Lucid Lynx

---

### Post by jsgosselin on 2011-06-17
Ok, so no Internet access at all...and from what you said, it was running well before the crash. And, from what I understand, you have Network Manager currently installed on your computer.

What happens if you try to start Network Manager manually?

```
 sudo start network-manager

```

---

### Post by Farharbour on 2011-06-17
The response is " job already running: network-manger"

---

### Post by Farharbour on 2011-06-17
Another  change is that I  cannot  right  click the  netork manager  icon  to "  enable " I get  the " launch, properities remove etc.. " options

---

### Post by Farharbour on 2011-06-17
It ran  perfectly until  I  let the battery  die a second time

---

### Post by M1k3y on 2011-06-17
I had the same problem. Try using a USB and re installing Ubuntu that way. This worked for me (I'm not sure why). During the installation choose to get rid of your other ubuntu partition and make sure if you have a wireless switch that its on. Make sure to back up all of your files. Hope it helps
-m1k3y-

---

### Post by M1k3y on 2011-06-17
By the way when you re install Ubuntu make sure that it doesnt lose power.

---

### Post by Farharbour on 2011-06-17
So  I  should  download Ubuntu on  a  USB drive,  and reinstall  the operating  system? Just to  fix this?

---

### Post by Talon2 on 2011-06-17
Are you sure you haven't turned the wifi hardware off?

On my Latitude 2110 I have to hold down on Fn while pressing F6.  This toggles the wifi hardware on and off.  I have seen many people accidentally turn their radio off and wonder why they have no internet.

---

### Post by Farharbour on 2011-06-19
I have tried Fn F6 and  re-booted..  Still  no Internet at  all either wired or wireless

---

### Post by Farharbour on 2011-06-19
Here is the  terminal output:

*-network DISABLED      
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:cc:6c:01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=5751-v3.29a, BRCM ASF v6.15D latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:63:c8:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
skip@skip-laptop:~$ 


It appears that both  network connections are disabled. Can I enable them from the terminal?

Thanks again for you  suggestions and help

Skip

---

### Post by Swagman on 2011-06-19
```
 sudo ifconfig eth0 up
```

or wlan0 if it's wireless

---

### Post by wildmanne39 on 2011-06-19
Hi, try these commands.

```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
```
 lshw -C network
```
This will show one of four states. Claimed = driver loaded but not functioning. Unclaimed = no driver loaded. You may need to go to additional drivers or install Ndiswrapper. Enabled = driver loaded. So check the connections to the router. Disabled = Well, it says it all.

---

### Post by Farharbour on 2011-06-21
I tried the  commmands and  do not see the output language you  mention...  I must admit that this is  very frustrating...  I  have  been without internet  to days and I guess I need another PhD to run  Ubuntu  properly.. May it is time to go back to Microsoft? 

skip@skip-laptop:~$ sudo ifconfig wlan0 up
skip@skip-laptop:~$ sudo ifconfig  wlan0 down
skip@skip-laptop:~$ sudo ifconfig  wlan0 up
skip@skip-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:cc:6c:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a, BRCM ASF v6.15D latency=0 multicast=yes
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:63:c8:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Farharbour on 2011-06-21
Is it  possible to re-install  windows without loosing information  and  files? I am  defeated and really  need to use my  computer... Thanks  for your  attempts to  help, but  such simple problem should not  take days to resolve. I just don't  have the computer background to run  Ubuntu it  seems

---

