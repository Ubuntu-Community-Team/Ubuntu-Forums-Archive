---
title: "Ubuntu 12.04 desktop version, HP Microserver- connected to network but no internet"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by philip.m.marek on 2013-12-08
I'm trying to configure an HP ProLiant Microserver G7 N54L with an embedded NC107i PCI express gigabit ethernet server adapter.
I'm running 12.04 desktop version and UBUNTU recognizes that there is a LAN connection but the browser won't connect to the internet and I can't get a ping from any websites in the terminal.

The microserver is hooked up to a router and was actually working when I had a direct connection from the modem to the server. It worked long enough for me to install Amahi and then I started having trouble.

The following is my terminal output from the command "[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -c network"[/FONT][/COLOR]:

  *-network               
       description: Ethernet interface 
       product: NetXtreme BCM5723Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 38:ea:a7:a9:e6:9d 
       size: 100Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msipciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration:autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128duplex=full firmware=5723-v3.35 ip=75.143.240.10 latency=0 link=yesmulticast=yes port=twisted pair speed=100Mbit/s 
       resources: irq:42memory:fe9f0000-fe9fffff  


I'm completely new to Ubuntu...

---

### Post by 7182818 on 2013-12-10
> **philip.m.marek said:**
> 
The microserver is hooked up to a router and was actually working when I had a direct connection from the modem to the server. It worked long enough for me to install Amahi and then I started having trouble.


Maybe your interface still has the settings from when it was directly connected to the modem?  For instance, if you configured a hard-coded IP address it may no longer be suitable for use behind the router and you might want to use DHCP instead.  You can look at the output of 'ifconfig' and also look in /etc/network/interfaces to help determine whether this is the case.

If you are still having problems after that, verify that you can ping the router from the server and then verify that you can ping a public address such as 8.8.8.8.  If these don't work or you are still having issues, post back and we can go from there. :)

---

