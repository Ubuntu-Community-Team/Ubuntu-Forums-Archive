---
title: "minicom problem"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by mmq.kafi on 2008-09-09
[B]while I type minicom in terminal it says /dev/tty8 locked .

how I can unlock /dev/tty8?[/B]

---

### Post by Bart Simpson on 2008-11-25
> **mmq.kafi said:**
> [B]while I type minicom in terminal it says /dev/tty8 locked .

how I can unlock /dev/tty8?[/B]

Hi.
I do not know haw can you unlock /dev/tty8 but I advise you the method to configure minicom by hand from file:
1) sudo chmod -R 777 /etc/minicom
2) cd /etc/minicom
3) touch minirc.mdmcfg
4) gedit minirc.mdmcfg (or use any other editor like vim)
5) In the minirc.mdmcfg write:

# Machine-generated file - use "minicom -s" to change parameters.
pu port             /dev/ttyS0
pu baudrate         57600
pu bits             8
pu parity           N
pu stopbits         1

You should write your setting

6) Save minirc.mdmcfg
7) In terminal type: minicom mdmcfg
8) ...Now you are in minicom :)

If it will not work send me message :)

---

### Post by Nekativ on 2009-11-15
> **Bart Simpson said:**
> Hi.
I do not know haw can you unlock /dev/tty8 but I advise you the method to configure minicom by hand from file:
1) sudo chmod -R 777 /etc/minicom
2) cd /etc/minicom
3) touch minirc.mdmcfg
4) gedit minirc.mdmcfg (or use any other editor like vim)
5) In the minirc.mdmcfg write:

# Machine-generated file - use "minicom -s" to change parameters.
pu port             /dev/ttyS0
pu baudrate         57600
pu bits             8
pu parity           N
pu stopbits         1

You should write your setting

6) Save minirc.mdmcfg
7) In terminal type: minicom mdmcfg
8) ...Now you are in minicom :)

If it will not work send me message :)

Great advice!

---

