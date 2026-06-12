---
title: "Problem setting permissions"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-03-04
Hi all,
    I've just started messing around with ruby and rails. Somehow I started my first rails project (a school assignment) as root and now I can't access the project without using sudo. I've chmoded the folder to 775 and set myself as the owner and I still can't open it in Netbeans. Any ideas?

Output:
```
dan@dan-netbook:~/Courses/Theory/CURRENT_PROJECT$ ls -l assign3
total 64
drwxrwxrwx 6 dan root 4096 2010-02-26 22:47 app
drwxrwxrwx 4 dan root 4096 2010-02-26 19:30 config
drwxrwxrwx 3 dan root 4096 2010-02-26 22:59 db
drwxrwxrwx 2 dan root 4096 2010-02-26 19:30 doc
drwxrwxrwx 3 dan root 4096 2010-02-26 19:30 lib
drwxrwxrwx 2 dan root 4096 2010-02-26 19:30 log
drwxrwxrwx 3 dan root 4096 2010-02-26 19:30 nbproject
drwxrwxrwx 5 dan root 4096 2010-02-26 19:30 public
-rw-r--r-- 1 dan root  307 2010-02-26 19:30 Rakefile
-rw-r--r-- 1 dan root 8819 2010-02-26 19:30 README
drwxrwxrwx 4 dan root 4096 2010-02-26 19:30 script
drwxrwxrwx 7 dan root 4096 2010-02-26 22:47 test
drwxrwxrwx 6 dan root 4096 2010-02-26 19:30 tmp
drwxrwxrwx 2 dan root 4096 2010-02-26 19:30 vendor

```

---

### Post by sandyd on 2010-03-04
```

sudo chown -R *_username:username_* ~/Courses

```
and theirs a ":" in between the two "username"s

---

### Post by woodsonoversoul on 2010-03-04
What are the two usernames? My username and...

---

### Post by sandyd on 2010-03-04
> **woodsonoversoul said:**
> What are the two usernames? My username and...
repeat your username twice with the colon in between, so if your username is mike, then... mike:mike

---

### Post by William Shotts on 2010-03-04
> **woodsonoversoul said:**
> What are the two usernames? My username and...

The first instance is your user name and the second is your group name.  Modern Linux distros use a scheme called *User Private Groups* where each user is a member of a unique group.  This scheme allow easier configuration of shared directories.  You read more about them here: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/System_Administration_Guide_/s1-users-groups-private-groups.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/System_Administration_Guide_/s1-users-groups-private-groups.html)

---

