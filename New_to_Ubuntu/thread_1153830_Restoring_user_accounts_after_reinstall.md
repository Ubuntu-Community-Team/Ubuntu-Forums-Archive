---
title: "Restoring user accounts after reinstall"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by neotasic1 on 2009-05-09
Hi all,
Just a quick question to the gurus out there. I have just installed Jaunty over a previous Intrepid install with a separate home partition and multiple accounts . This restores most of my own account settings, but doesn't restore the other user accounts and files although they are still there in the home folder. I have managed to restore all these in the past, but can't remember how I did it. 
Using the graphical user management will not recreate the same user name and user id - gives an error message. I can create another user name with the same user id, then copy all the files across but this then means the username is different. Is there an easy way (CLI is ok) to achieve what I want - that is to recreate the user accounts and assign all the appropriate file and folder ownerships and permissions without the clumsy workaround?:confused:****

---

### Post by spiderbatdad on 2009-05-09
check the ownerships of the current accounts by changing to /home and ls -al```
cd /home
ls -al
```

---

### Post by neotasic1 on 2009-05-09
> **spiderbatdad said:**
> check the ownerships of the current accounts by changing to /home and ls -al```
cd /home
ls -al
```

Thanks for the response - I got that, but how do I re-create those users accounts so they can log in and access all their files and folders?

---

### Post by spiderbatdad on 2009-05-09
do you need to re-create the accounts? Are the accounts listed but with wrong ownerships or permissions?
For example I have these accounts...not really::popcorn: Don't post your user account names:
```
localhost: /home$ ls -al
total 28
drwxr-xr-x  7 root         root         4096 2009-04-15 07:51 .
drwxr-xr-x 22 root         root         4096 2009-04-26 07:04 ..
drwxr-xr-x 27 Tom          Tom          4096 2008-11-23 13:26 TOM
drwxr-xr-x 93 Dick         Dick         4096 2009-05-09 06:49 Dick
drwxr-xr-x  2 nagios       nagios       4096 2009-04-15 08:50 nagios
drwxr-xr-x 11 Harry        Harry        4096 2008-11-29 13:05 Harry
Sat May 09
localhost: /home$ 

```

---

### Post by neotasic1 on 2009-05-09
> **spiderbatdad said:**
> do you need to re-create the accounts? Are the accounts listed but with wrong ownerships or permissions?

I can log in as previously, but the other users can't. They have no separate login accounts at this stage, although their files are intact in the home directory. If I try to add them to the users, using their previous username and user id graphically from System>Administration>Users and Groups it will generate the error message:- "home directory already exists". Basically, by installing with a separate home partition, my login, all my files and folders, and most of my setup is intact - not so for other users without further work being required.

---

### Post by spiderbatdad on 2009-05-09
I am trying to ask 2 simple questions. Do your user account show they are owned by the users, and are the permissions correct. The answers are yes or no...not repeated explanantions of how users can't log in.

---

### Post by neotasic1 on 2009-05-09
> **spiderbatdad said:**
> I am trying to ask 2 simple questions. Do your user account show they are owned by the users, and are the permissions correct. The answers are yes or no...not repeated explanantions of how users can't log in.


Apologies, but it seems I am being unclear. here is the output of ls -al (usernames changed)

 
joe@sevenofnine:/home$ ls -al
total 44
drwxr-xr-x  8 root      root       4096 2009-05-09 20:09 .
drwxr-xr-x 22 root      root       4096 2009-05-08 10:57 ..
drwxr-xr-x 41      1004      1002  4096 2009-04-12 12:58 mike
drwxr-xr-x 49 janie     janie      4096 2009-05-09 19:59 janie
drwx------  2 root      root      16384 2008-11-21 16:26 lost+found
drwxr-xr-x 78 joe       joe        4096 2009-05-09 19:17 joe
drwxr-xr-x 40      1005      1003  4096 2009-04-29 15:26 stan
drwx------  4 root      root       4096 2009-05-09 20:09 .Trash-0
joe@sevenofnine:/home$ 

user joe is me, user janie used to be janie1. I added janie as the user in the users and groups menu, used the same user id as janie1, logged in to janie, navigated to home/janie1 folder, copied all files including hidden to home/janie. this worked as janie has access to all her files and folders, but now has to log in using janie rather than janie1 as username.

This seems a clumsy way to restore user accounts and file ownership and I am looking for a simpler way that is transparent to the other users.

the other two users were mike and stan with the user ids of 1004 and 1005. I am wondering how to recreate mike and stan's user accounts and restore ownership of their files.

---

