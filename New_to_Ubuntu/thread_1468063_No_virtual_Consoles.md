---
title: "No virtual Consoles"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by @rizz on 2010-05-01
Hello Friends,

   I just switched to Ubuntu 10.04 and it seems great but i cant find my Virtual console......?????????
when i press ctrl + alt + F2 all i get is a pitch black screen and no prompt.........????

Any help will be appreciated:KS

---

### Post by dracayr on 2010-05-01
yeah I had that too.. I have no Idea what changed it back to normal though.. :P

---

### Post by @rizz on 2010-05-01
Good to know i am not the only one.....but i need them back.....wonder what should i do?????

---

### Post by dracayr on 2010-05-01
[http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

to sum it up, there are two approaches, for most, one of them works, but there are some for which the problem is still unresolved.
A: ```
sudo modprobe vga16fb
sudo modprobe fbcon
``` (to make the change permanent, add vga16fb and fbcon to /etc/modules)

B: in the /boot/grub/menu.lst delete splash and vga=xxx from kernel line, 
or press "e" key before booting to edit this line and then press "b" to boot to check if it works.

dracayr

---

