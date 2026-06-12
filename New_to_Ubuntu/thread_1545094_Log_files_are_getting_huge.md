---
title: "Log files are getting huge"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by mad_max0204 on 2010-08-03
Hi guys,

I have a ubuntu box running my vmware VMs and today it said
that my / is out of space. I checked and var\log is over 14gb.
Huge files are kern.log, messages, syslog, syslog.1.

What should I do ?

Thanks

---

### Post by TheStroj on 2010-08-03
I remember someone had an issue like this, where every transfered package was logged and log file was insanly big. 

Maybe you have same issue, maybe post some examples that show up gazillion times in those log files?

---

### Post by mad_max0204 on 2010-08-03
Every line is like this with some minor difference:

Aug  1 08:07:36 i7-server kernel: [367474.826757] Unknown OutputIN= OUT=vmnet1 SRC=172.16.230.1 DST=172.16.230.255 LEN=244 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=224

Transmission is running on the server btw. Looks like every single packet is logged and thats alot.

---

### Post by da burger on 2010-08-03
Hi I had a problem like this a while ago and there's a small chance the causes are the same. Do you have ufw or gufw installed? If so check the logging levels, as I had accidentally put the logging to very high levels and it was generating a few hundred MB a day.
Angus.

---

### Post by mad_max0204 on 2010-08-03
I'm using firestarter if that helps

---

### Post by mad_max0204 on 2010-08-03
bump

---

### Post by endotherm on 2010-08-03
well you can use bleachbit (as root) to clear the logs for now. 

as for your firewall, I usually use gufw (it's the project du jour, since firestarter has long been considered a dead project). in gufw you can't alter rules, so I would try to find the ones where logging is set to true, and remove them, replacing them with simmilar rules but without logging.

---

