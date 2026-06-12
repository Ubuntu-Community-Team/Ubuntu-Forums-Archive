---
title: "With what can my linux box receives SMS from my gsm mobile?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-15
Hello,

I would like to command my linux box running with SMS. 

Is there any way to do such things? 

Thank you, 
Y.

---

### Post by northern lights on 2009-12-16
This summer, we wanted to have an SMS-blog for our travels.

This dude from a German hitchhike community had coded one ([http://sms.abgefahren-ev.de/]("http://sms.abgefahren-ev.de/")) and was so kind as to let us use it. You'd need a cell phone with a working SIM (prepaid does it) and a USB connection. Now as for pulling SMS from the phone in a regular intervals - I ain't got an idea how he did it. If however you're really interested and think yourself capable enough to grasp his code, contact *MrTweek* of *abgefahren.de*

---

### Post by frenchn00b on 2009-12-17
but normally we have some ways with internet. I recall one can send free in US, but in europe one can use a prepaid website for sending and receiving. 
```

~$ apt-cache search sms | grep sms
gammu-smsd - SMS message daemon
libgsmsd7 - SMS daemon helper library
gnokii-smsd-mysql - SMSD plugin for MySQL storage backend
gnokii-smsd-pgsql - SMSD plugin for PostgreSQL storage backend
gnokii-smsd - SMS Daemon for mobile phones
libsms-send-perl - driver-based API for sending SMS messages
prismstumbler - Wireless network sniffer
sms-pl - Send SMs via Polish GSM operators
smsclient - A program for sending short messages (SM / SMS)
smstools - SMS server tools for GSM modems
libnauty-dev - library for computing graph automorphisms (development files)
libnauty0d - library to compute graph automorphisms and canonical labellings
nauty - command line tools to compute graph automorphisms
ksmserver - session manager for KDE
```

although a GNU linux free version would be better. 

I have to read how to realise it ...your blog [http://sms.abgefahren-ev.de/](http://sms.abgefahren-ev.de/)
to be capable to receive sms

---

