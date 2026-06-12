---
title: "My wireless card changes its name on each restart. (wlan1 to wlan2, to wlan3 and so)"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Ubempi on 2008-02-20
Well my problem is that each time my computer starts Ubuntu will change the wireless card name (commonly wlan<NUMBER>) to something else. So far I've had the names wlan2, wlan3 and now it is wlan4. I don't know what is happening.

I've been reading a little and this: [http://ubuntuforums.org/showthread.php?t=212687](http://ubuntuforums.org/showthread.php?t=212687)
seems like my problem but I have no iftab in my /etc/

I have:
Ubuntu 7.10 (just installed)
I uninstalled "network manager" (because couldn't connect to internet)
I installed Wicd ( :) )

It seems that Network Manager does not cares about the changing name, in the other hand Wicd will get lost on each restart and I must tell it the new name each time.
To find out the new name I go: System > Administration > Network > MyWireless > Properties > and the name appears in the title of the window.

Some ideas?? Wich additional information should I post here?

Thanks

---

### Post by The Cog on 2008-02-20
Does the MAC address change each time (in ifconfig)?
Does looking at the file /etc/udev/rules.d/70-persistent-net.rules help?

---

### Post by Ubempi on 2008-02-20
> **The Cog said:**
> Does the MAC address change each time (in ifconfig)?
Does looking at the file /etc/udev/rules.d/70-persistent-net.rules help?

First boot: card name: wlan4
>>>>>>>>>>>ifconfig: Here, to my surprise, the wireless card is not listed, I also noted it appears disabled in the Network dialog (although I configured it with Wicd and works fine)
```
eth0      Link encap:Ethernet  HWaddr 00:no:ts:ho:wn:NN
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fern::xxx:xxfx:xexx:exxx/6x Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:9343 (9.1 KB)
          Interrupt:18 Base address:0xd800 

lo        Link encap:Bucle local
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:5032 (4.9 KB)  TX bytes:5032 (4.9 KB)
```

>>>>>>>>>>>/etc/udev/rules.d/70-persistent-net.rules: Now this seems like trouble, I don't understand this list. Changed the ATTRS{address} values, I'm not sure but, I'm afraid it is a security risk. Or not? Still, those chunks that are the same here, are the same in my configuration file, i.e. all the "7x" are the same numbers in my file)
```
# PCI device 0x1106:0x3065 (via-rhine)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:no:ts:ho:wn:NN", NAME="eth0"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:ex:px:5x:9x:7x", ATTRS{type}=="1", NAME="wlan0"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:ex:px:5x:8x:7x", ATTRS{type}=="1", NAME="wlan1"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:ex:ex:qx:ax:7x", ATTRS{type}=="1", NAME="wlan2"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:ex:3x:fx:8x:7x", ATTRS{type}=="1", NAME="wlan3"

# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:ex:px:5x:ax:7x", ATTRS{type}=="1", NAME="wlan4"
```

---

### Post by Ubempi on 2008-02-20
Some more info of the.

____________
2nd Boot-up: Card name: wlan4 (Internet works, no Wicd configuration needed)

>>>>>>>>>>>>>>>ifconfig: Now wlan4 appears in the list.
```
eth0      Link encap:Ethernet  HWaddr 00:no:ts:ho:wn:NN  
          inet6 addr: fern::xxx:xxfx:xexx:exxx/6x Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5740 (5.6 KB)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:5032 (4.9 KB)  TX bytes:5032 (4.9 KB)

wlan4     Link encap:Ethernet  HWaddr 00:ex:px:5x:ax:7x  
          inet addr:192.168.200.10  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe5e:1a17/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:1494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:168012 (164.0 KB)  TX bytes:14508 (14.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-ex-px-5x-ax-7x-00-00-00-00-00-00-00-00-00-00  
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

>>>>>>>>>>>>>>>>>70-persistent-net.rules: No change.



____________
3rd boot-up: Card name: wlan5 (Internet does not work, Wicd is configured for wlan4)

>>>>>>>>>>>>>>>ifconfig: equal to first boot.

>>>>>>>>>>>>>>>70-persistent-net.rules: just like the first boot with one more block at the end, this:
```
# PCI device 0x1814:0x0201 (rt2500pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:b3:px:5x:3b:7x", ATTRS{type}=="1", NAME="wlan5"
```

:confused:

---

### Post by The Cog on 2008-02-20
Aaaaaargh!!!

I really don't know what's going on there, but it isn't good. All the MAC addresses contain non-hex digits. It's not just the wireless card - even eth0 is showing both an invalid MAC address and an invalid IPv6 address. x, r, n, t, h, w are not valid hexadecimal digits.

I might be tempted to reinstall on the theory that something somewhere is horribly horribly corrupted. I've never seen anything like it.

---

### Post by ModelM on 2008-02-20
In /etc/udev/rules.d/[whatever number]-persistent-net-rules, at the top you should see a couple of entries, the original ones for ethernet & wireless. Here's this file from my system...

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"


# PCI device 0x168c:0x001c (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1c:26:71:67:8b", ATTRS{type}=="1", NAME="wlan0"

```

Look at the second entry here (the ndiswrapper one) this is the "out of the box" format. You need to change both device entries in your file (after backing it up, of course)  to look like the first entry in my file. Notice I've specified the driver name for the device and removed the address attribute completely.

The original format of the line says, "The device with MAC address XXX, using any driver, should be called eth0".

The new format of the line says, "The first device you find using the forcedeth driver should be called eth0".

Notice that we have removed the MAC address completly, and specified the driver name instead of saying "any driver".

You'll need to modify the first two entries in the file, one for wireless & one for ethernet, then delete all entries below these two.

Your drivers are, for whatever reason, reading/returning bogus MAC addresses which change each boot. A new MAC address, bogus or not, generates a new entry (eth0, eth1, eth2, etc). This will prevent this from happening, but it won't fix the root of the problem which is somewhere else.

---

### Post by Ubempi on 2008-02-20
> **The Cog said:**
> Aaaaaargh!!!...All the MAC addresses contain non-hex digits...

I don't know if it is safe to show the mac address on the Internet. So I decided to code the chunks on the string, putting :fx: where it says :09: and so. That's why you see non-hex values.
I don't know if it is a stupid thing to or not. I already said that on my second post, although my english is not the best, I may have not been clear.

> **ModelM said:**
> ...You need to change both device entries in your file (after backing it up, of course) to look like the first entry in my file...

OK, I did that, now I will be booting several times to see what happens, then I'll come back to tell how it goes.

Thanks a lot for sharing your knowledge.

---

### Post by Ubempi on 2008-02-20
> **Ubempi said:**
> .. I will be booting several times to see what happens, then I'll come back to tell how it goes...

Works flawless! I'm happy :)

Thanks.

---

