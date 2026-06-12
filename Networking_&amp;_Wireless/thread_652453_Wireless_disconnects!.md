---
title: "Wireless disconnects!"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by franciscojhh on 2007-12-28
Hi,

I have some problems with my internet connection. After booting, it works fine, but after a while (sometimes 5 mins, sometimes 5 hours) it gets disconnected. The network controller is (via lspci -v):
```

        Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: Unknown device 1948:3c01
	Flags: bus master, slow devsel, latency 32, IRQ 5
	Memory at fb004000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2

```
It works in windows without problems.

The error in /var/log is:

a lot of :
```

     WEP decrypt failed (ICV)
     RX WEP frame, decrypt failed

```
and then:
```

     nm_print_open_socks(): Open Sockets List: 
     nm_print_open_socks(): Open Sockets List Done. 
     wlan0: disassociate(reason=3)
     wlan0: RX WEP frame with unknown keyidx 0 (A1=00:80:5a:27:2a:ce A2=00:01:24:f4:80:95 A3=00:30:bd:4b:39:f2)
     wlan0: RX WEP frame with unknown keyidx 0 (A1=00:80:5a:27:2a:ce A2=00:01:24:f4:80:95 A3=00:30:bd:4b:39:f2)

```

I'm running a Ubuntu Gutsy Gibbon 32 bits.

Thanks in advance.

---

### Post by empthollow on 2007-12-28
are you using network manager?  I have had disconnect issued with nm-applet in gnome.  It will randomly disconnect especially if the computer is idle for some reason.  i am able to reconnect if i :
```
killall nm-applet && nm-applet
```
i don't understand why this is and have not found anything googling.except some launchpad bug entries.  I'm not sure it that is the problem i am having or if it is the problem you are having.  for the most part it doesn't disconnect when i have working on the computer.  I know that this is a problem with nm-applet because i installed ubuntu server and configured wpa_supplicant manually and have never had a disconnect.

---

### Post by Digger78 on 2007-12-28
I had  (maybe) the same issue with my Asus usb adapter.

after installing ndiswrapper & using the windows XP driver (rt2500usb) and blacklisting the "alternate driver :  rt2570"

Not sure if your card uses the same "alternate driver"  but you could try installing ndiswrapper + the XP driver for your card.

then

```
ndiswrapper -l
```

will show you something like

```
digger@Digbuntu:~$ ndiswrapper -l
rt2500usb : driver installed
        device (0B05:1706) present (alternate driver: rt2570)

```

edit  /etc/modprobe.d/blacklist

adding the line

```
blacklist rt2570 [COLOR="Red"] (or whatever your alternate driver is)[/COLOR]
```

reboot & test

---

