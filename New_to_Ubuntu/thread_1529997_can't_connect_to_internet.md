---
title: "can't connect to internet"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by mceven on 2010-07-13
Hello,

I just posted elsewhere and I think my query is better located here.  I installed Ubuntu 10.04 LTS and cannot connect to the internet at all, wired or wireless.  I figure that the wired connection has to be repaired first so I can install the proper drivers or whatever is needed to repair the wireless connection.  What info do I need to configure the wired connection?  Nothing is recognized when I connect the cable that's providing the internet connection to the computer I'm currently using (desktop vs. laptop).

Thanks for your help.

---

### Post by stevek123 on 2010-07-13
Generally direct wire connection is detected automatically. Even when booting from CD. I would suspect a hardware issue in the computer. One way to check would be to boot from an iso CD and see if it is detected...

---

### Post by HermanAB on 2010-07-13
Howdy,

Provided that there is a DHCP server on your LAN or internet router, you can fix things with:
$ sudo ifconfig
(to see what is going on)

$ sudo killall dhclient
(to make sure it isn't running already)

$ sudo dhclient eth0
(To bring things back up and auto configure the port)

---

### Post by MrOneEyedBoh on 2010-07-13
/\ Thanks for this.Im going to try this on my cousin laptop that we cant get it to connect wirelessly, odd...

---

