---
title: "weird error when i sudo modprobe ndiswrapper"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by jarvis13 on 2007-03-01
I have an HP Pavillion dv6110us and I'm trying to get dapper drake working on it (Edgy won't work with me at all)

I'm following the directions here [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

but when i type the command sudo ndiswrapper modprobe i get this error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/k ernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

any ideas? What more info do you need to help me with this?

I'm not exactly a newbie to Ubuntu (used it on my desktop for about a year) but this laptop gives me all kinds of trouble. But only with the wireless and the graphics card (Go figure).

---

### Post by spd106 on 2007-03-01
Can you please post the output of these commands?
```
ndiswrapper -v
```and ```
uname -r
```

---

### Post by jarvis13 on 2007-03-01
~# ndiswrapper -v
utils version: 1.9
driver version:        1.8
vermagic:       2.6.15-23-386 preempt 486 gcc-4.0



# uname -r
2.6.15-23-386


using a fresh dapper install. think i need a new kernel?

---

