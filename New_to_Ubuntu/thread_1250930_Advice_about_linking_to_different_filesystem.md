---
title: "Advice about linking to different filesystem"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by anirvana on 2009-08-27
Hello all,
           I'm looking for some advice about how to implement the following functionality in my pet project.

There are two users on my system, user1 and user2. When user1 logs in he can do what he wants etc.. when user2 logs in I want to somehow link the entire file system to another place. In more detail when user2 logs in and does something like ls ~, he should see contents of /home/user1/extra/home/user2/
and when user2 does ls /usr/bin he should see contents of /home/user1/extra/usr/bin/

Is there a simple way to do this kind of operation. I have looked up the ln command, but I am a little unsure about how to show a completely different file structure to a particular user.

Thanks in advance for any advice/pointers

---

### Post by duanedesign on 2009-08-27
When you add a new user it will create a home folder for that user.

```
 sudo adduser username

```

see adding/deleting new users in the following link. This will give you additional information about user managment such as setting folder permissions for particular users.

[https://help.ubuntu.com/9.04/serverguide/C/user-management.html](https://help.ubuntu.com/9.04/serverguide/C/user-management.html)

---

### Post by anirvana on 2009-08-27
@duanedesign

Thanks, but what if the user is already instantiated on my system. I agree when making a completely new user, this can be an option, but in my case the 2 users re already instantiated.

Any pointers/comments?

Thanks

---

### Post by Liolikas on 2009-08-27
Try ln things.

---

### Post by anirvana on 2009-08-27
@Liolikas

Thanks, I did play around with ln and found that you can make "soft links" to directories.

The problem being how can I link the user2 home directory to /home/user2 to something like /home/user1/buffer/home/user2 . can I use something like 
ln -s /home/user1/buffer/home/user2 /home/user2 .. I guess not. I didn't want to try it before I was sure so as to not hose my system.

Thanks

---

