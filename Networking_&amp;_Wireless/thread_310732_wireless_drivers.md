---
title: "wireless drivers"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by crazychristoph on 2006-12-01
I have a Linksys WMP54GS that was not detected with the default wireless driver from edgy.  So I installed ndiswrapper to install the wireless driver I downloaded from linksys.com  

```

chris@petunia:~$ sudo ndiswrapper -i ~/Desktop/Drivers/WMP54GS.inf
Installing wmp54gs
chris@petunia:~$ ndiswrapper -l
Installed drivers:
wmp54gs         driver installed, hardware present
```

Ok good, then I type modprobe ndiswrapper, then I check syslog to see if it  worked.  I then find this error.

```

Dec  1 16:57:14 petunia kernel: [   36.363575] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
Dec  1 16:57:14 petunia kernel: [   36.444510] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Dec  1 16:57:14 petunia kernel: [   36.444517] ndiswrapper (load_sys_files:215): couldn't prepare driver 'wmp54gs'
Dec  1 16:57:14 petunia kernel: [   36.445035] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

```

So my question is, does anyone have this card working on a 64 bit machine? And if so are there any 64 bit drivers to be found?

---

### Post by KingBahamut on 2006-12-01
[http://dossy.org/archives/000110.html](http://dossy.org/archives/000110.html)

for that card, though I have not tested it myself.

---

### Post by crazychristoph on 2006-12-01
Thats the guide I used. I got as far as modprobe which seemed to not work.  Thanks though.

---

