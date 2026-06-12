---
title: "will not boot"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by swampdude on 2009-02-03
hi i am using ubuntu 8.10 and i just did my first restart after installing my graphics driver and all the updates but ubuntu will not boot up. once the loading bar is finished i get a black screen and it says:

boot from (hd0,0) ext3 47523572-7fc9 etc etc etc

starting up ...

loading please wait

19+0 records in
19+0 records out

kinit: name_to_dev_t(blah blah blah

kinit:no resume image, doing normal boot.


What is this please help me

---

### Post by lykwydchykyn on 2009-02-03
If you hit ctrl-alt-f8 is there more information there or just nothing?

---

### Post by Crafty Kisses on 2009-02-03
It sounds like you created a conflict between NVIDIA and Ubuntu modules and libraries. Try running the following and hope for the best:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by swampdude on 2009-02-03
it says checking battery state

---

### Post by swampdude on 2009-02-03
still dont work

---

### Post by lykwydchykyn on 2009-02-03
When you boot, see if you can get it to boot to "recovery mode" (it should be the second entry in the GRUB menu).  Get yourself to a root console (it should be a choice in the menu that will come up, if it actually gets that far) and try the command suggested.

---

### Post by swampdude on 2009-02-03
so codeman any ideas on whats to do?

---

