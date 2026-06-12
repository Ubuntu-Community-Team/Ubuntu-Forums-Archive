---
title: "how to create a brand new user fully isolated from current user?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-14
Hi
I want to create another user for my ubunut, I want it to be able to login into Gnome but I dont want to let that user has any kind of access to the data which my current user puted in its home folder.

Can you please let me know how I can do it?

Thanks.

---

### Post by jakupl on 2008-12-14
okay... you dont want him to have access to your home folder or??

---

### Post by legolas_w on 2008-12-14
Yes, to my home folder, but he should be able to update the system or install new software. but absolutely no access to my home folder.

Thanks

---

### Post by jerome1232 on 2008-12-14
Just changing the permissions on your home folder should do the trick.

If you'r running Gnome then the gui way:

Click Places -> Home Folder, Now click "Up", Right click on your users home folder and select "Properties", Click the "Permissions" Tab, Remove all permissions from "Others".

---

### Post by iponeverything on 2008-12-14
Give the existing account these perms:

```

sodo chmod u+rwx /home/existingaccount
sudo chmod go-rwx /home/existingaccount

```

---

### Post by bodhi.zazen on 2008-12-14
See also : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by The Cog on 2008-12-14
Just to calrify those last 2 posts - you change your home folder so no other users or groups have any access. Then you just create another user in the normal way - Users And Groups from the menu.

---

### Post by jakupl on 2008-12-14
> **The Cog said:**
> Just to calrify . . .

:lol:

---

### Post by redandgreen on 2008-12-14
Not the OP, but wouldn't the new user be able to get into the folder with sudo anyway?

/noobiness

---

### Post by rakris on 2008-12-14
> **legolas_w said:**
> Yes, to my home folder, but he should be able to update the system or install new software. but absolutely no access to my home folder.

Thanks


He would get system administrative privileges if you update his id in /etc/sudoers

---

### Post by jerome1232 on 2008-12-14
If you want the new user to be able to update/install you could give the user permissions to only run apt-get as root, thus still limiting his ability to get into the other users home folder.

You would use the first command to edit the sudoers file the second is the line you would add to the bottom, replacing "newuser" with the real users name. I would recommend reading up on the sudoers file before you blindly follow my advice [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

```
sudo visudo
newuser ALL=(root) /usr/bin/apt-get
```

---

### Post by The Cog on 2008-12-14
If the other user can use sudo then he will be able to enter and see all your files. Your only recourse in that case is to keep your private files in an encrypted folder. I use encfs to keep my private data, but I hear that Intrepid has a different encrypted folder solution as an install option. 

If you want to use encfs, then you need to install encfs with **sudo aptitude install encfs** and then I use these two scripts to turn the directory on and off:
My script **crypton** contains this:
> #!/bin/sh
encfs ~/.crypt ~/crypt
and the script **cryptoff** contains this:
> #!/bin/sh
fusermount -u ~/crypt

These scripts create a folder called **crypt** where the plain file contents appear, and a hidden **.crypt** where the encrypted contents are kept.

---

