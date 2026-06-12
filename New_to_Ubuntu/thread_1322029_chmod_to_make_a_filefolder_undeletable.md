---
title: "chmod to make a file/folder undeletable"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by LeDechaine on 2009-11-10
I've ran into this problem once, and here I am again, because I don't know how I got this chmod or nautilus permissions interface config to work.

Seems to me that nautilus is buggy, i.e.: When you change the permissions of a file, you have to restart nautilus, or re-open your session, or completely restart the computer to enable the permissions to take effect, because nautilus seems to just don't care about the permissions and you can easily trash a "sudo chmod 700" file. It makes no sense, but hey, looks like that's how it works anyway.

So, if it's not the case, what am I doing wrong. I just want to make a file in my home folder undeletable (well, deletable only by root).

Or, if it's not possible, make a folder in my home directory undeletable (deletable only by root), i'll just put the file in there. (This was how I got it to work the last time, a question of parent folder permissions or whatever..)

---

### Post by amingv on 2009-11-10
Remember that "sudo chmod 700 somefile" makes "somefile" accessible only by it's current owner, if you created this file under your account you also need to change ownership to root for the file to be blocked. e.g.:

```
user1@ubuntu:~$ mkdir myfile
user1@ubuntu:~$ chmod 700 myfile
#file is stil accessible/deletable by user1, but nobody else
user1@ubuntu:~$ sudo chown root:root myfile
#file is now owned by root, and thereby only deletable by it
```

---

