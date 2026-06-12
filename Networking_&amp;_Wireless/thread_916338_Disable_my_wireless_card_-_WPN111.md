---
title: "Disable my wireless card - WPN111"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by itsjareds on 2008-09-10
I have read other threads about this but I still can not get it to work. I'm using a Netgear WPN111 USB adapter, which works fine (with a few bugs..) except I can't get my card to turn off completely when I restart my computer. The blue LED doesn't turn off and keeps blinking, so that means it's still working. The only way I can get the card to turn off is to manually unplug/replug it back in.

It'd be nice to not have to worry about remembering to unplug it. If I forget, then my internet doesn't work and I have to restart. I'm dual-booting Ubuntu and WinXP, and when I restart XP the card turns off fine. Is this because of some "hardware switch" that I've read about in other threads? Would it be possible to use this same switch in Ubuntu.. hopefully through a terminal?

I've also done some research through NDISwrapper's troubleshooting docs, but since I'm a real newbie at code editing in Linux I don't really know what I'm looking for. I tried restarting ndiswrapper with

```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```

But after I did rmmod ndiswrapper the light was still blinking. So in essence, that simulated my computer turning off and then booting up Ubuntu again.

---

### Post by itsjareds on 2008-09-10
bump

---

### Post by Crafty Kisses on 2008-09-10
There are pretty much 4 options.


Turn off the hardware (Need to search or consult manual for key-combination), Then remove the interface from
```
/etc/network/interfaces
```
Blacklist the driver in ```
/etc/modprobe.d/blacklist
```
Physically remove the kernel module ```
sudo modprobe -r ****
```


If you cant do #1, then I would probably do #3. You can also do the following to get the name of the driver: ```
lshw -C network
```

---

### Post by itsjareds on 2008-09-11
I saw that exact post on another thread ;)

None of them helped.. the LED was still blinking when I removed the module.

Edit: lshw -C network gave me this:

```

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:59:31:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpn11 driverversion=1.53+NETGEAR,09/26/2005,1.5.0.21 ip=192.168.0.127 multicast=yes wireless=IEEE 802.11g

```

So my driver is ndiswrapper+netwpn11? When I did sudo rmmod ndiswrapper+netwpn11 it gave me a not found error, and the same with netwpn11. I could disable ndiswrapper though.

---

### Post by itsjareds on 2008-09-12
..bump

---

