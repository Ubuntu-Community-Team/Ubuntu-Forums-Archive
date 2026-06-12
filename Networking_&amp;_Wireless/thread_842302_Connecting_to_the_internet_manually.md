---
title: "Connecting to the internet manually"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by manoka on 2008-06-27
Hello,
Does anybody know whether it is possible to connect to the internet manually and to disable the automatic connection. I'm using Ubuntu 7.10 and a broadband usb modem.
Many thanks in advance!
manoka

---

### Post by forger on 2008-06-27
you mean order the usb modem to be disconnected from the internet?

you can only disconnect from the modem I think:
```
sudo /etc/init.d/networking stop
```

otherwise, sounds like you need desktop automation: python-dogtail
> 
Description: GUI test tool and automation framework
 dogtail is a GUI test tool and automation framework written in Python.
 It uses Accessibility (a11y) technologies to communicate with desktop
 applications. dogtail scripts are written in Python.
 .
 Homepage: [http://people.redhat.com/zcerza/dogtail/](http://people.redhat.com/zcerza/dogtail/)


---

### Post by manoka on 2008-06-27
Thanks!
But the more important thing would be to (re)connect to the internet server (or -provider), as the connection is getting cut off (or braking down?) too often, and then I have to restart the computer every time to get connected again.

---

### Post by forger on 2008-06-27
you can start it the way you stop it ;)
> sudo /etc/init.d/networking start
or 
sudo /etc/init.d/networking restart

---

