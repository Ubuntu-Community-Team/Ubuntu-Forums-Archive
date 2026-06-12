---
title: "Unable to connect to the internet on ubuntu 14.04 LTS with USB modem"
date: 2015-02-01
forum: Networking &amp; Wireless
---

### Post by shane35 on 2015-02-01
I recently installed ubuntu 14.04 LTS but I'm unable to establish an internet connection.My modem is connected via usb and i have had no problems connecting to the internet in windows 7.I have tried setting it up by adding it manually as a mobile broadband connection but nothing happens when i try to connect.The modem im using is a Huawei E5331.I am unable to download any software due to having no internet so please don't suggest for me to do so,I've been working on this problem for awhile now so any help would be appreciated

---

### Post by TheFu on 2015-02-01
Welcome to the forums.

Sadly, it is highly likely that you'll need to download something, build it, to get this working.  But ... before we know that, we need to ask more than a few questions.
Please post the exact output, including the commands.  You can redirect the output from these to a file, then transfer those files to your phone (I assume the phone is how you are posting here).  When posting, it would also be most helpful if you can use "code tags" - the "Go Advanced" editing has a button for that.
```

# let us see if the hardware is even recognized
sudo lshw -C network
```

---

### Post by shane35 on 2015-02-01
These are the results and thank you for replying


```


code sudo lshw -C network
```


shane@shane-ESPRIMO-E3510:~$ sudo lshw -C network
[sudo] password for shane: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:19:99:4b:99:a1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f0020000-f002ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 58:2c:80:13:92:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ncm driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes
shane@shane-ESPRIMO-E3510:~$

---

