---
title: "Ethernet stops working"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by juveyfruit on 2007-11-25
I have Gutsy installed in my machine and have an Billion ADSL router.  All worked well until I decided to get my MEGA Sky tv usb tuner working.  

I did a ```
sudo chown -R user /lib
``` to copy over the megasky firmware into ```
/lib/firmware/2.6.22-14-generic
```, and copied over successfully.

My Mega Sky usb tuner loaded up successfully but my ethernet has stopped working.  It tries to assign itself an IP address and fails.  It recognises the address of the router 192.168.1.254 but it pauses on trying to acquire an IP address.

How do I begin fault finding my ethernet device?

---

### Post by mellowd on 2007-11-25
I assume its plugged into some sort of router, what happens if you reboot the router?

---

### Post by juveyfruit on 2007-11-25
I rebooted the router and still had the problem on my machine, which I shall name Ubuntu box #1

I can rule out that its a router hardware issue, as I've tested all ports with my second ubuntu box (Ubuntu box #2).

Also, I can vnc from my windows box to the second ubuntu box, through the router.

Furthermore, I've popped the Ubuntu live CD in and used on the ubuntu box #1.  I ran firefox and could access the ethernet and internet. 

Here are my current thoughts:

1) I think I've done something to the files located in /lib by using chown.

2) Last resort is to do some form of system restore, but i'd rather fix the problem and not waste bandwidth and time.

---

### Post by mellowd on 2007-11-25
can you post the output of this:

```
ifconfig
```

---

### Post by juveyfruit on 2007-11-25
These are the results from ifconfig:

eth0

Link encap:Ethernet HWaddr 00:1A:4D:2B:5D:2B
inet6 addr: fe80::21a4dff:fe2b:5d2b/64 Scope:Link
UP BROADCAS RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collissions:0 txquelen:1000
RX bytes:864 (864.0 b) TX bytes:1152 (1.1 KB)
Interrupt:20

lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 erorrs:0 dropped:0 overruns:0 frame:0
TX packets:4 erorrs:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX bytes:200 (200.0 b) TX bytes:200 (200.0 b)

---

### Post by juveyfruit on 2007-11-27
I have found a fix.

It seems that on startup Gutsy disables my ethernet device.  I can physically see this occur as the ethernet lights turn off when booting into Gutsy.

When booting into Windows the lights remain on, and the ethernet works.

I've read some posts re:network-manager.  There have been cases and also in my my machine where network-manager disables the ethernet device.

The fix is to remove network-manager and establish a network connection by using dhclient

```
sudo apt-get remove network-manager
sudo dhclient
```

Unfortunately, I do not know how to automagically turn on the ethernet as I manually enable it each time on startup using dhclient.

---

### Post by mellowd on 2007-11-27
It's odd that it would disable the device at bootup. Stil, a bug is a bug.

This link may be of some help: [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by juveyfruit on 2007-11-28
Actually, instead of using dhclient, i made sure that the following lines were present in /etc/network/interfaces

```
auto eth0
iface eth0 inet dhcp
```

My ethernet is enabled upon bootup.

---

