---
title: "nokia n95 unable to access mass storage"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2009-04-18
Hi when I plug in my nokia n95 by the USB cable and select DATA transfer mode I get an error message.


Unable to mount 8.0 GB Media
Failed to execute child process "gnome-mount" (No such file or directory)


How do I access the mass memory

---

### Post by hesjnet on 2009-04-18
Is gnome-mount installed?

Write this in the terminal:
```
sudo apt-get install gnome-mount
```

Or search Synaptic for "gnome-mount" (without the quotes)

---

### Post by bigmonmulgrew on 2009-04-18
bingo tyvm
takes seconds when you know how.
Just dropped that code in a terminal, plugged my phone back in and popped straight up.
Not sure how it got removed but I did screw a lot of things up a few weeks ago experimenting and am waiting for 9.04 before I reinstall.

Thanks again

---

