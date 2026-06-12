---
title: "Memor ease slide and film copier."
date: 2009-12-26
forum: New to Ubuntu
---

### Post by tsuchang on 2009-12-26
I received a new toy for Christmas.  One of these [http://www.pcmag.com/article2/0,2817,2340412,00.asp](http://www.pcmag.com/article2/0,2817,2340412,00.asp)
A Memor Ease 35mm slide and film converter.  
I installed the Adobe photoshop, direct x and the driver.
I have the unit plugged into a usb port but nothing works for me yet.
How do I set things up for the software to boot and let me play with my new toy?  I have tried the applications/wine/programs/cyberview rout but no joy.  I get flashes of windows opening and closing in the upper left of the screen then nothing.
I am using Ubuntu Jaunti.

---

### Post by cariboo on 2009-12-27
What is the output of dmesg when you plug your device in? TO check the output of dmesg, open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n15
```

and post the results in your next post.

---

### Post by 3rdalbum on 2009-12-27
What happens if you go to Applications > Graphics > XSane Image Scanner?

Windows drivers do not work in Wine, so you won't be able to scan directly into any Windows programs.

---

### Post by tsuchang on 2009-12-27
[   12.477871] type=1505 audit(1261932139.722:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2104
[   12.515091] type=1505 audit(1261932139.758:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2108
[   12.515161] type=1505 audit(1261932139.758:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2108
[   12.515194] type=1505 audit(1261932139.758:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2108
[   12.515226] type=1505 audit(1261932139.758:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2108
Caraboo.  this is the result.

[   12.618401] type=1505 audit(1261932139.862:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2113
[   12.618567] type=1505 audit(1261932139.862:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2113
[   12.640624] type=1505 audit(1261932139.886:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2117
[   16.521323] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.521326] Bluetooth: BNEP filters: protocol multicast
[   16.532506] Bridge firewalling registered
[   18.973017] ppdev0: registered pardevice
[   19.020187] ppdev0: unregistered pardevice
[   21.754321] forcedeth 0000:00:0f.0: irq 2299 for MSI/MSI-X
[   32.572007] eth0: no IPv6 routers present

---

### Post by tsuchang on 2009-12-27
3rdalbum
it says no devices available.

---

