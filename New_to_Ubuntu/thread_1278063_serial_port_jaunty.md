---
title: "serial port jaunty"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by angellika on 2009-09-29
hi, 

i am trying to co connect tunturi bike via serial port using usb serial converter. i have jaunty. i was trying minicom and some others programes as miniterm.py. when i tried echo i got this:

angelika@ti531925:~$ echo hello > /dev/ttyS0
bash: echo: write error: Input/output error

can anyone help me please?

jaro

---

### Post by lkraemer on 2009-09-29
You might try:
```

lsusb

```
or 
```

sudo wvdialconf /etc/wvdial.conf

```
to make sure you have the correct port as located by wvdial.

lk

---

### Post by angellika on 2009-09-29
nice, lsusb helped me so at least i know that serial port is connected in jaunty:

  	 	 	 	 	 	  Bus 005 Device 004: ID 0557:2008 ATEN International Co., Ltd UC-232A Serial Port [pl2303] 
 
i used this howto to instal and load up USB convertor to the system: 

[http://dev.forums.reprap.org/read.php?12,4546](http://dev.forums.reprap.org/read.php?12,4546)

what do you think about these connecting and disconnecting stuff below?

[QUOTE]angelika@ti531925:~$ dmesg | grep tty

[    0.004000] console [tty0] enabled
[ 1646.571196] usb 6-1: pl2303 converter now attached to ttyUSB0
[24902.840440] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[24977.361157] usb 5-1: pl2303 converter now attached to ttyUSB0
[28657.560764] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[28658.965864] usb 5-1: pl2303 converter now attached to ttyUSB0

so it looks like converter is finally connected to ttyUSB0. now just need to find or write some program that will handle communication with tunturi:) 

thanks for the hint lkreamer it moved me beyond horizont .o00o.

---

