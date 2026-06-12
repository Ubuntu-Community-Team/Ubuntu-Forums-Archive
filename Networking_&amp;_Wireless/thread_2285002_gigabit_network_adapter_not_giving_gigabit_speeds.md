---
title: "gigabit network adapter not giving gigabit speeds"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by thevikas on 2015-07-02
HI, I have a the MB with realtek gigabit ethernet. I have another computer (mac with gigabit thunderbolt) with another gigabit card. To test, I directly connected both computers with the same wire and checked with iperf.

```
[  4] local 192.168.0.22 port 5001 connected with 192.168.0.25 port 53588
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   113 MBytes  94.0 Mbits/sec

```

Please suggest why my setup does not give near 1000 Mbits bandwidth. Is this a driversw issue? The cards are connecting using 1000Mb/s as repoted by gnome.

---

### Post by weatherman2 on 2015-07-02
What kind of cable are you using?  Cat 5?  Cat 5e?  Cat 6?

I would try transferring more than 113 MBytes for the test.  I think can set this as an option to iperf.

Also, you might for fun try connecting them together with a gigabit switch.

---

