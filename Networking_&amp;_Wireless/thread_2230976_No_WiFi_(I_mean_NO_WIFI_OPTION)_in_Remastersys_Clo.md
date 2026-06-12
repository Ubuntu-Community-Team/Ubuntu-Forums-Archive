---
title: "No WiFi (I mean NO WIFI OPTION) in Remastersys Clone"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by xmbwd on 2014-06-22
Hi all.  I finally figured out how to install the deprecated Remastersys and get it working so it creates a bootable .iso.  I made a live USB stick with the .iso using Unetbootin.  But when I boot into the live USB, I have no WiFi (I should note that, obviously, the WiFi works normally on the system that I copied using Remastersys).  And when I say no WiFi, I mean it doesn't even show up as an option in the top menu under networking. 

I assume this has to do with the wireless card drivers and/or the kernel.  Here is some information that may help.  

I have an Intel® Wireless 7260 card.
I went [here]("http://wireless.kernel.org/en/users/Drivers/iwlwifi") and installed the proper iwlwifi firmware -- then restarted (my live USB has a persistent partition).

**iwconfig**
```
eth0      no wireless extensions.

lo        no wireless extensions.

```

**ipconfig** [*Note:  before I installed the iwlwifi firmware, this said no eth0 or lo*]
```
eth0      Link encap:Ethernet  HWaddr bc:ee:7b:03:61:47  
          inet addr:10.0.1.33  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beee:7bff:fe03:6147/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4895971 (4.8 MB)  TX bytes:473374 (473.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81327 (81.3 KB)  TX bytes:81327 (81.3 KB)

```

**sudo lshw -C network**
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: bc:ee:7b:03:61:47
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.1.33 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:60 ioport:e000(size=256) memory:f7d00000-f7d00fff memory:f0000000-f0003fff
  ***-network UNCLAIMED**
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c01fff

```

I feel like I'm one step away, but if anyone could help me out that would be awsome.

I'd like to:[INDENT] (a) get it working on this install, and also 
(b) figure out how to get remastersys to create an .iso with the right drivers.
[/INDENT]
 
Thanks!

---

### Post by xmbwd on 2014-06-25
Ok, so I guess this is not a common problem.  If you remove the Remasterys part of the equation -- that is, if you just focus on the WiFi capability being completely absent from the UI -- does anyone know of a solution?  I have had wireless problems before, but I've never had the WiFi not be an option (i.e., can't even chose "Enable Wi-Fi").

Any help would be great.  Thanks.

---

### Post by xmbwd on 2014-06-29
Not sure this is of interest to anyone, given the rousing response that I received.  But I figured out the problem, and it had nothing to do with Remastersys or the WiFi settings.  

The issue was with Unetbootin.  I don't know exactly what it does to create a bootable USB from your custom .iso (created -- perfectly -- in Remastersys), but it messes with something. As a result, using a USB created by Unetbootin, neither persistence nor WiFi work on a custom .iso.  However, WiFi does work on a stock Ubuntu downloaded .iso (again, using Unetbootin) -- hence the reason I thought it might be Remastersys. 

In all events, this thread is closed and solved. I switched to Multisystem to create the bootable USB, and all is well.  If you want to use MultiSystem instead of Unetbootin, it is [here]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/").   Also, there are a few tutorials on how to use it [here]("http://community.linuxmint.com/tutorial/view/1219") and [here]("http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce/Create-a-Multi-boot-USB-Stick-with-MultiSystem").

Quick and dirty instructions below.  


[LIST]
[*]Download and install install script (liveusb.info/multisystem/install-depot-multisystem.sh.tar.bz2) 
[*]Extract the install-depot-multiboot.sh Script to your Desktop 
[*]In terminal CD to Desktop and: /.install-depot-multiboot.sh
[/LIST]

    TO USE:

[LIST]
[*]    Insert a USB Drive 
[*]    Launch the Script via Applications > Accessories > MultiBoot 
[*]    Select your USB Device from the list and click Validate 
[*]    Now simply Drag and Drop an ISO into the Window to add the Distribution 
[*]    Click the button to the left to get more options:  add persistence 
[*]    Once finished, restart your PC, set your boot menu to boot from the USB device, Select the Distro you want to Boot and enjoy! 
[/LIST]

---

