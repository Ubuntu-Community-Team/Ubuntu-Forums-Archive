---
title: "wireless problem"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by hodgesse on 2009-05-18
Hi Ubuntu People:

I installed Ubuntu 9.04 this evening.  I have both Windows and now Ubuntu on this computer.

However, my wireless connection is not working on the Ubuntu part.  It's fine on Windows.

I don't even get an option to connect to a wireless network.

Any suggestions, please?

thanks in advance,
Erin

---

### Post by Game Over on 2009-05-18
This should help

> **pulpinator said:**
> Looks like the problem is that there is no driver for that Linksys USB Wi-Fi dongle. So you'll have to use the Windows driver with ndiswrapper.

See this documentation on how to do that:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by superprash2003 on 2009-05-18
if you still face problems , post output of **lshw -C network** from the ubuntu terminal

---

