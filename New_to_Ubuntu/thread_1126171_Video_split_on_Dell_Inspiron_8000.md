---
title: "Video split on Dell Inspiron 8000"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by hoprutop7 on 2009-04-15
When I installed Ubuntu 8.04.1 I got a weird, split up screen that I couldn't seem to make work. I found part of the solution at this thread:
[http://ubuntuforums.org/showthread.php?t=187687](http://ubuntuforums.org/showthread.php?t=187687)
but I had to do a few things differently. Firstly, I clicked fn and f7 simultaneously to create a small, but readable, Ubuntu screen. Then I took the advice in the aforementioned thread and opened a terminal by going to the Applications menu, then accessories, then terminal. I typed:
1.cd /etc/X11 (enter)
2.sudo pico xorg.conf (enter)
3.now arrow down until you see Section "Device"
4.The Identifier doesn't matter, but you need to change or add a Driver
5. So, either change, or add a line that says Driver "vesa" right after the Identifier line.
6. To close, hit Ctrl-x, Y for yes to save, and enter.
7. To exit the terminal, type exit.
Reboot and hit Fn and f7 again to allow the video to fill the screen. Fixed!

---

### Post by billgoldberg on 2009-04-15
> **hoprutop7 said:**
> When I installed Ubuntu 8.04.1 I got a weird, split up screen that I couldn't seem to make work. I found part of the solution at this thread:
[http://ubuntuforums.org/showthread.php?t=187687](http://ubuntuforums.org/showthread.php?t=187687)
but I had to do a few things differently. Firstly, I clicked fn and f7 simultaneously to create a small, but readable, Ubuntu screen. Then I took the advice in the aforementioned thread and opened a terminal by going to the Applications menu, then accessories, then terminal. I typed:
1.cd /etc/X11 (enter)
2.sudo pico xorg.conf (enter)
3.now arrow down until you see Section "Device"
4.The Identifier doesn't matter, but you need to change or add a Driver
5. So, either change, or add a line that says Driver "vesa" right after the Identifier line.
6. To close, hit Ctrl-x, Y for yes to save, and enter.
7. To exit the terminal, type exit.
Reboot and hit Fn and f7 again to allow the video to fill the screen. Fixed!


point 1 and 2 can be replaced by

```
gksudo gedit /etc/X11/xorg.conf
```

Just saying.

---

