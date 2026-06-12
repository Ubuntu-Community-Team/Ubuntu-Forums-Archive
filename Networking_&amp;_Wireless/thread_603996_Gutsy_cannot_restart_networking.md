---
title: "Gutsy cannot restart networking"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by scottmuz on 2007-11-05
I was having issues with my DSL modem and DHCP and wanted 
to be able to restart my networking on gutsy but I get:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                            Ignoring unknown interface eth0=eth0.   
                 [OK]
And the restart seems to have had no affect or
not happened at all. 

I've always used this in the past fine when my modem 
has gone screwy.

But it no longer seems to have any affect.

Even if my network is up and I do 
sudo /etc/init.d/networking stop 
I can still ping things outside my PC (and I only have
one eth interface eth0)

How can I restart my networking?

---

### Post by Jussi Kukkonen on 2007-11-05
I assume you are using NetworkManager? you can start/stop/restart it like this:
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

---

### Post by scottmuz on 2007-11-05
Thanks, that works perfectly!

I've make a note of that magic command.

---

