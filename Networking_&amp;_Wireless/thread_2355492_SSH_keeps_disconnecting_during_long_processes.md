---
title: "SSH keeps disconnecting during long processes"
date: 2017-03-13
forum: Networking &amp; Wireless
---

### Post by netflow on 2017-03-13
Just to clarify, I have no problems if I'm idling, the connection will stay open for hours and hours without any issues.  However if I am try to run a process that takes a long time to complete, say du -sh on a huge directory, the connection will always disconnect at some point.  

While running this test I had another ssh connection open to the same server just to make sure it wasn't a problem with the connection in general but that other connection remained stable and connected while the one running the du -sh command disconnected

Does anyone have any ideas what might be causing this?

---

### Post by The Cog on 2017-03-13
A really wild guess, but maybe the network between you and the server is dropping large packets. Try reducing the MTU at your end a bit, to perhaps 1400.
```
sudo ifconfig eth0 mtu 1400
```
I'm probably wrong, but it doesn't take long to test.
Default MTU is 1500 if you want to put it back again. MTU is shown in the output of **ifconfig**.

---

