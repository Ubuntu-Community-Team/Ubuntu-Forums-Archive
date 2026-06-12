---
title: "Another Ubuntu Wireless Internet Issue.  Please Help!!"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by tech7 on 2010-08-25
I'm new to linux, I installed Ubuntu 10.04.1 Lucid via wubi to run alongside my Win Vista OS (HP Pavilion DV9620).  Obviously, I ran into to the issue where there is no wireless internet capabilities.  And while following close to a dozen different forum help tickets, I've;
-installed appropriate ndiswrapper common(acccording to ubuntu site)
-installed appropriate ndiswrapper utils(acccording to ubuntu site)
-installed appropriate ndisgtk(acccording to ubuntu site)
-d/l's windows driver for wireless card (which was .exe file)
-d/l'd and attempted to install cabextract (to extract .inf file) w/o success
-d/l'd and attempted to install newest version of Wine as it was nowhere to be found on this install of ubuntu, and it will start to run in terminal but somewhere in the dashing lines i see there are no languages (i.e C,) present.
-uninstalled and reinstalled Ubuntu believing there was something wrong with install process.
-Then did everything all over again.
Can somebody help me?  I was so looking forward to ditching windows and making sweet love with linux :(  now after two days of hell, I'm really disappointed.....   :(

---

### Post by beew on 2010-08-25
What is your wireless card? 

In the terminal type ```
sudo lshw -C network
``` and let's see the output. You shouldn't need ndiswrapper .

---

### Post by tech7 on 2010-08-25
Broadcom BCM4311 802.11/g WLAN

---

### Post by beew on 2010-08-25
Ok follow the instructions here.
[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"]
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx[/URL]

---

### Post by tech7 on 2010-08-25
sorry, here's the reply..

*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:cf:bc:6f
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:ba:b6:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
cyberswim@ubuntu:~$

---

### Post by tech7 on 2010-08-25
thanks a lot for your help so far..  I followed the instructions and everything seemed to work out great, until reboot was required.  Drivers won't work after reboot.  In the hardware drivers utility it says that my driver is activated but not currently in use.  If I unplug my ethernet connect there are still no prompts and after looking around for quite some time, i still cannot find a way to connect to wifi..

---

### Post by tech7 on 2010-08-25
okay, nevermind, apparently i just needed to run this command now:
sudo ifconfig eth1 up

thanks for the help..

---

### Post by tech7 on 2010-08-25
> **tech7 said:**
> okay, nevermind, apparently i just needed to run this command now:
sudo ifconfig eth1 up

thanks for the help..
doesn't work now...  the preceding commands posted in another forum i suppose set something up for that to work..  i don't know what to do now..  I can't use this if I have to stay next to my router for internet connection..  
any suggestions from anyone?  
my connections utility up in the upper right corner will display nothing about wireless connections, only wired connections.  unless I run all those other commands from that other forum..
Also, I performed all the steps in the link above once again; still no luck, still no wireless..  At least the driver is present now..

---

### Post by tech7 on 2010-08-25
[http://ubuntuforums.org/showthread.php?p=9765750#post9765750](http://ubuntuforums.org/showthread.php?p=9765750#post9765750)

Here is how I fixed that issue..

---