### Post by spiderbatdad on 2009-05-09
ok this should restore user logins```
cd /home
sudo chown -R mike:mike mike
```for example. To fix janie. it sounds like you would do: ```
sudo chown -R janie1:janie1 janie
```

Then try making passwords```
sudo passwd mike
```enter your password for sudo, if necessary...then the new unix password for mike...twice.

---

### Post by neotasic1 on 2009-05-09
[QUOTE=spiderbatdad;7244817]ok this should restore user logins[CODE]cd /home
sudo chown -R mike:mike mike


Ok, just tried that but get this error message:-

chown: invalid user: `mike:mike'

Don't I have to create user mike first? And if so how via command line?

---

### Post by theozzlives on 2009-05-09
The best I've come up with is to backup & delete the folder, create acct, restore folder. That's what I've done in the past, remember to chown and chmod it to work right.

---

### Post by spiderbatdad on 2009-05-09
```
sudo adduser mike
```

actually since the /home/mike exists...I would do

```
sudo useradd mike
chown -R mike:mike mike
sudo passwd mike 
```

---

### Post by CatKiller on 2009-05-09
> **neotasic1 said:**
> Is there an easy way (CLI is ok) to achieve what I want - that is to recreate the user accounts and assign all the appropriate file and folder ownerships and permissions without the clumsy workaround?:confused:

CLI is probably more flexible for what you want to achieve.

**adduser** is probably what you want to use. You can specify the name, UID and Home folder for each new user, which is pretty much what you need to do, since you have an existing setup that you want to re-create.

I haven't used it, so I can't give you a handy command to put in, but **man adduser** should tell you what you need to know.

---

### Post by neotasic1 on 2009-05-09
> **spiderbatdad said:**
> ```
sudo adduser mike
```

actually since the /home/mike exists...I would do

```
sudo useradd mike
chown -R mike:mike mike
sudo passwd mike 
```

Perfect!!!! The second block is exactly what I wanted. Thanks for your patience and help. Will mark this solved.

---

### Post by spiderbatdad on 2009-05-09
a pleasure helping you.:P

---

### Post by albinootje on 2009-05-09
> **neotasic1 said:**
> [QUOTE=spiderbatdad;7244817]ok this should restore user logins```
cd /home
sudo chown -R mike:mike mike


Ok, just tried that but get this error message:-

chown: invalid user: `mike:mike'

Don't I have to create user mike first? And if so how via command line?

It makes sense to look at the uid in /home/
Let's assume that user mike had uid 1003 in the past, then you can do :
[code]
sudo adduser --disabled-password --disabled-login --uid 1003 mike

```

After you've done so for all your users, fire up the "Users and Groups" from -> System -> Administration, and set the passwords and the groups needed.

---

### Post by theozzlives on 2009-05-09
> **neotasic1 said:**
> [QUOTE=spiderbatdad;7244817]ok this should restore user logins```
cd /home
sudo chown -R mike:mike mike


Ok, just tried that but get this error message:-

chown: invalid user: `mike:mike'

Don't I have to create user mike first? And if so how via command line?

[CODE]sudo mkdir /home/temp
```
```
cd /home/temp
```
```
sudo mv /home/mike/* ./
```
```
sudo rm -rf /home/mike
```
```
sudo adduser mike
```
```
cd /home/mike
```
```
sudo mv /home/temp/* ./
```
```
sudo chown mike:mike /home/mike -R
```
```
sudo chmod 755 /home/mike
```
```
sudo chmod 644 /home/mike/.dmrc
```

---

### Post by albinootje on 2009-05-09
Remember that "adduser mike" will not put user mike in any specific group.
For sounds the user needs to be in group audio for example.

---

### Post by neotasic1 on 2009-05-09
> **albinootje said:**
> [QUOTE=neotasic1;7244844]

It makes sense to look at the uid in /home/
Let's assume that user mike had uid 1003 in the past, then you can do :
```

sudo adduser --disabled-password --disabled-login --uid 1003 mike

```


Thanks for your input, but unfortunately this generates the same problem I encountered with the graphical way of doing it, basically it will generate an error message that /home/mike already exists. The solution offered by spiderbatdad gets around this and works perfectly.

Thanks again to all.

---

### Post by albinootje on 2009-05-09
> **neotasic1 said:**
> [QUOTE=albinootje;7244896]
unfortunately this generates the same problem I encountered with the graphical way of doing it, basically it will generate an error message that /home/mike already exists. 

Okay, this is better in that case.
```

sudo adduser --no-create-home --disabled-password --disabled-login --uid 1003 mike

```
Good that you solved it! :) 
And remember to add the groups for the users that you want them to use.

---

