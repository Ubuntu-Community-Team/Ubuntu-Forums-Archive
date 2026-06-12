---
title: "Assistance Please!"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by tgnuhc on 2006-10-22
Everytime i reboot the pc, the wireless network shuts down. So, i have to go back into terminal and type in "sudo modprobe bcm43xx."  Is there any way to just set it up, so i don't always have to do this after every reboot?  Thanks!

---

### Post by Totzo on 2006-10-22
```
sudo gedit /etc/modules
```

insert your module, bcm43xx, save the file and that should do it

---

### Post by tgnuhc on 2006-10-22
Thanks, Totzo!!!  You made my life much easier, and i am eternally greatful.

---

### Post by Totzo on 2006-10-22
no bother, welcome to ubuntu!

---

