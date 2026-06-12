---
title: "ndiswrapper doesn't work after delete  -&gt; reinstall driver"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by palomar on 2008-07-26
Hi,
The first time I installed a windows driver in the Ndiswrapper gnome GUI it was detected correctly and in gnome networkmanager I could see some wireless networks. I could not get connection, so I uninstalled the windows driver in the ndiwrapper GUI and tried to 'modprobe acx' (that's my wifi chipset). Again I could see networks, but still doesn't work.

After reboot I tried installing a windows driver again the same way and it's recognized correctly ('Hardware present'), but in Gnome network manager there is no reference anymore to any wireless networks. There is only a wired network..

ndiswrapper -l tells me: tiaclxn: driver installed
modprobe ndiswrapper: no errors (no messages at all)
iwconfig gives only lo and eth2, both no wireless extenions.
ifconfig: also only lo and eth2.

So how do I enable wireless again with ndiswrapper? Seems like ndiswrapper works well, so maybe something else is 'hiding' it...

---

### Post by caljohnsmith on 2008-07-26
You might need to blacklist a module that Ubuntu is currently trying to use for your wireless card, so you can make sure Ubuntu uses ndiswrapper instead. What is your wireless card's chipset? And how about posting the output of:
```
sudo lshw -C network
```

---

### Post by Ayuthia on 2008-07-26
> **palomar said:**
> Hi,
The first time I installed a windows driver in the Ndiswrapper gnome GUI it was detected correctly and in gnome networkmanager I could see some wireless networks. I could not get connection, so I uninstalled the windows driver in the ndiwrapper GUI and tried to 'modprobe acx' (that's my wifi chipset). Again I could see networks, but still doesn't work.

After reboot I tried installing a windows driver again the same way and it's recognized correctly ('Hardware present'), but in Gnome network manager there is no reference anymore to any wireless networks. There is only a wired network..

ndiswrapper -l tells me: tiaclxn: driver installed
modprobe ndiswrapper: no errors (no messages at all)
iwconfig gives only lo and eth2, both no wireless extenions.
ifconfig: also only lo and eth2.

So how do I enable wireless again with ndiswrapper? Seems like ndiswrapper works well, so maybe something else is 'hiding' it...

Since ndiswrapper -l did not provide "device present", it usually means that there is something wrong with the driver.  When you do "modprobe ndiswrapper", can you check dmesg and see if there are any error messages out there for ndiswrapper?

---

### Post by palomar on 2008-07-26
> **caljohnsmith said:**
> You might need to blacklist a module that Ubuntu is currently trying to use for your wireless card, so you can make sure Ubuntu uses ndiswrapper instead. What is your wireless card's chipset? And how about posting the output of:
```
sudo lshw -C network
```

I have to type it over from the laptop screen since it has no internet connection ;) It says:

```

*-network: 0 UNCLAIMED
description: network controller
product: ACX 100 22Mbps Wireless Interface
vendor: Texas Instruments
physical id: a
bus info: pci@0000:00:0a.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=32
*-network:1
(info about my wired network card).....

```

Seems like there is a driver loaded for this wlan card. How do I disable it to use ndiswrapper??


> Since ndiswrapper -l did not provide "device present", it usually means that there is something wrong with the driver. When you do "modprobe ndiswrapper", can you check dmesg and see if there are any error messages out there for ndiswrapper?
i'm sorry for being incomplete, but it does say 'device present':

```
ndiswrapper -l
tiacxln: driver installed
    device (104C:8400) present (alternate driver: acx)

```

---

### Post by caljohnsmith on 2008-07-26
You can only use one driver at a time for your ACX100 chipset; to use ndiswrapper, you should remove the "acx" module:
```
sudo modprobe -r acx
```
Then see if ndiswrapper is working OK with your wireless card by scanning for available networks:
```
sudo iwlist <interface> scan
```
You can use iwconfig to find the name of your interface (usually wlan0, eth1, etc). If scanning for networks returns an error, then you might have to remove and then reinstall the ndiswrapper module just to get things working:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
And then try scanning for networks again. Let me know how that goes. :)

---

### Post by palomar on 2008-07-26
**[edit] Have not yet read the reply above. WIll try that first.**

Ok, tested again some stuff... when removing ndiswrapper module (modprobe -r ndiswrapper) and inserting it again (modprobe ndiswrapper) I get some errors in syslog and messages:

```

loadndisdriver: loadndisdriver: load_driver(330): too many .bin files for driver tiacxln
loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver tiacxln

```
But it also says loaded and registered (can't easily copy paste all that stuff right now).

---

### Post by palomar on 2008-07-26
> **caljohnsmith said:**
> You can only use one driver at a time for your ACX100 chipset; to use ndiswrapper, you should remove the "acx" module:
```
sudo modprobe -r acx
```

When executing I see no errors, so I think it's unloaded successfully. But when running lshw -C network I still see the ACX 100 22Mbps Wireless interface as mentioned in my previous post.

> 
Then see if ndiswrapper is working OK with your wireless card by scanning for available networks:
```
sudo iwlist <interface> scan
```
You can use iwconfig to find the name of your interface (usually wlan0, eth1, etc). If scanning for networks returns an error, then you might have to remove and then reinstall the ndiswrapper module just to get things working:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
And then try scanning for networks again. Let me know how that goes. :)
modprobe ndiswrapper (uninstalling/reinstalling) goes without error messages, but iwconfig does not give me any wireless network interfaces. Only lo and eth2.
I think the problem maybe has to do with that errors "too many .bin files etc." as mentioned in my last post.

---

### Post by palomar on 2008-07-26
Ok, progress now :) The windows driver contains 5 .bin files. Regarding to the syslog there are too many .bin files, so I deleted some bin files untill there was no error in the syslog. I needed to delete one file (the smallest).
It doesn't work yet, but now I can see some networks in gnome network manager.

---

