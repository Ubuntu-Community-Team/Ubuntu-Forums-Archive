---
title: "Nova-t pci fails to do a thing"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by regomodo on 2010-11-30
Hi,

I've got a tv card in my system and I can't get it to do a thing. 

/dev/dvb/ is populated and I can see the card via lspci.

However, cli-tools such as 'scan' fails with an error(intentionally removed the locale):

> 
root@ubuserv:~# scan /usr/share/dvb/dvb-t/xx-xxxxxxx 
scanning /usr/share/dvb/dvb-t/uk-Salisbury
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2287: FATAL: FE_GET_INFO failed: 25 Inappropriate ioctl for device

Any suggestions?

---

