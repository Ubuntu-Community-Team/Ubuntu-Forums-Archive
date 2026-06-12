---
title: "wine sharing"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by arju305 on 2010-11-03
Guys. currently facing 2 problem. Help Me Please!!!!!!!!!!!!!!

1.    I installed a software using wine. It's location is in .wine folder within home. Theress another user in my dekstop. He also want to execute the program. But he cannot do that as he is not accessible to open my home folder.
How can it be solved.

2. The other user (desktop user of course) cannot even mount the windows drives i.e NTFS. When ever he clicks, administrator password is asked.
How can it be done.
:(

---

### Post by yeats on 2010-11-03
> 1. I installed a software using wine. It's location is in .wine folder within home. Theress another user in my dekstop. He also want to execute the program. But he cannot do that as he is not accessible to open my home folder.
How can it be solved.

Can the other user also install software?  If so, they'll need to install it within their profile as well.

> 2. The other user (desktop user of course) cannot even mount the windows drives i.e NTFS. When ever he clicks, administrator password is asked.
How can it be done.

If the other user is someone who can be trusted, you can make him an administrator System -> Administration -> Users and Groups - change the account type.

---

### Post by arju305 on 2010-11-03
> **chrissharp123 said:**
> Can the other user also install software?  If so, they'll need to install it within their profile as well.



If the other user is someone who can be trusted, you can make him an administrator System -> Administration -> Users and Groups - change the account type.

File size is about 500mb. Is there no way except installing twice???
Sorry. I dont want him to be the adminitrator.

---

### Post by mutex023 on 2010-11-03
> **arju305 said:**
> File size is about 500mb. Is there no way except installing twice???


You have to change the permissions of you home directory then.
Right click your home directory in /home and change the permissions to allow others to read/write .
Then create a link to the exe file (i'm assuming its an exe your friend wants to run) in the .wine folder from you friends home folder. To create a link, just right click on the file and select 'create link'. Then copy the link to your friends home folder.

---

### Post by arju305 on 2010-11-05
> **mutex023 said:**
> You have to change the permissions of you home directory then.
Right click your home directory in /home and change the permissions to allow others to read/write .
Then create a link to the exe file (i'm assuming its an exe your friend wants to run) in the .wine folder from you friends home folder. To create a link, just right click on the file and select 'create link'. Then copy the link to your friends home folder.

Can the path of the wine folder be changed i.e not in home????

---

### Post by eriktheblu on 2010-11-05
Edit /etc/fstab to automatically mount the ntfs partition. That should make it available to all users.

---

### Post by arju305 on 2010-11-05
Thanks alot. IT worked.
But what about wine.... do u know how to place it at a folder away from home.
It would be a great help again.

---

