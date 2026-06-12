---
title: "Concern about access to home folder"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Udayakiran on 2009-09-18
Hi, i have installed media tomb to my file server. I had made myself and the 'users' group (udayakiran:users) the owner of the media folder. Then i made it accessible with full permissions (rwx) by myself and the 'users' group and no permission for others. So, mediatomb could not access the folder. I added myself to the mediatomb group. and it could read the media folder.

the relationship of the groups and users can be visualized like this:
```

user        mediatomb     udayakiran
                |        /     |     \
                |       /      |      \
group         mediatomb    users    udayakiran
                           /              \ 
                          /                \
folder                  Media          /home/udayakiran

```Now my question is, can mediatomb read my home folder too? And if anyone could login with the mediatomb user id, can they access my files?

I have a suspicion that mediatomb may also be a member of the users group.

---

### Post by mapes12 on 2009-09-18
> And if anyone could login with the mediatomb user id, Login in as mediatomb and check it out yourself.

---

### Post by Udayakiran on 2009-09-19
Unable to login. What is the default password for mediatomb user?

---

### Post by seshomaru samma on 2009-09-19
If you are concerned about certain files, right click on them and choose properties , you can see the permissions there. You can do that for folders as well. 
If I'm not mistaken there is no default password for mediatomb , if can verify it [here ]("http://mediatomb.cc/pages/documentation")

---

### Post by Udayakiran on 2009-09-20
> **seshomaru samma said:**
> If you are concerned about certain files, right click on them and choose properties , you can see the permissions there. You can do that for folders as well. 
If I'm not mistaken there is no default password for mediatomb , if can verify it [here ]("http://mediatomb.cc/pages/documentation")

I'm using server edition without any GUI. So cant do what you said.

I was unable to login to the mediatomb account.

And i made a HUGE mistake. Though the mount folder was owned by udayakiran:users, the files were owned by udayakiran:mediatomb. I guess thats how mediatomb was able to access the files. I'm sorry. My fears were unnecessary.

Thx for your help.

---

### Post by kevmitch on 2009-09-20
I guess you solved your problem, nevertheless, these could have proved handy.
```

groups mediatomb

```
that should tell you what groups mediatomb belongs to.

The mediatomb user probably has no password (i.e., should not be able to log in at all). You can however become that user with su
```

sudo su mediatoomb

```

---

### Post by Udayakiran on 2009-09-26
> **kevmitch said:**
> I guess you solved your problem, nevertheless, these could have proved handy.
```

groups mediatomb

```that should tell you what groups mediatomb belongs to.


Actually that added to the mystery when i tried it. 'mediatomb' belonged to no other groups than the 'mediatomb' group.

> **kevmitch said:**
> 
The mediatomb user probably has no password (i.e., should not be able to log in at all). You can however become that user with su
```

sudo su mediatoomb

```


Using that command, i get:
```
This account is currently not available.
```

Thx for the reply.

---

