---
title: "wired ethernet stopped working after recent updates"
date: 2022-01-03
forum: Networking &amp; Wireless
---

### Post by EXAsoft on 2022-01-03
Have a laptop HP Elitebook 1050 G1 with Ubuntu 18.04 (used almost daily) and Windows 10 (used very rare, and not recently). A few months ago, I added more SSD memory and set up Ubuntu 20.04 on the new space. However, I had no time to finish it, so I continued working on Ubuntu 18.04. Now a few days ago, I finally wanted to tackle the Ubuntu 20.04 project again. Of course, there were tons of updates, coming in through the wired ethernet connection just fine. 

Today I booted and had no ethernet connection. Reboot, no change. Wireless is working, but not wired. The wired connection is done through a RJ45 to USB-C connector, works fine on Ubuntu 18.04 and worked just before the updates, so the hardware is not a problem. I rather suspect that a driver has been "eliminated" through the updates. 

Details: 
[LIST]
[*]Ubuntu 20.04.3 LTS (Focal Fossa) 64-bit 
[*]Kernel Linux 5.11.0-43-generic x86_64 
[/LIST]
 
/etc/NetworkManager/NetworkManager.conf:
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
```

/etc/netplan/01-network-manager-all.yaml:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```


Output of `sudo lshw -C network`:
```

  *-network                 
       Beschreibung: Kabellose Verbindung
       Produkt: Wireless-AC 9560 [Jefferson Peak]
       Hersteller: Intel Corporation
       Physische ID: 14.3
       Bus-Informationen: pci@0000:00:14.3
       Logischer Name: wlp0s20f3
       Version: 10
       Seriennummer: 04:d3:b0:0f:da:07
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=iwlwifi driverversion=5.11.0-43-generic firmware=46.4d093a30.0 9000-pu-b0-jf-b0- ip=192.168.1.35 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       Ressourcen: irq:16 memory:ed310000-ed313fff
```

The above shows only the wireless connection, so clearly there is something missing. How can I get back the wired ethernet connection?

---

### Post by TheFu on 2022-01-03
20.04 doesn't use ifupdown. That has been deprecated with netplan put in place.  On a desktop (non-server), 99% of the folks here would use network-manager.

Since the system doesn't know about the wired NIC, you need to determine what it is, exactly, and load the driver.  Since 18.04 is working, you can boot into that and get the NIC name/chip and driver information (but not the driver module).

Thinking about this a bit more ... can you create a fresh 20.04 "Try Ubuntu" flash boot drive and boot from that?  After booting from it, does the wired connection work? If it does, then you have a copy of the correct driver and just need to determine the package it comes from (use apt search or dpkg-query to get the package name), then try booting into the 20.04 install, connect with wifi and install that package.  Once installed, you can do a [/b]sudo modprobe[/b] to get it loaded into the kernel, then maybe restart the networking subsystem (may not be necessary), and go into the normal network manager applet to disable the wifi connection and toggle the wired connection so that works.

Once the package is installed, the driver should be loaded in all boots going forward.
Probably not important, but modules are in /lib/modules/`uname -r`

In theory. ;)

From my notes:
```
# ###############[ APT Package Search ]############
# Which package provides a specific file?
dpkg -l {part-of-package-name}*
dpkg -S /usr/bin/passwd
dpkg-query --search '/path/to/file'
apt-file search vim

# list of files in a known package:
dpkg-query -L {pkg-name}

```

---

### Post by EXAsoft on 2022-01-06
> **TheFu said:**
> 
Thinking about this a bit more ... can you create a fresh 20.04 "Try Ubuntu" flash boot drive and boot from that?  After booting from it, does the wired connection work? If it does, then you have a copy of the correct driver and just need to determine the package it comes from (use apt search or dpkg-query to get the package name), 

@TheFu: Thanks for the brilliant idea! When booted from 20.04 USB drive, I have in fact wired internet connection. 
Output of `sudo lshw -c network` is:

```
  *-network DISABLED
       description: Wireless interface
       product: Wireless-AC 9560 [Jefferson Peak]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 10
       serial: 04:d3:b0:0f:da:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-43-generic firmware=46.6bf1df06.0 9000-pu-b0-jf-b0- latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ed310000-ed313fff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@4:2.3
       logical name: enx00e04c680134
       serial: 00:e0:4c:68:01:34
       size: 100Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.11.11 duplex=full firmware=rtl8153a-4 v2 02/07/20 ip=192.168.1.35 link=yes multicast=yes port=MII speed=100Mbit/s
```

