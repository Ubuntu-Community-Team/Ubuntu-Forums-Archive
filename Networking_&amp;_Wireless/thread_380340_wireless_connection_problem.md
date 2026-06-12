---
title: "wireless connection problem"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by epilogue on 2007-03-09
hi, i am a new ubuntu user. i installed it yesterday.

i have a asus laptop, model: W5F. i can use my wireless connection with other os but when i use ubuntu it doesnt work. is it possible to make it work at ubuntu?

---

### Post by Floppyjoe on 2007-03-09
This link may be of help.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Floppyjoe

---

### Post by handaxe on 2007-03-09
Hi,

You don't provide much info :(......there are quite a few things to consider here as to why is will not work. Wifi card make and kernel driver availability, use of ndiswrapper (to use the Windows driver if Linux kernel drivers are not available or do not work), encryption type etc.

At the command prompt, type:

```
sudo lshw -C network
```

and post the output.

Some folk have access point/encryption rather than hardware problems. Assuming that you have driver & other hardware issues sorted out, you might try WICD as your manager of wireless connections. Under active development.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (clicking on the dowloaded deb file should bring up the installer). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption.

[B] NB - ver 1.0.9 might give problems so use 1.0.7 for the mo'.

[/B]HA

---

### Post by epilogue on 2007-03-10
here my result

  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@07:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:fe7ff000-fe7fffff irq:5
  *-usb
       description: Bluetooth wireless interface
       vendor: ASUSTek Computer, Inc.
       physical id: 2
       bus info: usb@4:2
       version: 19.15
       serial: 0194E8-5B-0002
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@08:04.0
       logical name: eth0
       version: 10
       serial: 00:17:31:1a:ce:58
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=10.0.0.4 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:fe8fe400-fe8fe4ff irq:50

i have no idea about what should i do =)

---

### Post by epilogue on 2007-03-10
when i first installed ubuntu, in networking i could see wireless connection but i wasnt able to enable it. i tried to install drivers. followed the instructions [http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL) from here. but now i only see wired and dial up connections in the networking. :s

---

### Post by handaxe on 2007-03-10
Hi,

I am surprised by what you found - I have the same wireless card and Ubuntu detected it ok and installed the drivers. Your output shows that the card is not properly set up and no driver is reflected.

First uninstall the source forge driver, then in synaptic, re-install or install the linux-restricted-modules-2.6.17-11-generic.

Reboot.

See if you have eth1 shown under logical name: after 
sudo lshw -C network
HA

Look what i found - [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452).

Seems likely your problem and the solution above should work.

---

### Post by epilogue on 2007-03-12
hi again

after making so much effort to solve problem, i decided to reinstall ubuntu(i had nothing to lose). now it recognises my wireless card 

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@07:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:26:77:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:fe7ff000-fe7fffff irq:177
  *-usb
       description: Bluetooth wireless interface
       vendor: ASUSTek Computer, Inc.
       physical id: 2
       bus info: usb@3:2
       version: 19.15
       serial: 0194E8-5B-0002
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@08:04.0
       logical name: eth0
       version: 10
       serial: 00:17:31:1a:ce:58
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=10.0.0.4 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:fe8fe400-fe8fe4ff irq:50

```

i installed the wicg and it can see wireless connections near to me. but i havent been able to try it if it connects. as soon as possible i will try to connect but i think its gonna connect cos looks like no problem with card. 

so i can say the result is good(although it costed reinstalling the system. but of course due to my newbieness). so much thanks for your help. 

now i will try to make my bluetooth mouse work :popcorn:

---

### Post by epilogue on 2007-03-12
i am writing this while connected to wireless network. i am glad to have it worked. 

cheers

---

