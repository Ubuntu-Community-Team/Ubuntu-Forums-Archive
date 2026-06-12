---
title: "COnfigure Mobile Broadband Ubuntu 8.10 (U810/U1010)"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by yeufui on 2008-11-26
I have a U1010/U810 just installed with ubuntu 8.10, everything was working perfectly fine except for its HSDPA/3G configuration. I check that all hardware is detected and working but when i try to do a connection it got disconnected immediately, further troubleshooting i suspected there could be something wrong with the pppd, I am running out of idea...anyone could help please?

Thanks & Regards.

---

### Post by copai on 2008-12-11
hi, I also has the same problem with modem sierra 881u. I apply broadband for connection. if me connect always soon disconnect. please help me... (im using ubuntu 8.10)

---

### Post by matt.parkes on 2009-02-02
How did you check that the hardware is working?

I can't even seem to initiate a connection, I'm using a BlackBerry Bold.

---

### Post by theoldgit on 2009-02-25
I have the same problem. I used to use 8.04 and just plugged my phone in (Sony Ericsson k530i) and worked perfectly. I upgraded to 8.10 and nothing. Same phone same account but i cannot get it to connect. It reconises the phone and I can edit the settings but nothing seems to work. I now have a Samsung phone and thats exactly the same.
I plug in the phone and get the radio button on the network thing but when i select it i get disconnected immediately.
Help !!!!

---

### Post by katumba1 on 2009-02-27
I posted this on another thread and didn't get a response: can someone tell me just how to get it to dial out on the mobile broadband card? My 8.10 sees that card and I can configure it, I just don't know how to get it to connect.

Any help please??

Kat

---

### Post by tosk on 2009-04-09
There's a bug in network-manager that came with intrepid.

```
sudo apt-get update
sudo apt-get upgrade network-manager
```

[http://tosker.us/2009/01/30/mobile-broadband-in-ubuntu-810-64-bit/](http://tosker.us/2009/01/30/mobile-broadband-in-ubuntu-810-64-bit/)

---

