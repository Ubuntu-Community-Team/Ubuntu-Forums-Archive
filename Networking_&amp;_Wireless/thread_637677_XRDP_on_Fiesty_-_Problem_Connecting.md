---
title: "XRDP on Fiesty - Problem Connecting"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Kazade on 2007-12-11
Hi,

At work I have been running an XRDP server on Kubuntu Feisty for a while and it has worked perfectly fine when I connect from home. I've recently switched from Kubuntu to Ubuntu at work (without a reinstall, just a sudo apt-get install ubuntu-desktop) and now XRDP is broken.

I have edited the startwm.sh file so that it now looks like this:

```
#!/bin/sh

x11vnc -display :0 -localhost &
sleep 5
vncviewer localhost:0 -fullscreen
```

Which is a hack I have seen on these forums. It seemed to work because now when I connect I get a bit further but it bails out after "Send encodings" Here is what is displayed in the log:

```
password ok
sending share flag
receiving server init
receiving pixel format
receiving name length
receiving name
sending pixel format
sending encodings
error - problem connecting
```

Does anyone know how to solve this problem?

---

