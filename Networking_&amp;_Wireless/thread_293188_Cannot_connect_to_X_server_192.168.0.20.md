---
title: "Cannot connect to X server 192.168.0.2:0"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-11-04
I am telneting from an Ubuntu 6.0.6 laptop to a Fedora Core 4 server.

I then try to invoke an xterm.

I get the following error:

> Cannot connect to X server 192.168.0.2:0.
Check the DISPLAY environment variable or use `-d'.
Also use the `xhost' program to verify that it is set to permit
connections from your machine.

The $DISPLAY env var is set properly to point to my Ubuntu laptop.
I also used xhost (on the laptop) to allow connection to the laptop's X server from the FC4 machine.

But I am still getting this error.

What am I doing wrong?

Thanks!
Alex

---

### Post by amohanty on 2006-11-05
I dont know if you can use X forwarding in telnet, have you tried (assuming you have X forwarding enabled)
**ssh -X username@host_ip**

or if you have XDMCP enabled on the other machine (its disabled by default):
**X :20 -query host_ip**

HTH
AM

---

### Post by xp_newbie on 2006-11-05
> **amohanty said:**
> 
**ssh -X username@host_ip**

Bingo! This did the trick. Thank you very much!

---

