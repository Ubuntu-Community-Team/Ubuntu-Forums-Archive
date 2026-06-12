---
title: "Bluetooth Personal Area Network (PAN) in 8.10"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by eee1000huser on 2009-02-24
Can anyone point me towards a tutorial on how to set up a bluetooth PAN (tcp/ip over bluetooth) in Ubuntu 8.10.

It seems most tutorials are based on the old version of bluetooth stack used in 8.04..


Cheers,

--e

---

### Post by cak3 on 2009-03-24
bump. I am trying to get one setup between two computers, and don't know enough to really figure it out myself.

---

### Post by fa2k on 2009-04-03
Please help with this one. I suddenly realised that I can no longer connect to the internet via my phone. I only use this rarely, but it would be nice if it would work those times.

I used a simple script before, but it no longer works
```
#!/bin/sh
sudo pand -E -D -S -c 00:16:B8:8F:4D:14
echo Connecting...
sleep 20
sudo dhclient bnep0
echo Done!

```

---

### Post by kervel on 2009-04-29
i think it is simply broken in the ubuntu version of bluez. ubuntu comes with bluez 4.32 and quoting the release notes of bluez:

> 
Release of bluez-4.33
16th March 2009, 08:00 am by Marcel Holtmann

The releases fixes multiple regression within the networking service and SDP service discovery.

i am trying to get it to work in various ways, including directly via dbus, without any luck, on 2 machines, both with internal bluetooth and with an external dongle..

---

### Post by sanktnelson on 2009-05-07
see this bug report on launchpad:

[https://bugs.launchpad.net/bugs/336012](https://bugs.launchpad.net/bugs/336012)

It also contains a workaround at least for the case of connecting to a mobile phone.

---

### Post by fa2k on 2009-05-07
Thank you sanktnelson for telling me about this bug! 

I get an IO error from the ```
sudo hcitool enc ...
``` commmand in the workaround :( It is nice to know that it is registered as a bug, though. I just hope that someone takes the time to fix it.

---

