---
title: "[SOLVED] after installing failsafe terminal working but gui not working"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by ramesh24 on 2008-12-15
hai i have installed ubuntu 8.10 yesterday. my installation process gone smoothly, but when i am logging no gui display appear. i able to log through fail safe terminal. but when i log through genome only blank screen appear. i am using 14 inch samsung monitor with 600* 800 resolution. any body give me correct solution.
ramesh 24

---

### Post by Hospadar on 2008-12-15
Do you know what kind of video hardware you are using?

Could you post the outputs of the following commands:
lsmod
cat /etc/X11/xorg.conf
lspci

Also please post any errors or warnings you get at the terminal when you
sudo /etc/init.d/gdm restart
(this command restarts the GUI login manager, gdm)

Also maybe try
sudo /etc/init.d/gdm stop
startx

And post any errors you see

---

### Post by ramesh24 on 2008-12-17
today i sucessfuly installed ubuntu 7.10 faisty. it works correctly. thanks for haspadar for his valuable advice.
i given up installing ubuntu 8.10.

---

### Post by ramesh24 on 2008-12-23
i again reinstall ubuntu 8.10 and i sucessfully installed it . It worked correcctly. Thanks for hospader for his advice.

---

