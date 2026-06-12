---
title: "Strange problem!!!!!"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by becoolpal on 2009-07-02
I have this strange problem
I am an owner n i am not able to change the permission of the file that i have downloaded .Its actually a movie .When i click on the properties of the avi file It shows that the owner is "root" and i am not able to change its permission .Moreover i am not able to delete that file.

PLEASE TELL ME HOW TO DELETE THAT AVI FILE !

---

### Post by TeoBigusGeekus on 2009-07-02
```
sudo rm /location/of/file/nameoffile.avi
```
Careful with the rm command.

---

### Post by ~sHyLoCk~ on 2009-07-02
To change permission :

```
sudo chmod a+rx filename.avi   
```

Use ```
man chmod
``` to learn about different types of permission settings.

To remove it:

```
sudo rm filename.avi
```

---

### Post by becoolpal on 2009-07-03
thanx a lot !!! 
It worked !!!

---

### Post by Celauran on 2009-07-03
Changing permissions is fine, but if it's something you downloaded yourself, you may want to change ownership to your account (chown). Another question comes to mind, though; why is root the owner of the file? Are you running any applications as root?

---

### Post by becoolpal on 2009-07-04
that is what i am thinking .I never used any application as root .Don't know why it showing the root as owner.Anyways i have deleted the whole directory!!!

---

