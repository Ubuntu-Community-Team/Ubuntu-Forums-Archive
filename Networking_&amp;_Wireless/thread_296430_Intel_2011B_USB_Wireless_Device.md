---
title: "Intel 2011B USB Wireless Device"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by hiptahop on 2006-11-09
I have an Intel PRO/Wireless 2011B LAN USB Device that I can't get working.  

I first installed linux-wlan-ng, but the device still didn't work  Now, I'm trying NDISWrapper, but am still stuck.

Any suggestions?

jeremy

```
jeremy@BlueBox:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 8086:1111 Intel Corp. PRO/Wireless 2011B 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

```
jeremy@BlueBox:~$ ndiswrapper -l
Installed drivers:
wlanusb         driver installed, hardware present
```

```

jeremy@BlueBox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by wieman01 on 2006-11-09
What's the output of:
> lshw

---

### Post by hiptahop on 2006-11-09
Sorry there's so much, but I'm not sure how much to exclude.

```

        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: PRO/Wireless 2011B 802.11b Adapter
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.32
                   serial: 00245B002WG
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:f6010000-f60100ff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
```

```

        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 78
             serial: 00:e0:4c:ea:74:19
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=192.168.1.125 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:e800-e8ff iomemory:f6011000-f60110ff irq:185
```

```
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes
```

---

### Post by wieman01 on 2006-11-09
It says your wireless adapter is disabled:
> *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes
Is there a hardware switch of any kind or is the Ethernet cord plugged while you are trying to scan?

And when you install "ndiswrapper" did you blacklist the Linux driver ("prism" something...)?

---

### Post by hiptahop on 2006-11-10
There are no hardware switches, but the ethernet line was connected when I scanned with lshw.  I attempted to reboot and use the wireless device while otherwise unconnected to the network, with no change.  I didn't enter lshw in that state, but I did just now after unplugging the ethernet again with no change.

I've read several posts that mention blacklisting drivers, but none with much of an explanation.  I haven't blacklisted whatever might be conflicting with NDISWrapper (this is the problem blacklisting solves?).  And I'm not sure how.

Would I append the following to blacklist?
```

# conflicts with NDISWrapper
blacklist prism2_usb
```

Here are outputs from modules and blacklist:

```
jeremy@BlueBox:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
```
```

jeremy@BlueBox:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
```

---

### Post by hiptahop on 2006-11-10
Adding the linux driver to blacklist worked!  I realized too late though that kismet doesn't work with windows drivers, so I am going to try again to get the linux-wlan-ng driver to work.

I [read, under the section titled "supported devices"]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb"), that this driver is compatible with this specific device, but I have been unable to get it working properly.

Any suggestions?

---

### Post by wieman01 on 2006-11-10
I have checked the guide and it specifically mentions "ndiswrapper"... So Kismet is an issue? Where did you find that information? Have you tried scanning after blacklisting the Linux driver?

---

### Post by hiptahop on 2006-11-10
See kismet [readme]("http://www.kismetwireless.net/documentation.shtml").

> Chipsets known to NOT WORK:
...
ndiswrapper        - Anything using ndiswrapper is using WINDOWS drivers AND CAN NOT BE USED WITH KISMET.

Without a driver known to work with kismet, I can't configure the Capture Source in kismet.conf ([Section 12]("http://www.kismetwireless.net/documentation.shtml")).

---

