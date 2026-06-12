---
title: "regarding multi serial port PCI card IO address problem"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by ayaskant16 on 2008-11-12
hi,
i am having a multiple I/O UART card.
my driver is able to detect all serial port.
but only for three ttyS* device it is giving some wrong I/O as a result on this port serial communication is not happening.

my linux Version is 2.6.23.2

the /proc/tty/driver/serial file shows

serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0
1: uart:16C950/954 port:00001060 irq:21 tx:0 rx:0
2: uart:TI16750 port:000010A0 irq:21 tx:3 rx:0 RTS|CTS|DTR|DSR
3: uart:TI16750 port:00E42CFB irq:20 tx:0 rx:0 CTS|DSR|CD|RI
4: uart:TI16750 port:00E7DCFB irq:20 tx:0 rx:0 CTS|DSR|CD|RI
5: uart:TI16750 port:00001068 irq:21 tx:0 rx:0
6: uart:TI16750 port:00001078 irq:21 tx:0 rx:0
7: uart:TI16750 port:000010E0 irq:20 tx:0 rx:0
8: uart:TI16750 port:00E2BCFB irq:20 tx:0 rx:0 CTS|DSR|CD|RI
9: uart:TI16750 port:00001060 irq:21 tx:0 rx:0
10: uart:TI16750 port:00001070 irq:21 tx:0 rx:0
11: uart:unknown port:000010B8 irq:21


thus from above you can see the port address for 3,4,8 are different and thus not working.

can you please tell me how to rectify this  
thanks in advance

---

