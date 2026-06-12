---
title: "Intalling problems!! please help"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by tubaking182 on 2009-02-05
ok, i'm not a total n00b, but i am decently new to the ubuntu scene, i have a previous version of ubuntu on an external hard drive and the grub was installed on the internal of my old laptop. now i have a "new" laptop and a new live cd for ubuntu 8.10, i would like to install the grub from my previous linux install because i have all my settings and such on it, but when following the guide on reinstalling the grub, i cannot get it to work. at the step where you type 

"grub>find /boot/grub/stage1"

i changed to 

"grub>find /media/disk/boot/grub/stage1"

as that is how the computer sees the external from the live cd, i get the error that the file is not found and i know it is there. when i had this issue before i was able to skip that step and just type 

"grub>root (hd1,0)

grub>setup (hd0)" or i could have typed (hd1) to put the grub on the external.

i get the error "error 21: selected disk does not exist"

i have no idea how to fix this as i have never come across it before. but when i try to just install brand new and lose everything i click install and go through until it says stating up the partitioner and it freezes at 50%. i have been sitting at 50% for about 30 minutes now and i am getting irritated.

i know the internal drive on this laptop is bad and i was wondering if maybe that had something to do with the partitioner not working or stopping at 50%. i really hope you guys can help me out, i promised y friend i live with that the laptop would be up and running by morning and it's 9:40 now, i am getting worried that the comp won't work. thanks in advance for your help!!

---

### Post by tubaking182 on 2009-02-05
correction, as soon as i posted this thread the partitioner started up, but it won't recognize my external, it only gives me the choice to install to the internal

---

### Post by tubaking182 on 2009-02-05
figured it out on my own, changed the usb cord i was using and was able to install in ten minutes

---

