---
title: "Edit Grub."
date: 2011-02-15
forum: New to Ubuntu
---

### Post by nnjond on 2011-02-15
Hi,

I need to add 

rootdelay=130

to my grub menu every time I boot up.

Can someone please give me pedestrian instructions as how to edting 

(which) appropriate file to make a permanent change?

Thanks for your time.

---

### Post by davidmohammed on 2011-02-15
gksudo gedit /etc/default/grub

add rootdelay=xx to this line:
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=xx quiet splash"


save

sudo update-grub

---

### Post by mikewhatever on 2011-02-15
In a terminal window type **gksudo gedit /etc/default/grub**

locate the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

add your option:
```
GRUB_CMDLINE_LINUX_DEFAULT="rootdelay=130 quiet splash"
```

save and exit.
Run **sudo update-grub**

---

