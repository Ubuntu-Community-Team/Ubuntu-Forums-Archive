---
title: "Wi-fi help"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by seilesh.BE on 2008-12-19
haio friends can any one of u help me...i am using acer laptop i want to know how to connect wifi in ubuntu ....

---

### Post by seilesh.BE on 2008-12-19
while installing ubuntu why is that necessary to creat /boot for min of 500mb

---

### Post by FuturePilot on 2008-12-19
> **seilesh.BE said:**
> haio friends can any one of u help me...i am using acer laptop i want to know how to connect wifi in ubuntu ....
If you click on the network icon in the corner by the clock, select "Connect to hidden wireless network" if you network is hidden. If it's not, it may just show up in the list.
> **seilesh.BE said:**
> while installing ubuntu why is that necessary to creat /boot for min of 500mb
You don't need to, but you can if you want. /boot just holds the necessary files that are needed to start booting up the system.

---

### Post by halitech on 2008-12-19
> **seilesh.BE said:**
> while installing ubuntu why is that necessary to creat /boot for min of 500mb

you probably don't need a seperate partition for it but even if you don't, it will create one because its part of the file system. I had to with my system because it wouldn't boot otherwise.

---

### Post by superprash2003 on 2008-12-19
post output of the following commands from terminal
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

