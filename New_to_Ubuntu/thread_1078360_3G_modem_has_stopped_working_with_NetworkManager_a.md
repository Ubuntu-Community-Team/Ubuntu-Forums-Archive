---
title: "3G modem has stopped working with NetworkManager applet"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by r3bol on 2009-02-23
I've been using a 3G USB modem with NetworkManager applet for a while now with no problems. All of a sudden, it just stopped working with the error - "The network has been disconnected". 

I tried things like restarting, deleting the modem's profile and creating it again, but it's still not working. 
I can connect with my WLAN dongle though and my 3G modem is working fine on my eeePC running the default Xandros distro. 

Anyone have any idea why it won't connect anymore on ubuntu?

Here is some info:```
leke@leke-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
leke@leke-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:07:89:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xee00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128072 (125.0 KB)  TX bytes:128072 (125.0 KB)

```

---

### Post by r3bol on 2009-02-23
Well well! It just so happened my update manager had 4 NetworkManager specific updates and straight after the update (and a restart) my 3G modem is now working again. 

Solved! :)

---

### Post by r3bol on 2009-03-01
Mark as solved seems to be missing from my thread tools.

---

### Post by dragon_reborn on 2009-03-15
how did you set up the dongle? I would like to use this method as well but do not know how to set it up?

---

### Post by r3bol on 2009-03-16
I have the Network manager applet installed - [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

So choose Edit connections from the applet menu and select the Mobile broadband tab from the window. Click the Add button and fill in the required fields your operator requires to run your 3G modem (This will be operator specific).

(If I remember correctly, it might require a restart for the modem to be recognised the first time).

I assume you have a data plan setup with your operator. Mobile data transfer can be quite expensive for general browsing ;)

Good luck :)

---

