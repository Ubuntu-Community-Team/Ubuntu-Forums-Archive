---
title: "modem doesnt work"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by vivek.pandey on 2010-10-06
i gotta a 2G bsnl usb modem but the problem is it doesnt work on ubuntu or any linux os...how to make it work...i m really pissed off using windows but need to have an internet access so cant switch to ubuntu..pls help:confused::confused::confused:

---

### Post by alaukikyo on 2010-10-06
maybe try this? 
[http://news.softpedia.com/news/How-to-Connect-the-ZTE-MF636DB-USB-Modem-on-Ubuntu-158663.shtml](http://news.softpedia.com/news/How-to-Connect-the-ZTE-MF636DB-USB-Modem-on-Ubuntu-158663.shtml)

---

### Post by dineshs on 2010-10-07
connect your modem.Post the results of the following terminal commands(applications-accessories-terminal)
```
lsusb
```
```
dmesg | grep -e "modem" -e "tty"

```

---

