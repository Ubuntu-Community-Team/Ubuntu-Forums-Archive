---
title: "COM ports"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by TroyStachnik on 2010-02-01
I am programming a robot and using BASIC Stamp editor, when i start the program and try to identify which port my robot is plugged into, the program states No available COM ports. how can i fix this problem. (i am using Ubuntu 9.10)

---

### Post by Socrates1013 on 2010-02-01
How many COM ports do you have? If only one and you are trying to access /dev/ttyS0, another desktop/app may be accessing that port then you will have to close it. Are you using a serial usb adapter?

---

### Post by TroyStachnik on 2010-02-01
2 COM ports and no they are built in to the PC itself (Tower)

---

### Post by lkraemer on 2010-02-02
This will help you locate the serial ports:
[http://www.linux.org/docs/ldp/howto/Serial-HOWTO-11.html](http://www.linux.org/docs/ldp/howto/Serial-HOWTO-11.html)
[http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html)


lk

---

### Post by Socrates1013 on 2010-02-02
Try this to find out what processes are using that port:

fuser /dev/ttyS0
fuser /dev/ttyS3

you can use the -k switch w/ those commands as root to kill the process right away.

---

