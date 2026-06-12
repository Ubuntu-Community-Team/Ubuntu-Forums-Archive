---
title: "Samba Share Path"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-12-27
Folks,

Going mad here.

Running 16:04 on a laptop, also on my network I have two Raspberry Pi devices, both with samba server running.

One share definition displays exactly as expected but for some reason the other one has the following;

```
[TVH-Recordings]
comment = For testing only
        writable = yes
        create mode = 775
        path = /media/CORSAIR/Recordings/
        valid users = osmc
        directory mode = 775
        browseable = yes
        read only = no

```

For some reason when I browse the network both CORSAIR and Recordings show as directories.

I don't want CORSAIR to show, any ideas what may be the problem appreciated.

As mentioned, other R-Pi displays share exactly as required.

Geffers

---

