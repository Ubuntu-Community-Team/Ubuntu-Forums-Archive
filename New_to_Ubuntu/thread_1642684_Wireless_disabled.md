---
title: "Wireless disabled"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-12-10
On my laptop running a 8GB WUBI install, my wireless seems to have gone down. When I right-click on my network indicator icon, the wireless option is greyed out and unchecked.

When I run:
```
sudo ifconfig wlan0 up
```
I get:
```
SIOCSIFFLAGS: Unknown error 132
```

Any ideas on why this is happening?
Thanks in advance.

---

### Post by kroq-gar78 on 2010-12-14
*bump*

---

### Post by synicalx on 2010-12-14
Do you know what model wireless card your lappy has?

Most wireless problems in Ubuntu seem to come from driver issues, most of which have some sort of workaround/fix

---

### Post by kroq-gar78 on 2010-12-14
I know its an Atheros adapter from seeing the windows updates but I don't know what kind. How do I find out?

EDIT: It runs 10.04 btw

---

### Post by hansdown on 2010-12-14
Hi kroq-gar78.

Hopefully, this thread helps.

[http://www.linuxquestions.org/questions/slackware-14/siocsifflags-unknown-error-132-wlan0-intel-wifi-5100-a-771841/](http://www.linuxquestions.org/questions/slackware-14/siocsifflags-unknown-error-132-wlan0-intel-wifi-5100-a-771841/)

---

### Post by kroq-gar78 on 2010-12-14
> **hansdown said:**
> Hi kroq-gar78.

Hopefully, this thread helps.

[http://www.linuxquestions.org/questions/slackware-14/siocsifflags-unknown-error-132-wlan0-intel-wifi-5100-a-771841/](http://www.linuxquestions.org/questions/slackware-14/siocsifflags-unknown-error-132-wlan0-intel-wifi-5100-a-771841/)
uhhh.... yeah..... that was what was wrong........ :|

it works after a reboot. that was stupid.....

Thanks to everybody who helped

---

### Post by hansdown on 2010-12-14
Err...
sorry kroq-gar78.

I just read that link to the end.

Glad you fixed it, though.

---

### Post by kroq-gar78 on 2010-12-16
without the drunk stuff :)

---

