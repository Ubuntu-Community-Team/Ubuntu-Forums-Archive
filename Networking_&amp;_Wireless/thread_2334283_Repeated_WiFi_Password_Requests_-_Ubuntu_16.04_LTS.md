---
title: "Repeated WiFi Password Requests - Ubuntu 16.04 LTS"
date: 2016-08-18
forum: Networking &amp; Wireless
---

### Post by eliotc2 on 2016-08-18
Hi All. I've recently upgraded to 16.04 and have since been having the above problem. Although, I had similar, intermittent problems with the older version of Ubuntu (14.x). When connecting to my WiFi network, I enter a correct password, the system tries to connect and then asks me for the password again. Obviously, each time I am inputting the correct password. No problem connecting to the router with other devices such as Android phones. I am unable to access the config of the router - locked down by the service provider, so I am unable to change any of the encryption settings that some previous threads have suggested. Network Manager shows that the connection uses WPA & WPA2 Personal security settings. My laptop can see the default gateway - connects fine via Ethernet.

I am an unexperienced Ubuntu user, so please, if possible, try to use layman terms. My knowledge of Ubuntu terminal commands is poor to say the least. I've looked through tonnes of threads on this but can't find anything that helps. 

Any suggestions, anyone, please?

---

### Post by eliotc2 on 2016-08-19
A small update on this. I've scanned the web and have been able to find username and password for my router, so I can get in and change encryption settings if necessary. But that seems preposterous; it would mean, for example, that I wouldn't be able to connect to any WiFi networks in hotels, without firstly accessing their router and changing it's configuration to suit my requirements. Things like this should just work, no?

---

### Post by eliotc2 on 2016-08-21
I've since learned how to do an output of my config using [COLOR=#111111][FONT=Consolas]sudo lshw -class network[/FONT][/COLOR]

Here's the output, hope it helps:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:d3:db:7d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.132 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:30 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 0c:84:dc:d1:59:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.4.0-34-generic firmware=610.812 link=no multicast=yes wireless=IEEE 802.11bgn
eliot@eliot-Lenovo-B575e:~$ ^C
eliot@eliot-Lenovo-B575e:~$

---

### Post by eliotc2 on 2016-08-21
Also, using command: [COLOR=#111111][FONT=Consolas]lspci -nn -d 14e4: Produced the following ouput:

[/FONT][/COLOR]02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)


[COLOR=#111111][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by eliotc2 on 2016-08-21
SOLVED. Found this link 

[http://http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

Installed the updated drivers and now connected wirelessly :-)

---

