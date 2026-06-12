---
title: "Lenovo stuck @ ubuntu boot menu"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by KageZ on 2010-03-28
hi everyone, 
 i m new on Ubuntu.I use "Universal USB Installer" copy Ubuntu 9.10 iso to my usb Scandisk 8 Gb. 

I can boot to "Ubuntu boot menu" on DOS; but then when i choose "run Ubuntu on this usb", it runs 3 lines of command then stuck there. Could anyone help me ?

[IMG]http://img97.imageshack.us/img97/3237/lenovop.jpg[/IMG]

---

### Post by spiderbatdad on 2010-03-28
is that a prompt you have at the end of line in your picture?
It looks like the message from kernel is "try usb=true." If you have a prompt after splash --, type in usb=true and hit enter. If not try f6 for other options, and Esc to get rid of any menu...then add usb=true to the end of the kernel line.

---

