---
title: "Acessing the same evolution mail file from Ubuntu/Windows?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Chris Hansen on 2009-01-02
Hello,

On my dual boot system, I have Evolution installed on both Windows and Ubuntu. Can you change the location that the mail and stuff is stored and could you access it from both systems?

Thanks.

---

### Post by Tim Sharitt on 2009-01-02
You could create a link in your home folder called .evolution that points to the evolution folder on your windows partition. I don't think the config files are platform specific.
An example in a terminal:
```
ln -s /windows_partition/evolution_folder /home/username/.evolution
```
Plug in the correct directories of course.

It may be possible to point your Evolution folder in windows at your ~/.evolution folder, but you would need an ext2/3 driver for windows.

---

### Post by Chris Hansen on 2009-01-02
> **Tim Sharitt said:**
> You could create a link in your home folder called .evolution that points to the evolution folder on your windows partition. I don't think the config files are platform specific.
An example in a terminal:
```
ln -s /windows_partition/evolution_folder /home/username/.evolution
```
Plug in the correct directories of course.

It may be possible to point your Evolution folder in windows at your ~/.evolution folder, but you would need an ext2/3 driver for windows.

Thanks.

Turns out I'm having trouble getting Evolution to work in Windows. We'll see how it goes but it would be slick if it could work.

---

### Post by Chris Hansen on 2009-01-05
I couldn't get evolution to work in windows, is it possible to try a similar trick with Thunderbird?

I installed Thunderbird on both windows and ubuntu and it seem to work fine in both systems. I was looking at the folders for each version and they are different and I wasn't sure what to look for.

Thanks.

---

