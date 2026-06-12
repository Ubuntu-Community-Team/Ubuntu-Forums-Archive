---
title: "EVDO usb card not detecting"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by hunter2000_ on 2009-07-18
In ubuntu 8.04 when I issue command
**modprobe usbserial vendor=0x05c6 product=0x6000** 

I get the error
**FATAL: Error inserting usbserial (/lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko): Operation not permitted **

output of **lsusb** is
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 19d2:fffe
Bus 001 Device 001: ID 0000:0000

Can some one explain why this happens and how to get the usb device detected?

---

### Post by Tman5293 on 2009-07-18
It might not be recognized because the filesystem is not readable by Linux. I suggest repartitioning it.

---

### Post by niteshifter on 2009-07-18
Hi,

Must modprobe as root:
```
sudo modprobe usbserial vendor=0x05c6 product=0x6000
```

---

### Post by GeorgeVita on 2009-07-18
Hi **hunter2000_**,
from your **lsusb** seems to have the **19d2:fffe** modem and not the **05c6:6000** you are trying to use. Check and inform us.

You can also do some basic tests:

Boot without the modem, wait for the system to load, attach it, wait 15-20 seconds, open a terminal window and try:```
dmesg
```
This command will show all system activity. Look at the last 10-15 lines for 'usbserial' or 'ttyUSB' etc. Copy here only these 10-15 lines of **dmesg**.

Try also:```
**ls /dev/ttyU* /dev/ttyA* /dev/ttyH***
``` to see if any serial communication port is already created for your modem. Post the  respond of above command.

Read also: [http://ubuntuforums.org/showthread.php?t=1113950](http://ubuntuforums.org/showthread.php?t=1113950)
(and the links included)

Regards,
George

---

