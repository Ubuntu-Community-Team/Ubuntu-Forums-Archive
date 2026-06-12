---
title: "dpkg configure -a serious problem wont fix"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by BinaryEnCoder on 2010-08-22
Hello :)
I have a problem with updating and installing anything since 
dpkg was interrupted and when I run 
```
dpkg --configure -a
```to fix the problem it starts 
```
Setting up firefox (3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2~lucid) ...
```and it stays like this forever :( 
I'm new to ubuntu and I'm stuck here, I cant update :'( or install anything

---

### Post by mamut0o1 on 2010-08-22
Try this:
sudo chmod 755 /usr/bin/dpkg

then try this:
sudo apt-get upgrade dpkg

---

### Post by BinaryEnCoder on 2010-08-22
dude thnx, you're awesome!! it worked :)
now can you explain to me WHY it worked ?? i'm a bit confused

---

### Post by mamut0o1 on 2010-08-22
You're welcome; when you did the upgrade the permission to this folder got "deleted" /usr/bin/dpkg. so you issued a change mode 755 to restore this value and then you were able to upgrade the package.
That happend to me before too!

---

### Post by BinaryEnCoder on 2010-08-22
so its like locking the file right ? with the chmod we unlocked it then we upgrade
thats clever :) I didnt know what locking files works this way 
thnx again :)

---

### Post by mamut0o1 on 2010-08-22
Yes you could say that. You did not have permission to that file so you could not run it. see command "ls -l" so you can see what I mean.

---

