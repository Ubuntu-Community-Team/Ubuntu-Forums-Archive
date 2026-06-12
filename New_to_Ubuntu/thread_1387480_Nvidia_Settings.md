---
title: "Nvidia Settings"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-01-21
how do i get my nvidia settings to stay at the same res. because when i  logout or restart i have to set it all over again. its not a big task but i would like to just have it stay how i set it up.

---

### Post by cjnkns on 2010-01-21
I think you need to open the terminal and 

> sudo nvidia-settings

This should open the nvidia dialog and then any changes you make will stick.

---

### Post by Extract_Here on 2010-01-21
thanks man ill see if that helps

---

### Post by rossmoore on 2010-01-21
I have seen some people post that they have trouble making the settings stick. They could apply the settings with:
sudo nvidia-setting -l

That loads the settings. If that does the job then you can put this in /etc/init.d/rc.local.

---

