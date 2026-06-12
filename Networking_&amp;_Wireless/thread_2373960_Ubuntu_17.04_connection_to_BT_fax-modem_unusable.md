---
title: "Ubuntu 17.04 connection to BT fax-modem unusable"
date: 2017-10-11
forum: Networking &amp; Wireless
---

### Post by DinghyMan on 2017-10-11
I am using Ubuntu 17.04 with a BT Fax Modem from Trusty. I have had this connection working before with earlier versions of Ubuntu, and I have paired the device, and can see it is connected to /dev/ttyS0 as it reports on the baud rate. 
[FONT=courier new]#sudo setserial -avG /dev/ttyS0
[FONT=arial]gives[/FONT]
#/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test[/FONT]

However, if I use e.g. Gtkterm to communicate with the device, it reports "Cannot open /dev/ttyS0: Permission denied".

I have ensured that I am in the same permissions group as dialout (sorry if my terminology is incorrect).

If I use chmod 666 /dev/ttyS0, then I stop receiving the error, but if I try to type AT commands (as a prelude to getting it to work with Efax-gtk), I get no response. Typing "AT<CR>" should provide the response "OK", which I don't receive. If the baud rate were wrong, I would expect to see corruption, which I don't see.

Any help would be most appreciated.

Many thanks,

---

