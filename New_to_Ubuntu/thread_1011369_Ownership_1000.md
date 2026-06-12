---
title: "Ownership 1000"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by RealG187 on 2008-12-14
I have a few directories in my home directory that say "1000" under owner. I think a few are from when I moved the contents of my old home directory to my new one when I made a new account and deleted the old one. Also I have a few directories I put on from a Windows machine usinf EXT2IFS.

If I goto change the owner of the directory to me, any subfolders still say "1000" as the owner and it's unpractical to do this to every subdirectory in my home folder.

How can I make it so that I am the owner of all the files/directories in my home folder?

---

### Post by sisco311 on 2008-12-14
type:
```
sudo chown -R $USER\: $HOME
```
in a terminal.

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by dwasifar on 2008-12-14
From the commandline:

```
sudo chown -R {username}:{groupname} /home/{username}/
```

Replace {username} and {groupname} with your username and the group you would like the files to belong to, usually this is the same as your username.  The R means "recursive" and will act on all the contents of the directory as well as the directory itself.

---

### Post by RealG187 on 2008-12-14
```
sudo chown -R $USER\: $HOME
```

Gives this

> xg@MIKED5:~$ sudo chown -R $USER\: $HOME
[sudo] password for xg: 

chown: cannot access `/home/xg/.gvfs': Permission denied



and for 
```
sudo chown -R {username}:{groupname} /home/{username}/
```
What would groupname be?

---

### Post by dwasifar on 2008-12-14
groupname will usually be the same as your username.  

So if your username is, say, "snoop," the command will be:

```
sudo chown -R snoop:snoop /home/snoop/
```

---

### Post by sisco311 on 2008-12-14
> **RealG187 said:**
> ```
sudo chown -R $USER\: $HOME
```

Gives this

You can ignore that error message.

Check in nautilus if the command worked.

---

### Post by RealG187 on 2008-12-14
> **sisco311 said:**
> You can ignore that error message.

Check in nautilus if the command worked.

I think it actually worked, despite the error. Thanks.

---

### Post by sisco311 on 2008-12-14
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by RealG187 on 2009-01-20
Okay I that and I am the owner, but I also need a command to quikly set it so I can set my permissiosn to read and write, when I write files from windows, the permissions are set so I can only open files and not rename/edit/delete, I can do this manually, but once again that could be tedious...

---

### Post by mrbiggbrain on 2009-01-20
> **RealG187 said:**
> Okay I that and I am the owner, but I also need a command to quikly set it so I can set my permissiosn to read and write, when I write files from windows, the permissions are set so I can only open files and not rename/edit/delete, I can do this manually, but once again that could be tedious...

look up the chmod command on google, i belive thats the one.

---

### Post by cariboo on 2009-01-20
You can set read/write permissions by running in a terminal:

```
sudo chmod -R 755 /home/<user>
```

where <user> is your user name. NTFS can't set specific owner and read/write permissions.

Jim

---

### Post by RealG187 on 2009-01-22
> **cariboo907 said:**
> You can set read/write permissions by running in a terminal:

```
sudo chmod -R 755 /home/<user>
```

where <user> is your user name. NTFS can't set specific owner and read/write permissions.

Jim

Thanks, I think that did it. I was wondering let's say I had the terminal already in my home directory (it is when you start it) could I just type ```
sudo chmod -R 755
```?

---

