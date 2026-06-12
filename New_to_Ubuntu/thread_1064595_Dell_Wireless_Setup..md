---
title: "Dell Wireless Setup."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Flufflebuns on 2009-02-09
I am still a beginner to Ubuntu, and just loaded up a second older computer with Xubuntu 8.10. I need assistance getting my wireless up and running. I have an external Dell Wireless 1350 WLAN PC Card (and no internal card). It worked fine in Windows, but I have no clue as to how to get it up and working with Xubuntu. 

Also if it helps, the computer is a Dell Inspiron 1000 Laptop.

Thanks.

---

### Post by doctorbighands on 2009-02-09
[This]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") is a great place to start.

---

### Post by Peter09 on 2009-02-09
Can you post the output of the terminal command

```
lshw -C network
```

---

### Post by Ponderous on 2009-02-09
Here is my output:
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:b8:c8:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:4a:06:d1:8f:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


My problem seems to be this.  I have installed ndiswrapper from the Add/Remove list and I even located my .inf driver file and clicked add driver.  When I click configure network it says 'could not find network configuration tool."  

Not sure what to do here.  I want to throw the damn thing out the window.

Thanks for any help everyone.

---

### Post by Peter09 on 2009-02-10
try putting this into a terminal to get the driver

```
sudo apt-get install b43-fwcutter
```

---

### Post by Ponderous on 2009-02-10
> **Peter09 said:**
> try putting this into a terminal to get the driver

```
sudo apt-get install b43-fwcutter
```

This is what I need to do to correct my problem?  That seems like a different driver than what I got from the Dell site.

---

### Post by Ponderous on 2009-02-10
I still can't configure my network.  I tried the b43-fwcutter and then reboot.  When I go to Windows Wireless Drivers under System, and click config network it says "Can't find network configuration tool."

Any other suggestions?

---

