---
title: "Gigabit ethernet driver help - noob"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by akiforj on 2005-11-17
I've got an IC Plus IP1000 gigabit ethernet on the motherboard, and I'm trying to install drivers for it but the instructions are not making much sense. 

> 
b. for kernel 2.6.x
        -------------------
           #make all  => generate ipg.ko
           #insmod ./ipg.ko
           #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy
              eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1...
              xxx  is your ip address, ex: 192.168.102.211
              yyy  is your netmask address, ex:255.255.255.0 


I've got the terminal opened and I'm at the directory where the driver files are, but inputting the first command does nothing, not even an error message. 

Can anyone tell me what the proper method is for installing this driver or direct me somewhere that does? Thanks.

---

