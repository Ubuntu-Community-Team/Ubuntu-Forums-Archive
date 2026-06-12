---
title: "gparted"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Drenriza on 2009-11-26
When i installed ubuntu in the dorm of time, i didnt use the entire hdd for the operative system (why, i dont know :)).

Now ive used gparted to make the remaining gb,s to an ext 3/4 primary filesystem. to work along with my ext2 primary boot partition. But i cannot create anny folders in it.

I've been told i need to give myself the rights to the new drive, but how do i do this?.

Hope some1 can help.
Thanks on advance:KS

---

### Post by plucky on 2009-11-26
> **Drenriza said:**
> When i installed ubuntu in the dorm of time, i didnt use the entire hdd for the operative system (why, i dont know :)).

Now ive used gparted to make the remaining gb,s to an ext 3/4 primary filesystem. to work along with my ext2 primary boot partition. But i cannot create anny folders in it.

I've been told i need to give myself the rights to the new drive, but how do i do this?.

Hope some1 can help.
Thanks on advance:KS

Look here [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux) for further information.

Good Luck

---

### Post by ukripper on 2009-11-26
Install gparted:
```
sudo apt-get install gparted
```

Here is very good video to understand rest of the steps - [http://www.youtube.com/watch?v=9jT8n9PKiFE](http://www.youtube.com/watch?v=9jT8n9PKiFE)

---

### Post by profeta81 on 2009-11-26
once the filesystem is mounted directory <dir> (tthe name is up to you), from the command line you could do:

cd <dir>            # where <dir> is the name of the directory there the FS is mounted
sudo mkdir <name>   # this creates the directory (administrator passwrd required)
chown <your_name>:<your_group> <name>

then you will be able to go with the file browser to that directory and move, create and delete files as you wish.

note: you can find <your_name> you can use the command:

whoami

and for the <your_group>:

id -gn

regards

---

