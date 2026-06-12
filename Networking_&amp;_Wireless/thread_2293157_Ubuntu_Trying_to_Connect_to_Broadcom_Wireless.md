---
title: "Ubuntu: Trying to Connect to Broadcom Wireless"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by jdd.wheeler on 2015-09-03
Hello, I am very new to Ubuntu and I have been trying to connect to the internet using wireless, but every time I try to use Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel it does nothing after I push apply changes. The first time I tried to do it the loading froze. Any help would be appreciated (:

---

### Post by kerry_s on 2015-09-03
were you connected to the internet ? the drivers are downloaded when using additional drivers.

what i do, i install off line making sure to check the box for third party drivers, it then installs the drivers that are in the installer, so after it's finished installing when i reboot the wifi is ready to go. i just did a clean install of 15.10 beta using this method about 2 hours ago. it works on any ubuntu version from 14 & up.

---

### Post by Bucky Ball on 2015-09-03
Welcome. I have changed your post to default font and point size. Please use them for regular posting. Thanks. 

Have you rebooted with no ethernet cable in? 

Please open a terminal and post the output of the following command after a reboot. When it asks for your password, type it in. It will be invisible, as it should be. :)

```
sudo lshw -C network
```

See the last link in my signature for how to put your output between code tags when posting.

---

### Post by jdd.wheeler on 2015-09-03
I was not connected to the internet before, and I rebooted without the ethernet cable in, but still no luck. 
This is the code I got after I entered 
```
sudo lshw -C network
```

```

*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4d:e9:cc
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
```

Thanks For All The Help

---

### Post by Bucky Ball on 2015-09-03
Plug the cable in, get online, and try this:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install firmware-b43-lpphy-installer
```

Pull the cable, reboot, run the 'sudo lshw -C network' command again if you're not online.

You may need to blacklist the driver you have installed for this to work. This:

```
driver=b43-pci-bridge
```

... seems to be the wrong one for this:

```
BCM4312 802.11b/g LP-PHY
```

---

### Post by jdd.wheeler on 2015-09-05
I got online with the cable, updated, unplugged, and rebooted. It didn't work and after running the command it gave back the same code. How do I blacklist it?

---

### Post by Bucky Ball on 2015-09-05
Open additional drivers and see what is enabled in there.

---

### Post by jdd.wheeler on 2015-09-06
This is what shows up when I go to additional drivers, but when I try to select the using broadcom wireless driver source the loading bar stops and all it says is "Applying changes..." and below that it says " A proprietary driver has a private code that Ubuntu developers can't review or improve. Security and other updates are dependent on the driver vendor.


[http://kayve.net/broadcom_wifi.png](http://kayve.net/broadcom_wifi.png)

---

### Post by Bucky Ball on 2015-09-06
Click 'Do not use this device' then do the instructions from post #5. Plug the cable in and:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-lpphy-installer
```

PS: Please attach large screenshots/pics by 'Go Advanced' or 'Adv Reply' and using the paperclip icon. Thanks. :)

---

### Post by jdd.wheeler on 2015-09-06
This is what happens after I enter in the last 2 commands:

```
sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-generic-lts-vivid linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firmware-b43-lpphy-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  firmware-b43-installer

E: Package 'firmware-b43-lpphy-installer' has no installation candidate
```

---

### Post by wildmanne39 on 2015-09-06
Please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