So the driver seems to be "r8152", right? 
When I do `dpkg-query --search r8152`, the output is:
```
linux-modules-extra-5.8.0-43-generic: /lib/modules/5.8.0-43-generic/kernel/drivers/net/usb/r8152.ko
```

> **TheFu said:**
> connect with wifi and install that package.  Once installed, you can do a  [/b]sudo modprobe[/b] to get it loaded into the kernel, then maybe  restart the networking subsystem (may not be necessary), and go into the  normal network manager applet to disable the wifi connection and toggle  the wired connection so that works.

If the above is correct, I now know that the package is "linux-modules-extra-5.8.0-43-generic", yes? But there were some more kernel updates after the install, so in my installed version, the kernel is not 5.**8**.0-43 any more, but 5.**11**.0-43-generic. I guess I would have to look for a package "linux-modules-extra-**5.11.0-43**-generic" ? On the other hand, it was the kernel updates that removed the wired connection, so maybe I should stick to the old module? (But mixing versions has kind of a bad feeling.) 
And when found, I am not quite sure how to "install that package". Some apt-command? Could you please explain?
And then what does "modprobe" do? (the man page does not tell a lot). If it does not work, how can I revert it? (the installing and the modprobing).

Sorry my asking a lot, but as it is kernel modification, I'll be rather sure about what I am going to do, in order not to mess things up. 
Thanks a lot for your help!

---

### Post by chili555 on 2022-01-06
If the wireless is working, then -extra is installed. Verify:

```
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```The real question is why r8152 doesn't load or, if it does, what errors or warnings appear.

```
lsmod | grep r8152
sudo modprobe -v r8152
sudo dmesg | grep r8152
```

---

### Post by EXAsoft on 2022-01-08
output of `sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status`:
```
Status: install ok installed
```

So extra is in fact installed... But what's going wrong?

Output of `lsmod | grep r8152`:
(nothing)

Output of `sudo modprobe -v r8152`:
```

insmod /lib/modules/5.11.0-44-generic/kernel/drivers/net/mii.ko 
insmod /lib/modules/5.11.0-44-generic/kernel/drivers/net/usb/r8152.ko 

```

Output of `sudo dmesg | grep r8152`:
```

[  226.777327] usbcore: registered new interface driver r8152

```

@chili555 - does that tell you something? What else could I check or do? Thanks a lot!

---

### Post by TheFu on 2022-01-08
Looks to me like the usb network driver is installed and loaded. Does it not work now?
Does it show up in the commands we've asked about previously? I.e. .... did you run those again?

---

### Post by EXAsoft on 2022-01-10
After reboot, the same (no wired ethernet). When I run the above three commands again (lsmod, modprobe, dmesg), same output as in the last post. If I then do `lsmod | grep r8152` again (without reboot), the output is
```

r8152                  81920  0
mii                    20480  1 r8152

```

But if I switch off the wireless, still no internet connection, i.e. wired ethernet still does not work.

Trying `sudo lshw -c network` still gives only the wireless connection:
```

  *-network DEAKTIVIERT
       Beschreibung: Kabellose Verbindung
       Produkt: Wireless-AC 9560 [Jefferson Peak]
       Hersteller: Intel Corporation
       Physische ID: 14.3
       Bus-Informationen: pci@0000:00:14.3
       Logischer Name: wlp0s20f3
       Version: 10
       Seriennummer: 04:d3:b0:0f:da:07
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=iwlwifi driverversion=5.11.0-44-generic firmware=46.4d093a30.0 9000-pu-b0-jf-b0- latency=0 link=no multicast=yes wireless=IEEE 802.11
       Ressourcen: irq:16 memory:ed310000-ed313fff

```

What else could I try? 
I attach complete output of dmesg, maybe it contains useful hints? Any other files / outputs that could be helpful?
[ATTACH]289782[/ATTACH]
Thanks a lot!

---

### Post by EXAsoft on 2022-01-10
An addition, don't know if it is related to the above problem: 
Played around with docker today: downloaded and installed Portainer and an echo server. Both containers are running (and wireless connection is on). But I cannot connect to any of the containers using http(s)://localhost:somePort (the request times out). ping localhost however works, responds from localhost (127.0.0.1) as expected.

---

