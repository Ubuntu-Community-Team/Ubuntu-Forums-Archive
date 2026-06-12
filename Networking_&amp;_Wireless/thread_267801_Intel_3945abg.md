---
title: "Intel 3945abg"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by Charles Hand on 2006-09-29
Why does my Intel 3945abg work out of the box when I install Ubuntu, but never works when I build a kernel? 

(I know, use ndiswrapper. It's more of an academic question.)

---

### Post by Charles Hand on 2006-09-29
Hmmm. Ndiswrapper isn't working

syslog:Sep 29 14:42:31 localhost kernel: [4294698.601000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
syslog:Sep 29 14:47:04 localhost kernel: [4294699.250000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

It sure would be nice to know how the Ubuntu installation makes this chip work without ndiswrapper.

---

