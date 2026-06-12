---
title: "usermod don't create home dir"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by hypermorph on 2010-10-14
Hi, I'm trying to know everything about user and group creation and have found a problem I can't fix. I create a new clean (almost) account:


$ useradd newacc
After creating the password I want to assign the home directory for the account:


$ usermod -md /home/newacc newacc

$


And this is what I get. Nothing in response from the system. So I guess, everything is OK. But the directory hasn't been created. So I repeat the operation:


$ usermod -md /home/newacc newacc

 $ usermod: no change (or like that. I'm translating from spanish)
But the directory is not there. I check the etc/passwd file and the directory appears as my home directory.

 

By reading the manual page I thought that was the way to assign a home directory (and copy the /etc/skel contents) to a user that hasn't got any. But it's not working for me.

Any help would be greatly appreciated.

Thanks

Fran
-----

Santos
------

---

### Post by papibe on 2010-10-14
I would recommend you to use "adduser" instead of "useradd".
Regards.

---

### Post by hypermorph on 2010-10-14
Well. thanks for your answer. But that didn't solve my problem. I want to do it the other way, and if it is possible I want to know what I'm doing wrong (if I'm doing something wrong) and the right way to do it.

Thanks

---

### Post by QLee on 2010-10-15
[QUOTE=hypermorph]Well. thanks for your answer. But that didn't solve my problem. I want to do it the other way, and if it is possible I want to know what I'm doing wrong (if I'm doing something wrong) and the right way to do it.
...[/QUOTE]
Well, papibe's advice was probably good advice because the useradd man page also give the same advice.

However, of course you can choose to do things the way you want to. I note that your description seem to indicate that you are doing this from a user prompt. But, you don't show any error messages like I get when I try the commands you listed from a user prompt. Does it work any differently if you do the commands with sudo?

Edit: Excuse me, I just noticed your posting history. Welcome to the forum! As a new user, you may want to have a look at this.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by luvshines on 2010-10-15
> **hypermorph said:**
> Well. thanks for your answer. But that didn't solve my problem. I want to do it the other way, and if it is possible I want to know what I'm doing wrong (if I'm doing something wrong) and the right way to do it.

Thanks

From useradd man pages:
```
-m, --create-home
Create the users home directory if it does not exist. The files and directories 
contained in the skeleton directory (which can be defined with the -k option) 
will be copied to the home directory.
**By default, no home directories are created.**
```

I checked it too, if there is no home directory initially, usermod -md will not create any new one either

---

### Post by hypermorph on 2010-10-15
QLee, first of all, thanks for your help. And, it's true, I was writing fast and didn't add the sudo to the description of the commands, but I really was doing it with sudo. There´s no other way, because using the normal account, I get a message about the impossibility to unlock the etc/passwd file or a message stating 'no change'.

luvshines, thanks for your help, too. I still don't know if there's something I'm not doing well. If I create the directory by hand and later I want to remove the user account, the shell removes the acccount, but not the directory (a message says that the directory is not the user's directory), but my /etc/passwd file shows it is.

Thanks. Bye

Fran
-----

---

### Post by luvshines on 2010-10-15
> **hypermorph said:**
> 
luvshines, thanks for your help, too. I still don't know if there's something I'm not doing well. If I create the directory by hand and later I want to remove the user account, the shell removes the acccount, but not the directory (a message says that the directory is not the user's directory), but my /etc/passwd file shows it is.

Thanks. Bye

Fran
-----

Who is the owner of the directory when you create it manually ?

You delete account with 'userdel -r <user-name>' ?

---

### Post by luvshines on 2010-10-15
I would suggest adding a new user with 'useradd -m' then delete it with 'userdel -r' and see if it still gives the error

---

### Post by sandyd on 2010-10-15
> **hypermorph said:**
> QLee, first of all, thanks for your help. And, it's true, I was writing fast and didn't add the sudo to the description of the commands, but I really was doing it with sudo. There´s no other way, because using the normal account, I get a message about the impossibility to unlock the etc/passwd file or a message stating 'no change'.

luvshines, thanks for your help, too. I still don't know if there's something I'm not doing well. If I create the directory by hand and later I want to remove the user account, the shell removes the acccount, but not the directory (a message says that the directory is not the user's directory), but my /etc/passwd file shows it is.

Thanks. Bye

Fran
-----
you need to chown it.
For example, if the user is called "john" and the home directory you created is "/home/john"
then
```

sudo chown john /home/john
```

---

### Post by luvshines on 2010-10-15
> **sandyd said:**
> you need to chown it.
For example, if the user is called "john" and the home directory you created is "/home/john"
then
```

sudo chown john /home/john
```

Should not it be
```

sudo chown john:john /home/john

```

---

### Post by sandyd on 2010-10-15
> **luvshines said:**
> Should not it be
```

sudo chown john:john /home/john

```
depends on if he creates a matching group for the user
the syntax is 
```

sudo user:user_group /home/user
```
so it doesn't really matter wether or not he puts the group afterwprds

---

### Post by sisco311 on 2010-10-15
> **sandyd said:**
> depends on if he creates a matching group for the user
the syntax is 
```

sudo user:user_group /home/user
```
so it doesn't really matter wether or not he puts the group afterwprds

I would use the:
```
chown user: /path/to/home
```
syntax.

from **man chown**
> If a colon but no group name follows the user name, that user is made the owner of the files and the group of the files  is  changed  to that user's  login  group.

---

### Post by sandyd on 2010-10-15
> **sisco311 said:**
> I would use the:
```
chown user: /path/to/home
```syntax.

from **man chown**
ooh.  neat trick
thx!

---

