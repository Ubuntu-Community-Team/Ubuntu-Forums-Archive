---
title: "Pc wont connect to network"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Nolander on 2009-05-27
Uve installed ubuntu(9.04) on one of my desktop and im tring to connect to my laptop(vista) using a switch.my laptop says its got limited connectivity and my desktop wont connect at all. sorry for the lack of details ive been away from ubuntu for nearly a year!

ta,
nolander

---

### Post by cariboo on 2009-05-27
You will probably have to repair your Vista network connection before doing any thing else, as limited connectivity means that you really don't have acommection at, windows is just being optimistic.

One you have repaired your network connection try and ping your desktop.

```
ping 192.168.1.100
```

substitute your desktop ip address for the one in the above example.

---

### Post by lisati on 2009-05-27
I've had similar connectivity problems when one of my machines tries to use an IP address that it has no business using e.g. when the IP address has been assigned to another machine in the network. I'm not too clear on what causes it beyond noting that it has sometimes happened when I've woken a machine out of sleep/suspend/hibernate mode.

A short term solution is to use the "repair connection" option mentioned by cariboo907. My usual longer-term solution is to keep DHCP enabled in my machines and router, and set my router to assign a static IP address to each of the MAC addresses of my computers (both wired and wireless).

---

