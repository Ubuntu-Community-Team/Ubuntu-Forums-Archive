---
title: "QCA9565 / AR9565 on Ubuntu 14.04 Cannot enable wireless"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by mahdi7 on 2015-02-15
Hi, i have problem connecting using wifi on Ubuntu 14.04, i try every tips on this forum but none works for me.  When i click turn on wireless, it automatically turn off. It cannot be enabled.  I just installed ubuntu yesterday on my laptop and update it.
This is the output of the script. Can someone help me?

---

### Post by praseodym on 2015-02-15
There is an Acer module loaded (obviously, its an ASUS computer?!):
```

sudo rmmod acer_wmi
sudo rfkill unblock all
```

---

### Post by mahdi7 on 2015-02-21
Wow, It works! 
Thanks for your help!

---

