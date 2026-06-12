---
title: "Windows in Ubuntu"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Bigjge on 2009-04-25
I am using wubi.   Is the a linux program where I can run a windows program in ubuntu.

---

### Post by Natovr on 2009-04-25
Yes, [http://www.winehq.org/](http://www.winehq.org/)
install it by typing "sudo apt-get install wine" without quotes into the terminal

---

### Post by Spiritous on 2009-04-25
> **Natovr said:**
> Yes, [http://www.winehq.org/](http://www.winehq.org/)
install it by typing "sudo apt-get install wine" without quotes into the terminal

And VMWare

---

### Post by Natovr on 2009-04-25
and VirtualBox

---

### Post by atomizer on 2009-04-25
With wine you can run a single Windows program under Ubuntu.

With VMware you can install Windows in linux (the whole OS)

---

### Post by Spiritous on 2009-04-25
> **atomizer said:**
> With wine you can run a single Windows program under Ubuntu.

With VMware you can install Windows in linux (the whole OS)

:( Shh

---

### Post by presence1960 on 2009-04-25
> **Bigjge said:**
> I am using wubi.   Is the a linux program where I can run a windows program in ubuntu.

My preference is to run Windows in virtualization inside Linux rather than using wine. Some swear by wine but the fact is that you can't run ANY Windows software in wine. A good amount of the software out there for windows just will not work in wine.

Another preference I have is that the host OS should be more stable than the guest OS. Wubi may be fine to get newbies who are unsure of partitioning to get them using Linux, but the fact it is inside windows is a disadvantage/liability in my opinion. That is why I would recommend running Windows inside Linux with VMWare or Sun VirtualBox. You have a full install of windows and can run programs and the host OS (Linux) is very stable and secure. Just my preferences not looking to flame or be flamed. :)

---

### Post by UbuntuNerd on 2009-04-25
I run XP in Virtualbox and never had any problems, check this detail [guide](http://my.opera.com/ubuntunerd1/blog/show.dml/2855482)

---

