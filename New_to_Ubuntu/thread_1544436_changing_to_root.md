---
title: "changing to root"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Sybil Ross on 2010-08-02
how do i log on as root in ubuntu or fedora?

---

### Post by uRock on 2010-08-02
In ubuntu, use  ```
sudo {command}
``` and in Fedora use ```
su
``` this is not safe and should only be used for administrative purposes. Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MasterGamerJK on 2010-08-02
[su root] changes to root, but if you want to graphically login as root, on ubuntu do this:

1- in CMD run "su root"
2-type "passwd"
3-creat a new unix password by entering it twice as prompted
4-log out
5-manually type in your new user name "root"
6-type newly created password
7-press "enter"
8-make changes and get out of root account
9-log back into your original noob account to use the system


it is not good practice to use the root account like this, unless your doing a lot of edting of restricted files. then it will save time, but you should NOT make a habit of useing root for everyday causes

---

