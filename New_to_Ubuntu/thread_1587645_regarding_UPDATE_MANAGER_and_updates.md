---
title: "regarding UPDATE MANAGER and updates"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by utkarshjadhav on 2010-10-03
update manager isnt working properly ... dunno why ..
error is 
```

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```
and while I do the following 
```

sudo apt-get update

``````

sudo apt-get upgrade

```it generates a lot of errors. like 
```

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

```please help!

---

### Post by andrewthomas on 2010-10-03
Overloaded server?
 
Try again a bit later.

---

### Post by utkarshjadhav on 2010-10-04
output for 
```

sudo apt-get update
sudo apt-get upgrade

```-------------------------------------

```

root@utkarsh-desktop:/media# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

```
F1!!!

---

### Post by muteXe on 2010-10-04
who says it's a graphics problem?

---

### Post by ibizatunes on 2010-10-04
```
root@utkarsh-desktop:/media# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
```

make sure you dont have another package management open, ie ubuntu software center, or something like that

---

