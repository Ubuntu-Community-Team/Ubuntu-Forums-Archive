---
title: "Remote Desktop Server recommendation?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by six30two on 2009-11-29
Running Ubuntu Server 9.10 with a Xubuntu desktop. 

Any recommendations for a remote desktop server application? I'd like to use the GUI for my server while I'm in class, and my server is in my room. 

I use an old shitter Dell Latitude while I'm in class, so I'm hoping for something that doesn't lag like all hell.

---

### Post by earthpigg on 2009-11-29
have you considered ssh with X forwarding?

the lag will depend entirely on the upstream bandwidth of your server...

---

### Post by XCan on 2009-11-30
If you're wanting graphically intensive apps, you better be prepared for having Gbit lines if you use X forwarding. Compression may help you though. Also, some apps are just inherently slow through X forwarding for some to me unknown reason. For example, the editor and main window in Matlab lags for me without being even close on consuming the BW (within LAN).

---

