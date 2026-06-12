---
title: "MAC spoofing/rc.local"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by nickco on 2009-12-04
I am spoofing my mac address using these to lines:

```
ifconfig eth0 down hw ether xx:xx:xx:xx:xx:xx
ifconfig eth0 up
```I was wondering if there is a way to get this to run automatically every time I restart my computer.

I have tried adding them to rc.local but it doesn't seem to be working.

Honestly, I have very little idea how rc.local works and am looking for any solution that will get these to run at boot.

Thanks.

---

### Post by madmax.santana on 2009-12-04
Hello there! I am not a Ubuntu expert or not even good at any distro of Linux. Hell, I don't fully know how to administrate any operating system. Learning phase, :D

But I have a little idea. It can be a fool's day-dream of course. Why don't you try creating a script file for this spoofing code and give it exeutable status through chmod. Then integrate the Ubuntu to run the script file on startup through the Startup Configuration Utility.

I am not sure but if I were you, I would not hesitate in experimenting... Good luck.

---

### Post by bsharp on 2009-12-04
You can add options like that to the /etc/network/interfaces file. (I believe that's it, I'm not on my Ubuntu box right now)

---

