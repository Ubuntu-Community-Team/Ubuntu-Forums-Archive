---
title: "Ubuntu 11.04 Does not Start. (Fresh Install)"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by rez182 on 2011-05-04
did a fresh dual boot install of Ubuntu 11.04 a couple of times, all the results were the same, it does not start. after i select ubuntu from the grub, the purple screen shows up (the loading logo does not show) then a message appears at the top left of the screen saying:
> mountall: Disconnected from Plymouth
and it freezes. im sure its the lack of driver compatibility (graphics card to be exact) although it worked perfectly fine in 10.10. how i know is because if i unchecked the "Download updates while installation" box, 11.04 started but in classic mode.

in recovery mode if i select failsafe graphics mode, it does not load.

how can i fix this problem?

thanks

---

### Post by mike555 on 2011-05-04
you probably picked "auto login" when you installed it ........ bad move...... you need to be able to pick "classic" from the login menu....

---

### Post by rez182 on 2011-05-04
no i did not im sure. im pretty cautious about my personal data so i make sure i have to enter my password at login.

EDIT: if i download the driver while installing, i cant see the login screen at all...if i dont download driver while installing, then it tell me to select classic at login.

---

### Post by searchfgold6789 on 2011-05-04
Also, try setting "nomodeset" to be one of your boot options, from grub before you boot. It goes right after the line saying "quiet splash".

---

### Post by rez182 on 2011-05-04
> **searchfgold6789 said:**
> Also, try setting "nomodeset" to be one of your boot options, from grub before you boot. It goes right after the line saying "quiet splash".
im sorry i dont understand what your talking about. how do i do this and what is the benefit?

---

### Post by mike555 on 2011-05-04
OK , then when you put in your username go down and pick "classic" from the menu at the bottom bar, then put in your password and enter.

---

### Post by rez182 on 2011-05-04
> **mike555 said:**
> OK , then when you put in your username go down and pick "classic" from the menu at the bottom bar, then put in your password and enter.
so there is no hope of enjoying the unity? and i should never download the driver that pops up in "additional driver"?

---

### Post by mike555 on 2011-05-04
I went through a bunch of trouble getting Unity to work ( I have a Nvidea 7300 ) and ended up deleting nvidea drivers , then installing an experimental driver that showed up in drivers after a restart ..... it seems to work ok , but I don't really like Unity so switched to classic anyway .......if Ubuntu doesn't have the classic option in the next version , I'll be looking for a different distro ...

---

### Post by rez182 on 2011-05-04
will the official driver from nvidia work?

EDIT: it might work read this [http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml](http://news.softpedia.com/news/New-Nvidia-Linux-Driver-Supports-Ubuntu-11-04-196264.shtml) (might need some help with installing it)

---

