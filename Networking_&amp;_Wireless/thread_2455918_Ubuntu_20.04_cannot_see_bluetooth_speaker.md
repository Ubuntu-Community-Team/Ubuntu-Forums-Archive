---
title: "Ubuntu 20.04 cannot see bluetooth speaker"
date: 2020-12-30
forum: Networking &amp; Wireless
---

### Post by 6tr6tr on 2020-12-30
When i open bluetooth settings, it see my phone and some other devices but not my bluetooth speakers.

Laptop: Lenovo X1 Carbon 4th Gen (16 GB RAM)
Speakers: Sony SRS-X77
Ubuntu 20.04

I have the speakers in pairing mode. Is there any software I can install that will find and pair it?

---

### Post by #&amp;thj^% on 2020-12-30
How are you trying to pair it?
Mine srs-xb22 one click to power on, followed by a long press 2-3 secs you should hear pairing.
```
[bluetooth]# scan on
Discovery started
[CHG] Controller 74:D8:3E:93:80:4F Discovering: yes
[NEW] Device 88:C2:55:B6:07:18 POWERDRIVER-0718
[NEW] Device F8:DF:15:7F:64:73 SRS-XB22

```
```
inxi -F
System:
  Host: me-ThinkPad-X1-Carbon-7th Kernel: 5.4.0-59-generic x86_64 bits: 64 
  Desktop: MATE 1.24.0 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 20R10010US v: ThinkPad X1 Carbon 7th 
```

---

### Post by 6tr6tr on 2020-12-30
Ah, I understand! Thank you!

---

### Post by #&amp;thj^% on 2020-12-30
Magic...
No really, just open a terminal and run this for me _while the speakers are in pairing mode_.
```
bluetoothctl

```
your prompt will change to "[bluetooth]#"
now run:
```
scan on
```
Show Now?

---

### Post by 6tr6tr on 2020-12-30
Yes, the issue was the speakers were not going into actual pairing mode. I think they were connected to something else. Thank you for helping!

---

### Post by #&amp;thj^% on 2020-12-30
> **6tr6tr said:**
> Yes, the issue was the speakers were not going into actual pairing mode. I think they were connected to something else. Thank you for helping!

:) I hate when that happens. ;)

---

