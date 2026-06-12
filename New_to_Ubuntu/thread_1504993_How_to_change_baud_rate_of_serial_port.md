---
title: "How to change baud rate of serial port"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by iron_guitarist1987 on 2010-06-08
I am trying to connect a Galil Motion Controller (DMC) into a desktop running Ubuntu 10.04 through the serial port. The DMC is has a baud rate of 19200, 9600 or 1200. The desktop only has one serial port. How do I change the baud rate of the serial port?

---

### Post by akester on 2010-06-08
I think the baud of rs-232 is 9600.

Some monitoring programs allow you to monitor different baud rates but as for controlling them, you might need some sort of converter.  I found a piece of software called [SerLook]("http://sourceforge.net/projects/serlook/files/") that looks like it might do that.

(PS if you want to connect it directly, make sure it is operating on RS-232, or else you might have communication problems.  I'm not the best with electronics so I am no help in helping convert it to RS-232.)

---

### Post by lkraemer on 2010-06-08
Try:
[http://ubuntuforums.org/showthread.php?t=51085](http://ubuntuforums.org/showthread.php?t=51085)

lk

---

