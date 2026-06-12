---
title: "unused disk"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by micox on 2011-07-08
Originally I loaded Ubuntu on one disk of my twin 250 disk Toshiba Satellite laptop making the original Windows OS shift over to the other disk. I've now trashed all of the useless Windows rubbish so I have an empty 250 disk. But I can't get into it with my Ubuntu OS and it's a shame to waste it. Any ideas please. The disk shows as 'New Volume' in my Places list.:lolflag:

---

### Post by grahammechanical on 2011-07-08
Is this disk formatted? Do you want to access files already on it or use it to store files? Have you run Disk Utility? What does that say about this disk?

Regards.

---

### Post by lmarmisa on 2011-07-08
You should be able to access that second hard drive from Ubuntu without any problem. You can mount it selecting Places -> New Volume. The files and folders of this unit will be located at '/media/New Volume'.

Try to install gparted if you wish to rename the name of partition New Volumen with a different label (for example, MyData). If you wish to install Gparted. open a terminal and type

```

sudo apt-get install gparted 

```

---

### Post by wildmanne39 on 2011-07-08
> **micox said:**
> Originally I loaded Ubuntu on one disk of my twin 250 disk Toshiba Satellite laptop making the original Windows OS shift over to the other disk. I've now trashed all of the useless Windows rubbish so I have an empty 250 disk. But I can't get into it with my Ubuntu OS and it's a shame to waste it. Any ideas please. The disk shows as 'New Volume' in my Places list.:lolflag:
Hi, try to mount it using disk utility then you should be able to access your files.

---

