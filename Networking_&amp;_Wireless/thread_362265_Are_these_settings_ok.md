---
title: "Are these settings ok?"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-15
These are my settings: -

wlan0 IEEE 802.11g ESSID:"conexant" 
Mode:Managed Frequency:2.437 GHz Access Point: 00:0A:E9:02:1F:A6 
RTS thrff Fragment thr=2346 B 

And this is the end of my /etc/network/interfaces (note the default wireless usb device frequency is 2.412 but my router is 2.437): -

iface wlan0 inet dhcp
wireless-essid conexant
wireless-ap 00:0A:E9:02:1F:A6
wireless-freq 2.437G

The other this is that my driver was installed via ndiswrapper, and I did this once it was working: -

ndiswrapper -m

Is this driver now permanent?

Some confirmation of these settings would be cool, because I'll be able to turn the machine off

---

### Post by spd106 on 2007-02-15
They look ok, though you may not need the last two lines, leave it as it is at the moment though.

To check that it will start on boot check that the ndiswrapper is listed in the /etc/modules file
i.e. ```
~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper

```

and that an alias has been added to the /etc/modprobe.d/ndiswrapper file i.e.
```
~$ cat /etc/modprobe.d/ndiswrapper 
alias wlan0 ndiswrapper

```

---

### Post by wej1971 on 2007-02-15
Brilliant. As soon as I restle the g/f of the computer and switch back to Ubuntu, I'll try it.

Assuming the kernel update hasn't broken it.

---

