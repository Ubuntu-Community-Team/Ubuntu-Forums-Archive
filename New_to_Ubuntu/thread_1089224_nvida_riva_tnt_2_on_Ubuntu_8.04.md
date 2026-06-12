---
title: "nvida riva tnt 2 on Ubuntu 8.04"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by pafire on 2009-03-06
hello,
i have tried a couple of methods to install nvidia riva tnt 2 drivers on my ubuntu 8.04 but to no use. This is on a dual boot pc with the other system being xp home. I cannot increase my screen size any larger than 800 x 600 on the Ubuntu system ,please help with any suggestions

---

### Post by overdrank on 2009-03-06
> **pafire said:**
> hello,
i have tried a couple of methods to install nvidia riva tnt 2 drivers on my ubuntu 8.04 but to no use. This is on a dual boot pc with the other system being xp home. I cannot increase my screen size any larger than 800 x 600 on the Ubuntu system ,please help with any suggestions

HI and have you tried using ```
gksu displayconfig-gtk
``` and adjust the resolution. The driver that is install with Ubuntu should work well.

---

### Post by pafire on 2009-03-07
here are the results, stil need help on this issue
 gksu displayconfig-gtk 
on_button_test_config_clicked()
Got pid 10394
(0, 0)
checkpoint 1
None
False
Sorry, this configuration video card driver
and monitor doesn't appear to work:

Messages from the X server:
(EE) Problem parsing the config file
(EE) Error parsing the config file
Fatal server error:

---

