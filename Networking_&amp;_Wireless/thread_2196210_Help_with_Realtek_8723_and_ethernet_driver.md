---
title: "Help with Realtek 8723 and ethernet driver"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by dustinmarc on 2013-12-28
I believe I have made the mistake of following too many seperate instructions and now I am utterly confused.  To begin with I installed 12.04, and quickly realized that no network connections were available, despite the fact that this laptop has ethernet and wireless.  So I went online and found a set of instructions at [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) to make the ethernet work.  I was able to follow those instructions, and the ethernet works perfect.  Next up was the wireless.  After following instructions at [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized) the last line - sudo modprobe rtl8723e
says that is an anvalid argument.  I am able to see both my Realtek 8723 and the Qualcomm Gigabit Ethernet in the "Additional Drivers" thing that comes with linux, but the wireless will not work at all.  The driver says that it is activated but not currently in use.  I am sure what I did was install two drivers for the same thing, and confused the OS (not as confused as I am though, lol) but I don't know where to go from here.  Any help would be greatly appreciated.

Edit - I should also note that I installed the 64bit O.S. and I don't even know if those drivers were meant for that, but they seemed to build okay.
Edit2 - output of 
```
sudo lshw -businfo
```
```
 *-network               
       description: Ethernet interface
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 8c:89:a5:0e:4e:ed
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx ip=192.168.0.10 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:f7900000-f793ffff ioport:d000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: RTL8723AE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:c000(size=256) memory:f7800000-f7803fff

```

---

### Post by dustinmarc on 2013-12-28
As I expected, I had two drivers trying to be used at the same time.  I fixed this by going into the compat_src folder and typing ```
sudo make wlunload
``` which unloads all wireless drivers from compat (which is what got the ethernet working), and then going back into the rtl folder and re-making and installing their driver.  sudo modprobe rtl8723e worked perfectly after that.

---

