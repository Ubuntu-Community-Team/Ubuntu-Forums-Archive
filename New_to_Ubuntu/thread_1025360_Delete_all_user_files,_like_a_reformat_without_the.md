---
title: "Delete all user files, like a reformat without the reformat?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by karasuman on 2008-12-30
To make a long story short, a condition of my little brother getting his computer back is that all of the files on it are deleted first.  My dad has asked me to sort this out without actually looking at the files (guess what little bro has been looking at), and what I've come up with is

```
rm -rf ~/ &
```

which, of course, deleted his entire home directory.  Interestingly, it didn't seem to touch his trash, which has 109 lovely pictures in it...  

Is this the best way to go about doing this?  Any suggestions?

---

### Post by sam_delta on 2008-12-30
as far as i know, the trash is kept in your home directory at:
~/.local/share/Trash/files/

but since you already deleted the entire home dir, it is posible that he deleted the files as root, and the files are in the root trash?, not sure about that tho

also, remember that home folser contain hidden folders with configuration files vital for some programs, so  ull also loose some config 
why dont you just make a new user, and delete the current user?

sam

---

### Post by hyper_ch on 2008-12-30
well, the trash is hidden and you only delete the visible files with it. Easiest si to remove the whole dir and recreate it. If you brother's username is "brother" then do:

```

sudo rm -Rf /home/brother
sudo mkdir /home/brother
sudo chown brother:borther /home/borther

```

---

### Post by Ender41 on 2008-12-30
> **hyper_ch said:**
> well, the trash is hidden and you only delete the visible files with it. Easiest si to remove the whole dir and recreate it. If you brother's username is "brother" then do:

```

sudo rm -Rf /home/brother
sudo mkdir /home/brother
sudo chown brother:borther /home/borther

```

 Who is the superuser on this computer, ie you or your brother ?
If your brother and others use the computer then maybe you need to set up a root account, against ubuntu policy I realise but it may be the exception that proves the rule. If you are the superuser then just delete his account and recreate it with a new user name and password, that way he won't be able to access the old Trash files. If your brother is the only user of this computer then I would reinstall, this will make him start all over again and he might learn from his mistakes. However this time I would set myself up as the superuser and make sure he doesn't know my password.

---

### Post by karasuman on 2008-12-30
My brother is the only account on this computer; it's an old laptop, and he's the only one who uses it.  I didn't think I could delete his entire account without making a root account, which I've done before, but I'm not sure I want to do that with his computer.

---

### Post by handydan918 on 2008-12-30
If all the pix are in one place, this should be trivial. Especially if they all have a common extension. 

```
rm -rf *.jpg
``` for example. 

On the subject of creating a root account, I don't see why that would be needed. All you have to do is create another admin account, delete brother, and create a new account for him. You could even make his a limited account, and hide the admin account.

---

### Post by karasuman on 2008-12-30
Ha ha, this might all be a moot point, because I did just create another admin account, log into it, and...

the computer made a funny noise and turned off.  It won't turn back on.

I'm going to go ahead and blame it on the porn.  :P  (That, and it's, like, eight years old...)

---

### Post by handydan918 on 2008-12-30
> **karasuman said:**
> Ha ha, this might all be a moot point, because I did just create another admin account, log into it, and...

the computer made a funny noise and turned off.  It won't turn back on.

I'm going to go ahead and blame it on the porn.  :P  (That, and it's, like, eight years old...)


*GASP*
Oh NO!! You didn't run the dreaded ```
sudo frymy_computer
``` command did you??

:P

---

