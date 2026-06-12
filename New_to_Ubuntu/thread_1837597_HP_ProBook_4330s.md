---
title: "HP ProBook 4330s"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by sjur on 2011-09-02
I just got a HP ProBook 4330s, which won't connect to Wifi because it's "disabled by hardware switch". The button for wireless (perhaps the "hardware switch"?) keeps blinking between yellow and blue. <code>rfkill disable all</code> didn't work, and no proprietary drivers appear in the list. Any help would be greatly appreciated.

---

### Post by LowSky on 2011-09-02
Welcome to the forums... try the command and then in the top right of the panel right click the network icon and enable wireless if you can.

found this solution here:
[http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working](http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working)

Hopefully it helps

---

### Post by sjur on 2011-09-02
Hi LowSky, and thanks for your quick reply! I've tried that several times with no success. But I think I got it working now, after downloading and compiling a new Ralink driver. Thanks for your help, though;)

---

