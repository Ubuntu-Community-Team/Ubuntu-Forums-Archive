---
title: "wireless problems"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by vixinu on 2008-03-24
Hi, I recently upgraded to Ubuntu 8.04 beta.  I have a Broadcom 4318 wireless chip.  I have the firmware installed and everything, but when I go into Network Manager I only have wired connection options, no wireless, like this:
[ATTACH]63693[/ATTACH]
also, I have a strange output for ```
lshw -C network
``````


IDE                       
  *-network        
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=16 module=ssb
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 80
       serial: 00:11:24:43:36:74
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=sungem driverversion=0.98 ip=192.168.1.70 latency=16 maxlatency=64 mingnt=64 module=sungem multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0_rename
       serial: 00:11:24:c5:a9:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

My computer recognizes my router and all (wifi-finder) but I can not uses it.
Please help.
Thanks,
Josh

---

### Post by Eiríkr on 2008-03-25
Network Manager is known to have very limited functionality, and apparently causes all kinds of trouble if you have both wired and wireless on the same machine.  Many threads I've read here on the forum strongly recommend replacing Network Manager with WICD, which unfortunately is not included in the Ubuntu repositories, and must therefore be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").

Hope this works for you,

Eiríkr

---

### Post by Paris Heng on 2008-03-25
Yes try WICD, you will know what is the different between WICD and the MN. Cheers~

---

### Post by vixinu on 2008-03-25
Thanks, but I am having problems installing wicd.  When I try to install it, it never will start up.

---

### Post by imdano on 2008-03-25
Could you go into more detal about the problem you're having?  After you install, what happens when you run /opt/wicd/tray.py from a console?

---

### Post by vixinu on 2008-03-25
never mind, it works.

Thank you all!

---

### Post by vixinu on 2008-03-25
Well, not quite... It only worked once.  Here is what I get:
```
ERROR:dbus.proxies:Introspect error on :1.103:/org/wicd/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/opt/wicd/tray.py", line 7, in <module>
    import edgy
  File "/opt/wicd/edgy.py", line 363, in <module>
    tr=TrackerStatusIcon()
  File "/opt/wicd/edgy.py", line 323, in __init__
    wireless.SetForcedDisconnect(False)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, 
```](*,)

---

### Post by imdano on 2008-03-25
Try running
```
sudo /etc/init.d/wicd start
```Then start the tray again.  If it still doesn't work, try going into /opt/wicd/data and deleting all the .conf files that are there, then repeat the last two steps.

---

