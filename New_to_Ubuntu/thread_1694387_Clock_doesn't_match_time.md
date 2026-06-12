---
title: "Clock doesn't match time"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Awesome96 on 2011-02-24
I'm having this problem where the clock in the top bar doesn't match the time settings. After looking around on the Internet I tried setting the hardware clock and then setting the system time to the hardware clock time setting, but it doesn't match up?
awesome@ubuntu:~$ sudo hwclock --date 022415432011
Thu 24 Feb 2011 09:40:57 AM CET  -0.969108 seconds

Why is it setting it to 09:40:57 AM when I'm asking it to set it to 15:43?

---

### Post by rburkartjo on 2011-02-24
awe are you dual booting between windows an linux. let me know if you are i have a fix.

---

### Post by Awesome96 on 2011-02-24
> **rburkartjo said:**
> awe are you dual booting between windows an linux. let me know if you are i have a fix.

Yes, also, switching DE to gnome through ubuntu-desktop seemed to fix the issue, compared to xfce in xubuntu. I thought the only difference between the *buntus was the DE and the default packages installed?

---

### Post by rburkartjo on 2011-02-25
here is the reg fix if you want to install never had any problems after i did

[http://lifehacker.com/#!5742148/fix-windows-clock-issues-when-dual+booting-with-os-x](http://lifehacker.com/#!5742148/fix-windows-clock-issues-when-dual+booting-with-os-x)

---

