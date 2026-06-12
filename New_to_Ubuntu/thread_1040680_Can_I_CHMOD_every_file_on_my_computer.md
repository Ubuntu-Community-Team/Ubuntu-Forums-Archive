---
title: "Can I CHMOD every file on my computer?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by RarelyWrongJared on 2009-01-15
Is there a way to use chmod to enable all permissions for every file & directory for every user on my volume "public"?



chmod -R uog=wrx /public/

is that right?  or will that remove permissions?

Any insight would be appreciated!
Thanks!

---

### Post by Iowan on 2009-01-15
It *might* be possible... and probably easier to do than undo when something goes wrong - some things don't work with the wrong permissions.

---

### Post by Bölvaður on 2009-01-15
There is also ~/Public/ which you could also play with.

but yes you can do that, or chmod 777 /public which sets all rights on (7 = 111 in binary, which stand for write read execute)  755 is the norm though.

---

### Post by RarelyWrongJared on 2009-01-15
what would the code be?

chmod -R 777 /public/

i really need help with the syntax on this one....
thanks!

i need all users complete access to every file...

---

### Post by handydan918 on 2009-01-15
> **RarelyWrongJared said:**
> what would the code be?

chmod -R 777 /public/

i really need help with the syntax on this one....
thanks!

i need all users complete access to every file...

Why? And do you know what constitutes a file?

---

### Post by albinootje on 2009-01-15
> **RarelyWrongJared said:**
> 
chmod -R uog=wrx /public/


This is the same (except using sudo) :
```

sudo chmod -R 777 /public/

```
But please realize, depending on the setup of your machine/users/access, that this is a potential security hazard.

---

### Post by RarelyWrongJared on 2009-01-15
i have a LAN network wtih a volume called "public"
with MANY sub-directories, each containing files with different permissions from different users.
the intention is to let ANY samba user access ANY file or directory and do ANYTHING they want off our public volume.

currently, we are encountering permission issues when we try to copy or open some files...
i would like to get on the server and change the permission of every file so every user can read write and execute any directory or file that has been placed under PUBLIC

is there a way to do this?  we have over 100,000 files in thousands of directories....

if there is a chmod command that will recursively make all permissions on everything 777 for everyone, that is what I am looking for....

---

### Post by albinootje on 2009-01-15
> **RarelyWrongJared said:**
>  if there is a chmod command that will recursively make all permissions on everything 777 for everyone, that is what I am looking for....

In that case you should start use the "force user=" and "force group=" and force file and dir permissions options for that share in Samba, otherwise you can run in trouble again, because of different samba users reading and writing, while still using the default umask, and thus create... files and/or directories which others cannot move or delete etc.

---

### Post by jerome1232 on 2009-01-15
Yes that will make it so that any user can read, write and execute files in there. And it will recurse into all subdirectories of /public.

The only problem is that when a user creates a file in /public then it will be owned by them with default permissions (rw-r--r--) I don't know how to overcome that.

---

### Post by albinootje on 2009-01-15
> **albinootje said:**
> In that case you should start use the "force user=" and "force group=" and force file and dir permissions options for that share in Samba, otherwise you can run in trouble again, because of different samba users reading and writing, while still using the default umask, and thus create... files and/or directories which others cannot move or delete etc.

Here's an example :
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

Section :  How to share group folders with read/write permissions (Authentication=Yes)

An example for your purpose, after having used your chmod -R command already on /public :

```

[Public]
  comment = Public share
  path = /public
  guest ok = yes
  read only = no
  create mask = 0700
  directory mask = 0700
  force user = root
  force group = root

```

Restart samba, and test it.

In the near future you might want to create a non-priviledged user.
For example creating a new user called "public", with /bin/false as shell, just to take care of those samba share permissions for your public share with that new user, with "force user = public" etc.

---

