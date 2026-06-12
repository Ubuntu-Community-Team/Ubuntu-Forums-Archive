---
title: "File rights"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by thgthg on 2009-01-11
Having a folder /home/.gemensam that I want to make visible and give read/wright rights for all users logged in to the PC.

---

### Post by Oak37 on 2009-01-11
I believe if you remove the period '.' from the beginning of the folder name it will be visible automatically. You can change permissions of the folder by right clicking on the folder, selecting properties and then the permissions tab. Then choose which permissions you would like to accept.

Unless it's a folder you created yourself be careful about changing the folder name i.e. removing the period. It could potentially cause any programs etc. that link to that *exact* filename to not work properly.

---

### Post by thgthg on 2009-01-11
I have tried to change in the way you suggest but the folder is owned by root so I am denied to change rights

---

### Post by Oak37 on 2009-01-11
You could use the terminal to rename the folder and change permissions.

To rename the folder
```
sudo mv /home/.gemensam /home/gemensam
```

To change permissions use chmod
```
sudo chmod -R *** /home/gemensam
```
where *** represents the numerical value of the permission you would like to set, see [here]("http://www.freeos.com/articles/3127/") for more details.

Just to be careful though, be cautious when changing folders/files that are owned by root as they might be that way for a reason.

---

### Post by thgthg on 2009-01-11
OK tnx for your help. I did the changes and it works fine. However, I cant not make a starter refering to the place /home/gemensam anymore. Error message: "There is no program for this type of files"

---

