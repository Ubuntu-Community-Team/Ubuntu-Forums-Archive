---
title: "Intel(R) PRO/Wireless 3945ABG/BG help"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by wengkhin on 2008-06-13
......

---

### Post by safire on 2008-06-13
I have the same adapter on my Dell Inspiron 1720. It works fine with kubuntu 8.04.

---

### Post by Gagle on 2008-07-19
Same problem here, worked fine out of the box on my previous Feisty install.   Now, after a fresh install of Hardy Heron, wireless and wireless LED indicators aren't working.   :confused:

---

### Post by JagDragon on 2008-07-19
There is a driver there for it: Enable it with
```
sudo modprobe iwl3945
```

If that works, and Network Manager (top right of screen) starts aqquiring networks, then make it default. Edit the /etc/modules file and add the line iwl3945.
```
gksu gedit /etc/modules
```

Hope that helps!

---

### Post by Gagle on 2008-07-19
I found excellent (and sooo simple) advice from Chili55 in this thread :
 
[http://ubuntuforums.org/showthread.php?t=766304]("http://ubuntuforums.org/showthread.php?t=766304")

Try it out especially if you have an intel 3945ABG.
It fixed both the LED and wireless connectivity issues I had.

:guitar:

Thx a ton for your help !

---

