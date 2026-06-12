---
title: "Wireless Detected just not working"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by dustin0 on 2008-04-12
Everything but my wireless card works with ubuntu. The system detects the wireless card but will not connect to a network. This card does work in windows.

lshw -C network
```
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
```

ndiswrapper -l
```
dustin@laptop:~/Desktop/sp38764$ sudo ndiswrapper -l
[sudo] password for dustin: 
bcmwl6 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
dustin@tuh2-laptop:~/Desktop/sp38764$ 

```
sudo iwlist scanning
```
dustin@tuh2-laptop:~/Desktop/sp38764$ 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

dustin@tuh2-laptop:~/Desktop/sp38764$ 
```

---

### Post by prshah on 2008-04-12
> **dustin0 said:**
> detects the wireless card but will not connect to a network. This card does work in windows.

lshw -C network
Code:
       configuration: driver=b43-pci-bridge latency=0[color=red] module=ssb[/color]

ndiswrapper -l
```
dustin@tuh2-laptop:~/Desktop/sp38764$ sudo ndiswrapper -l

[sudo] password for dustin: 
bcmwl6 : driver installed
	device (14E4:4311) present [color=red](alternate driver: ssb)[/color]

dustin@tuh2-laptop:~/Desktop/sp38764$ 
```

Nope your card is _not_ detected. You have configured the ndiswrapper driver but not loaded it. You are still using the _alternate_ suggested driver.

Try this:
```

sudo rmmod ssb
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwconfig

```

That should clear it up. If it does, post here for a permanent solution (this will last only till your next reboot). If it doesn't post here for an alternate suggestion;

in either case, post here :)

---

### Post by dustin0 on 2008-04-12
No Solution but the output is

dustin@tuh2-laptop:~/Desktop/sp38764$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dustin@tuh2-laptop:~/Desktop/sp38764$

---

### Post by dustin0 on 2008-04-13
bump

---

### Post by oarion7 on 2008-04-13
bump bump

(me too same problem)

although mine says "(alternate driver: bcm43xx)" instead of "(alternate driver: ssb)" so i used "sudo rmmod bcm43xx" and it told me "ERROR: Module bcm43xx does not exist in /proc/modules"

But anyway, same issue same outcome I believe. Any help? Much appreciated.

---

