---
title: "I think i have a bug in Jaunty?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-02
When ever i insert a CD into my CD drive nautilus is not working , I am unable to open my computer or any other drive partition . But when i remove it , it works perfectly

---

### Post by MontelEdwards on 2009-05-05
> **ravi_buz said:**
> When ever i insert a CD into my CD drive nautilus is not working , I am unable to open my computer or any other drive partition . But when i remove it , it works perfectly
Probably something wrong with your CD drive.
Do you have any other OS that you could test this on?
 did this only happen in Jaunty?

---

### Post by ravi_buz on 2009-05-05
Yes it works fine in all other os and also all other ubuntu versions

---

### Post by mikezila on 2009-05-05
Is this the same CD drive you used to install Ubuntu?

---

### Post by ravi_buz on 2009-05-06
yes its the same

---

### Post by kpkeerthi on 2009-05-06
Insert your CD, wait for a few seconds and post the output of
```
dmesg | tail
```

---

### Post by ravi_buz on 2009-05-06
ubuntu@ubuntu:~$ dmesg | tail
[  109.724741] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[  114.900699] Adding 1004020k swap on /dev/sdb5.  Priority:-1 extents:1 across:1004020k
[  126.723915] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  126.723920] Bluetooth: BNEP filters: protocol multicast
[  126.994117] Bridge firewalling registered
[  139.287050] lp0: using parport0 (interrupt-driven).
[  140.368842] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
[  147.033553] mtrr: no MTRR for e0000000,10000000 found
[  151.256013] eth0: no IPv6 routers present
[  222.522008] nautilus[5288]: segfault at 9836000 ip b62887dd sp b6276fc0 error 4 in libbrasero-media.so.0.1.1[b6278000+1e000]

P.S i screwed my ubuntu so cant boot into it, this is from live cd session and still having the problem

---

### Post by kpkeerthi on 2009-05-06
This bug has already been reported and apparently fixed. Are you running 9.04 final Live CD? What does **lsb_release**  print?

See [http://https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/350010]("http://https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/350010")

---

### Post by ravi_buz on 2009-05-07
since the bug is fixed how can i solve the problem should i download anything

---

