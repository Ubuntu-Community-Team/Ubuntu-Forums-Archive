---
title: "how do i change permissions for drives"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by avishek.ganta on 2010-07-27
While installing Ubuntu 9.04 I have created 4 partitions /root ,/media/C , /media/D , /media/E, The C , D, E drives have the owner as root , so how do i change it coz i am not able to access those drives [ cant use it as a storage space ].
PS:  New to Ubuntu.

---

### Post by endotherm on 2010-07-27
well, there are two things to consider. first, will you be useing the storage to store user files, or system apps/data?  will the data be used by more than one user?

if they are for user files, then open a terminal and enter these commands:
```

cd /media
sudo chmod -R <username>:<username> .

```

this will change the ownership of all the folders in /media to be owned by you. if you just want to apply it to single directories, replace the folder name where the '.' is. 

that should do you. be Very careful with chown. if you accidentally chown your / partition, there is no fix except to rebuild or restore from system backup.

---

### Post by avishek.ganta on 2010-07-27
wats <username>:<username> ? Is this my computer username??

---

### Post by endotherm on 2010-07-27
> **avishek.ganta said:**
> wats <username>:<username> ? Is this my computer username??


yep. lets say my username is 'yeeshkiplimpk'. I would enter a line like:
sudo chown -R yeeshkiplimpk:yeeshkiplimpk .
chown is the command.
-R tells it to perform the command on all sub directories and files  therein
username:groupname are the user and primary group you want to give the ownership to. all users have their own private group.
and . is the path to the item you want to chown. '.' is shorthand for the current directory.

when people post commands online, whenever you see angle-braces <> the convention is that you replace the <> tokens with the information pertinent to your use.

hth

---

### Post by Don1500 on 2010-07-27
> 
```

cd /media
sudo chmod -R <username>:<username> .

```

.

I believe you mean:

```

cd /media
sudo **chown** -R <username>:<username> .

```

---

### Post by endotherm on 2010-07-27
quite right, good catch. I do that at least once a month...

---

