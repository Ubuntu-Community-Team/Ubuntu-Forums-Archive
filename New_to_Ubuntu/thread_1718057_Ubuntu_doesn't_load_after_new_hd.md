---
title: "Ubuntu doesn't load after new hd"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by sav2003 on 2011-03-30
Hello,
Everything was ok until today when I placed another HD.
I have a dual boot new system win7+ubuntu 10.10. So when I placed my other hd,(the installation was made with one hd), ubuntu doesnt want to load again..The only thing I see aftes choosing ubuntu to load on Grub is a "_" and a black screen.. I attach 2 screenshots of the edit of the ubuntu load on Grub, and a screenshot that seems the new hd...Do I need to change something with edit in grub to load again??
Thanks in advance

p.s. My new hd used to be in raid before, its exactly the same with my first hd..I change motherboard, so system is working with 2 separate hds(in windows at least..)

[img]http://img19.imageshack.us/img19/1503/31032011565.jpg[/img]
[img]http://img33.imageshack.us/img33/875/31032011566.jpg[/img]

---

### Post by 5149.5 on 2011-03-30
You could try swapping the interface cables on the drives but it might not help.

---

### Post by sav2003 on 2011-03-30
I changed on edit hd0,msdos2 with hd0,msdos1, started but I now cannot access windows files and data :/

---

### Post by ronparent on 2011-03-30
Even though the raid is turned off in bios the raid meta data on the disk formally used in the raid needs to be erased. Raid meta data is erased with the dmraid program installed and running '**sudo dmraid -rE sda**' for each drive (or whichever drive has meta data). Once all meta data is cleared you can uninstall dmraid (optional).

---

