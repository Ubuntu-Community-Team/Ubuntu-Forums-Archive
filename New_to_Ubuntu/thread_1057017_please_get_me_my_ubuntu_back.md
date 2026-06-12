---
title: "please get me my ubuntu back"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-02-01
i had ubuntu installed in sda6,and used sda7 as swap.recently,i shrunk sda5(which was a 100GB ext3 volume meant for data storage),and with the free space thus created proceeded to install archlinux.while installing i created a new ext3 root partition as required for arch,and now that   is named as sda6.ubuntu partition has become sda7 and swap sda8.my problem is that the GRUB installed by arch detected windows but not ubuntu(i actually wanted to triple boot with ubuntu,arch and windows xp).now,i am troubleshooting things with arch and i suppose it will take quite a while for me to make it a full fledged OS.But,i don't see ubuntu in the GRUB OS list.how can i get that done so that i can use ubuntu again.please help me use my favourite OS again.

---

### Post by shifty_powers on 2009-02-01
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

refers to reinstalling grub after installing windows but the principle is the same...

---

### Post by stonecoldjha on 2009-02-01
i am afraid that wouldn't work as it would detect ubuntu and windows,but not arch.i want a triple boot,i.e i want all the three OS viz xp,ubuntu and arch to appear in the list.

---

### Post by bumanie on 2009-02-01
Can you post the output of > cat /boot/grub/menu.lst from arch.

---

