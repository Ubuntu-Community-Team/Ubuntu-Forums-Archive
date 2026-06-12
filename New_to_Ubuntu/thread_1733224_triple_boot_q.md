---
title: "triple boot q"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-19
i have a dual boot b/w win7(sda1,2) and ubuntu(sda5,6,7) , a shared ntfs partition (sda4)
i want to boot bt4 as well , do i make new partitions ?
/,swap,/home for bt as well ?
or do i mount swap as mutual b/w bt4 and ubuntu 
and /home as mutual ?
and just keep a diff / partition for both ?

---

### Post by PhillyPhil on 2011-04-19
You can use the same partition for swap, but I wouldn't try it for / or /home.

---

### Post by varunendra on 2011-04-20
> **PhillyPhil said:**
> You can use the same partition for swap, but I wouldn't try it for / or /home.
+1.
In fact you 'shouldn't' make multiple swap partitions as it is just wastage of space and sometimes causes problems also.

And last time I tried bt4, it used legacy grub which was unable to boot karmik (9.10). So while installing make sure to choose not to install grub at all. After rebooting, just boot in to Lucid as normal and update your grub2 to include bt4 in your existing grub menu:
```
sudo update-grub
```

For a shared drive, as oldfred often suggests, it is best to have a separate /data (or whatever you want to name it) drive, and separate partitions for '/' for each installation (which will also include /home, as keeping '/' and '/home' on separate drives doesn't make much sense after having a separate shared drive for your data)

---

### Post by neil_1 on 2011-04-20
alright thanks guys :)

---

