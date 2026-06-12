---
title: "Configuring WiFi USB Belkin F7D4101"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Cuco3 on 2010-08-05
I have a USB Belkin [F7D4101]("http://www.google.com/url?q=http://www.belkin.com/IWCatProductPage.process%3FProduct_Id%3D509866&sa=X&ei=ACtbTIKOBIO78gbm55HrAg&ved=0CC0QzgQoATAA&usg=AFQjCNGqIInntI6f5J3nDwq98LjEXkSEHA") Play Wireless adapter and a WiFi adapter built in the motherboard of my laptop.

When I go to hardware drivers, I see nothing for the Belkin device.

The built-in WiFi is working, but the Belkin doesn't appear when I type "sudo iwconfig," only the built-in adapater.

Any advice? I can't seem to find drivers or anything on Google, so I started a thread.

---

### Post by Cuco3 on 2010-08-06
Anyone?

---

### Post by lkraemer on 2010-08-08
Open a Terminal Window:
Copy & paste to prevent errors.......
```

lsusb
lshw -C network
dmesg tail

```

lk

---

### Post by doppelgangerx4 on 2010-09-13
I have the same problem with the same model wireless adapter.
```

$ lsusb
Bus 002 Device 005: ID 050d:615a Belkin Components 
Bus 002 Device 004: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:26:18:fd:5b:77
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:34 ioport:b800(size=256) memory:cffff000-cfffffff(prefetchable) memory:cfff8000-cfffbfff(prefetchable) memory:fbbf0000-fbbfffff(prefetchable)

$ dmesg | tail -n 30
[   30.183420]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   30.183433] CPU3 attaching sched-domain:
[   30.183436]  domain 0: span 3,7 level SIBLING
[   30.183439]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[   30.183447]   domain 1: span 0-7 level MC
[   30.183451]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   30.183464] CPU4 attaching sched-domain:
[   30.183467]  domain 0: span 0,4 level SIBLING
[   30.183470]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[   30.183478]   domain 1: span 0-7 level MC
[   30.183481]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   30.183495] CPU5 attaching sched-domain:
[   30.183498]  domain 0: span 1,5 level SIBLING
[   30.183501]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[   30.183509]   domain 1: span 0-7 level MC
[   30.183512]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   30.183525] CPU6 attaching sched-domain:
[   30.183528]  domain 0: span 2,6 level SIBLING
[   30.183532]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[   30.183540]   domain 1: span 0-7 level MC
[   30.183543]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   30.183556] CPU7 attaching sched-domain:
[   30.183559]  domain 0: span 3,7 level SIBLING
[   30.183563]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[   30.183570]   domain 1: span 0-7 level MC
[   30.183574]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   52.063545] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   89.914983] usb 2-1.2: USB disconnect, address 3
[  151.712470] usb 2-1.8: new high speed USB device using ehci_hcd and address 5
[  151.807294] usb 2-1.8: configuration #1 chosen from 1 choice

```

(Last bit is probably from when I removed the device just now to see what the model was. Plugged it back in immediately afterward.)

---

### Post by imatworkallday on 2010-10-04
So here is what I did to make it work:P

1) (Not sure if this actually contributed to the success or not) I went into the package manager and did a search for "broadcom". I marked "bcmwl-modaliases" for removal (not complete removal) and marked "broadcom-sta-common" and "-source" for installiation.  Applied the changed and restarted.

2) Went to the Belkin support site and downloaded the install package. Installed it using WINE.  The installiation failed but the files were copied.

3)Went to ndisgtk (I think, it's under Windows Wireless Drivers under System->Administration) and directed it to home/YOUR USERNAME/.wine/dosdevices/c:/Program Files/Belkin/F7D4101/V1/xp/bcmwlhigh5.inf. Clicked open, install, and it showed available networks.

4) restarted.

I really hope this helps! I hope I didn't leave anything out. Good luck!

I also did this on 10.10 beta.

---

### Post by lammypie on 2010-10-11
Apologies but I am a newbie to ubuntu and can't seem to get my F7D4101 to work with my F7D4401 modem router which is running WPA/WPA2 however I can get it to work with the router when no security is enabled on wireless. Does anyone have any idea to resolve?
 
Thanks

---

