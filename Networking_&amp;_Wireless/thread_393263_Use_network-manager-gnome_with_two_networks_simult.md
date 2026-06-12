---
title: "Use network-manager-gnome with two networks simultaneously?"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by stuporglue on 2007-03-25
Is it possible to be connected to two networks at the same time with the network manager applet?  If I don't use nm-applet, I can set this up manually, and it works, but it'd be nice to have the wireless chooser in the task bar. 

I have a wireless connection which works great, and which I use for general internet use. I also have a wired connection on a static IP address which just hooks into another computer for fast file transfer and use with Synergy2. 

The NetworkManager Wiki page says this: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

> The computer should use the wired network connection when its plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection.

...which isn't the desired behavior. 

Any way to stay connected to both all the time?

---

### Post by spd106 on 2007-03-25
Yes, Network Manager will ignore any interface defined in the /etc/network/interfaces file. So I suggest that you add the static wired interface there. 

NB This may cause problems if you define a gateway. So it's usually best to leave that bit out and configure it manually.

---

### Post by tuxinvader on 2007-03-25
some time between edgy and feisty the Ubuntu team was taken over by a bunch of mentals! The lunatics are now in charge! How can they think a network manager that only allows you one active interface is acceptable. If this isn't fixed before release I'm going back to the mother land. Debian here I come.

Up until now I've been impressed with all the excellent improvements Ubuntu has contributed to the Linux desktop. But this is Madness!!

---

### Post by tuxinvader on 2007-03-25
Just raised a bug in launchpad about this:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/96103](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/96103)

---

### Post by stuporglue on 2007-03-25
> **spd106 said:**
> Yes, Network Manager will ignore any interface defined in the /etc/network/interfaces file. So I suggest that you add the static wired interface there. 

NB This may cause problems if you define a gateway. So it's usually best to leave that bit out and configure it manually.

Interesting...I actually have both defined in /etc/network/interfaces, and Network Manager would still let me switch between them. 

I'll comment out the wireless one and see what happens. 

[QUOTE=tuxinvader]some time between edgy and feisty the Ubuntu team was taken over by a bunch of mentals! The lunatics are now in charge! How can they think a network manager that only allows you one active interface is acceptable. If this isn't fixed before release I'm going back to the mother land. Debian here I come.[/QUOTE]

That's not exactly the case. It only occurs if you use the network manager GUI. If you use the standard Gnome GUI, it works fine, and if you use the command line (ie. manually edit /etc/network/interfaces) it works fine. So, if you're a Debian user, you should probably be used to the command line way anyways. It just happens that this is my wife's computer, and so I'd rather give her the nice friendly GUI experience instead of driving her back to Windows -- she's already been an awfully good sport about the whole thing.

---

### Post by stuporglue on 2007-03-25
[QUOTE=stuporglue]Interesting...I actually have both defined in /etc/network/interfaces, and Network Manager would still let me switch between them.

I'll comment out the wireless one and see what happens.[/QUOTE]

No good. It still shows both interfaces in the network manager, and only lets me choose one of them. 

Here's my /etc/network/interfaces file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.0.0.0

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid linksys
```

And just for fun, here's the output of ifconfig on wired:

```
eth0      Link encap:Ethernet  HWaddr 00:19:21:B8:D7:3D  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::219:21ff:feb8:d73d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5781 (5.6 KiB)  TX bytes:24685 (24.1 KiB)
          Interrupt:22 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41597 (40.6 KiB)  TX bytes:41597 (40.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:E7:0D:2C:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:897 errors:0 dropped:8 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:636364 (621.4 KiB)  TX bytes:135095 (131.9 KiB)
          Interrupt:23 Memory:ff5e0000-ff5f0000 
```

....and wireless....

```
eth0      Link encap:Ethernet  HWaddr 00:19:21:B8:D7:3D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5922 (5.7 KiB)  TX bytes:24685 (24.1 KiB)
          Interrupt:22 Base address:0x8800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42287 (41.2 KiB)  TX bytes:42287 (41.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:E7:0D:2C:8B  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe0d:2c8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:955 errors:0 dropped:8 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:638610 (623.6 KiB)  TX bytes:143014 (139.6 KiB)
          Interrupt:23 Memory:ff5e0000-ff5f0000 
```

Note that in wired, wlan0 has no IP and in wireless eth0 has no IP. I did a full reboot to make sure everything that needed to re-read the interfaces file. 

Any ideas?

---

### Post by Mr. C. on 2007-03-25
Please see my post and explanation, starting with post #15, here:

[http://www.ubuntuforums.org/showthread.php?t=387319&page=2](http://www.ubuntuforums.org/showthread.php?t=387319&page=2)

MrC

---

### Post by stuporglue on 2007-03-25
Well, the good news is that a fix is coming for NetworkManager v .7 (hopefully). The bad news is that it's not here now. :-)

See [http://live.gnome.org/NetworkManagerToDo](http://live.gnome.org/NetworkManagerToDo) "Multiple Active Devices". 

I'll just hard code it in /etc/network/interfaces for now, and disable nm-applet. 

Thanks!

---

### Post by tuxinvader on 2007-03-26
> **stuporglue said:**
> 
That's not exactly the case. It only occurs if you use the network manager GUI. If you use the standard Gnome GUI, it works fine, and if you use the command line (ie. manually edit /etc/network/interfaces) it works fine.

No it doesn't. I configured my interfaces in the interfaces file ( I usually do because it's quicker ), but the network manager daemon is started at some point in the boot process. It's not the GUI, but a daemon that controls the nic. If you log on to a console you will see that one of your nics is down, even if you have them both set to auto in the interfaces file. So I can't just switch off the applet.

It would seem the NetworkManager daemon is started by the D-Bus system:
```
/etc/dbus-1/event.d/26NetworkManagerDispatcher
/etc/dbus-1/event.d/25NetworkManager

```

Just add an exit near the top of that file and it should stop NetworkManager from hijacking the interfaces. If Ubuntu hadn't been taken over by a bunch of crazies, this would not be necessary ;-p 

All joking aside, I still think Ubuntu is a fantastic OS and I just hope they can put in a fix for this before Feisty is released.

---

