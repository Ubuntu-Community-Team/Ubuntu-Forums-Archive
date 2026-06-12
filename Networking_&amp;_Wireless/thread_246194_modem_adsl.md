---
title: "modem adsl"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by Uchiha Sasuke^^ on 2006-08-28
hi there, well, i have a little problem, i don't know how to install Amigo ca80u usb adsl modem drivers, i download them from here [http://sourceforge.net/project/showfiles.php?group_id=47406](http://sourceforge.net/project/showfiles.php?group_id=47406) , name of the file "Driver for linux 2.6.10+" it contains five files: cxacru.c kbuild kconfig usbatm.c usbatm.h ... i read some about kernel, but i'm really new in linux, can anybody explain step by step how to install this, i can't download packages (cause i don't have internet in that machine) and then if someone can explain me how i define the user and pass to log to my internet service provider.thanz and escuse my english, i speak in spanish ](*,)

---

### Post by Uchiha Sasuke^^ on 2006-08-30
nobody can help with this?

---

### Post by Uchiha Sasuke^^ on 2006-09-03
thankz

---

### Post by drtvasudevan on 2006-09-03
well. you created a user account when you installed ubuntu.
use that.
there is no separate root account.

as for as modem is concerned i am not familiar with this one and so cant help.
in all probability it has been detected and configured.
just use DHCP and try to log into your net connection.
if not connected diable ipv6 and try again.
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox. 
if not working ping. do the following in terminal and post the result.
$sudo ifconfig
$ping -c 5 10.0.0.2
ping 82.211.81.186
ping [www.ubuntuforums.org](www.ubuntuforums.org)

---

