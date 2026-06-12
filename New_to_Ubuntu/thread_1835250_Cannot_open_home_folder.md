---
title: "Cannot open home folder"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-08-29
Hi friends,

Iam using ubunut 9.10.

yesterday my hard disk space filled and it shows,  there is low disk space. i cleared unwanted data about 80GB. after i restarted my system. again i logged in my user account. once logged in, i can't open desktop folders and i tried to open home directory, its also not opening.

But everthing working perfectly in other user account.

Kindly guide me to slove this issue.

---

### Post by OlyPerson on 2011-08-29
How did you delete the files?

Try going into a terminal and typing "ls /home/YOUR_USER_NAME" (where YOUR_USER_NAME is user account name) and see if you get an error.  Will try and help from there.

---

### Post by pmohankumar on 2011-08-29
K, iam doing

---

### Post by cgroza on 2011-08-29
Kind of a long shot, but did you empty the Trash folder?

---

### Post by Redblade20XX on 2011-08-29
> **pmohankumar said:**
> Hi friends,

Iam using ubunut 9.10.

yesterday my hard disk space filled and it shows,  there is low disk space. i cleared unwanted data about 80GB. after i restarted my system. again i logged in my user account. once logged in, i can't open desktop folders and i tried to open home directory, its also not opening.

But everthing working perfectly in other user account.

Kindly guide me to slove this issue.

If you are logged into another account after deleting the items, maybe that account doesn't have or lost permission to read or write to your home directory.

Take a look at this: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

- Red

---

### Post by pmohankumar on 2011-08-29
Ya i can open in terminal.

---

### Post by pmohankumar on 2011-08-29
Thanks,

i just cleared trash and now its opening but very very very slow.

i tried these commands in terminal:

apt-get update
apt-get autoremove
apt-get -f install
dpkg --configure -a

but no reaction.

what should i do?

---

### Post by scott_g on 2011-08-30
If you only have access to the terminal, you could try:
```
df -h
```
to check the disk usage?

You could also try a:
```
sudo apt-get autoclean
```
to clear up some more space?

Could also try a:
```
ls -l
``` to check the permissions in your home directory.

Scott

---

### Post by pmohankumar on 2011-08-30
Mr. scott,
i found the enemy.
in system monitor i found that, 
gvfsd-metadata taking 98-100% of cpu usage and also taking 2.3 GB and above ram space.

if gvfsd-metadata stop running, processing was fast.

---

### Post by Rhizoid on 2011-08-30
> **pmohankumar said:**
> Mr. scott,
i found the enemy.
in system monitor i found that, 
gvfsd-metadata taking 98-100% of cpu usage and also taking 2.3 GB and above ram space.

if gvfsd-metadata stop running, processing was fast.

If that happens on restart, have a look here: [http://ubuntuforums.org/showthread.php?t=1421580](http://ubuntuforums.org/showthread.php?t=1421580) for a longer term fix.

---

### Post by pmohankumar on 2011-08-31
Thanks a lot for all.

I deleted the  gvfsd-metadata folder in /home/dev116/.local/share/ and then restarted the system.
problem solved.

---

### Post by jtarin on 2011-08-31
Looks Like when you get your disk full those archives get corrupt, just remove the folder and it will be created again and the issue should be repaired.

---

### Post by pmohankumar on 2011-09-02
Ya, that's wright .

---

### Post by jfed on 2011-09-02
If a thread is solved, please scroll to the top of it and click "thread tools" and then "mark thread as solved"

saves us time :D and plus its good measure

---

