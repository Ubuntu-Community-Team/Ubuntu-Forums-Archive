---
title: "Packet Tracer"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by thijsdeschepper on 2009-09-22
I have recently installed Cisco Packettracer on my Ubuntu 9.04. I used the package that was provided at the Cisco Website.

The program works, but when there are a lot of items (pc's, routers, switches) in my scheme it start to run really slow, much slower as on my Win Xp on the same computer (Dual Core 2 GHz Intel processor).

Is anyone experiencing the same problem as myself, and know how to fix it?

Thanks
Thijs

---

### Post by hailtothethief on 2009-09-23
I have a feeling that you don't have direct rendering. Test for this with

```
glxinfo | grep direct
```

at a terminal.

If there is any output, it should look like

```
direct rendering: Yes
```


If there isn't any output, go here for directions on enabling direct rendering: [https://help.ubuntu.com/community/BinaryDriverHowto/]("https://help.ubuntu.com/community/BinaryDriverHowto/")

---

### Post by thijsdeschepper on 2009-09-23
I checked it, and it seems the direct rendering is enabled. The output is like you described.

Thanks anyway
Thijs

---

