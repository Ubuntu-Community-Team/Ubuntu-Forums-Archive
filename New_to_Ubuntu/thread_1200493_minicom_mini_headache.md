---
title: "minicom mini headache"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by gurt on 2009-06-30
I get this...
[INDENT]bam@mingus:~$ minicom
Lockfile is stale. Overriding it..
Cannot create lockfile. Sorry.
[/INDENT]Is there a way to clear it?

Also, minicom is not seeing ttyS0. I can see it there, but it doesn't work like the others.
[INDENT]bam@mingus:~$ dmesg|grep ttyS
[    1.104715] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.104947] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.105197] ttyS1: detected caps 00000700 should be 00000100
[    1.105208] 0000:03:00.0: ttyS1 at I/O 0xbc00 (irq = 17) is a 16C950/954
[    1.105326] ttyS2: detected caps 00000700 should be 00000100
[    1.105338] 0000:03:00.0: ttyS2 at I/O 0xbc08 (irq = 17) is a 16C950/954
[    1.105454] ttyS3: detected caps 00000700 should be 00000100
[    1.105466] 0000:03:00.0: ttyS3 at I/O 0xbc10 (irq = 17) is a 16C950/954
[/INDENT]

---

### Post by gurt on 2009-06-30
I figured out that I need to use -o option with minicom to avoid lockfile. I'm still not sure what it means though.

Still no solution on ttyS0 -- it's the only one not working.

Anyone?

---

### Post by Mark20 on 2009-08-21
Could be a number of different issues, here are some questions that come to mind:

Have you configured minicom to use ttyS0?  Is it possible minicom is simply using the wrong port?

Are you using the correct baud rate?

Have you tried using other similar programs?  Maybe give gtkterm a shot.

Can you give more detail into what exactly is wrong?

Mark

---

### Post by Mark20 on 2009-08-21
Ahhhh, just realized this is mega outdated.  Oh well :)

---

