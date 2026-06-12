---
title: "rsync help"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by jquis8411 on 2010-10-14
I have a desktop/file server with one HDD that has the Ubuntu on it and a second HDD I would like to use for backing up the various laptops floating around my house. I can use rsync and ssh to backup to the primary HDD no problem, however, I cant figure out how to backup to the second HDD. Ive tried mounting it in various different places and I cant seem to get around the fact that rsync cant get permission to make a directory to write to. Any help would be great TY.

---

### Post by baddnady23 on 2010-10-14
post the command that you are using when trying to backup

---

### Post by jquis8411 on 2010-10-14
```
 joe@joe-desktop:~$ rsync -h --progress --stats -r -tgo -l -p -D --update --delete-after --delete-excluded --exclude **/*trash*/ -e "ssh -i /home/joe/.ssh/id_dsa.pub -p22" /home/joe joe@192.168.1.104:/home/sda1
```

I just threw /home/ as an example, I get the same issue when I use /mnt, / I'm kinda at a loss TY

---

### Post by CharlesA on 2010-10-14
What file system is the second hard drive?

Try this after it's mounted:

```
rsync -ai source destination
```

---

### Post by jquis8411 on 2010-10-14
its ext4 right now but its empty other than the one partition and the file system so its nothing to change it if it would make life easier

---

### Post by jquis8411 on 2010-10-14
here is the error I get in case it helps. rsync: recv_generator: mkdir "/home/sda1/joe" failed: Permission denied (13). I tried using chmod to change the permissions on a directory I made specifically for a destination but either I didnt use it correctly or it just  didnt work because  rsync fails as it tries to write a folder "joe"

---

### Post by CharlesA on 2010-10-15
It really sounds like a permissions issue.

Can you do ls -ld /path/to/mountpoint ?

---

### Post by jquis8411 on 2010-10-15
Here you go..
drwxr-xr-x 4 root root 4096 2010-10-14 19:29 /sda1

I'm not sure if it's good to be mounted on / but I was trying everything, Thanks

---

### Post by jquis8411 on 2010-10-15
> **CharlesA said:**
> What file system is the second hard drive?

Try this after it's mounted:

```
rsync -ai source destination
```

I just noticed this sorry, how should I enter my source? I am on the source comp now and I am ssh into the host.

---

### Post by amac777 on 2010-10-15
> **jquis8411 said:**
> Here you go..
drwxr-xr-x 4 root root 4096 2010-10-14 19:29 /sda1

I'm not sure if it's good to be mounted on / but I was trying everything, Thanks

Try adding write access to the drive for all users:

```
sudo chmod 777 /sda1
```

After that you should be able to make new directories and copy files within /sda1.

---

### Post by CharlesA on 2010-10-15
> **jquis8411 said:**
> I just noticed this sorry, how should I enter my source? I am on the source comp now and I am ssh into the host.

It should be:

```
rsync -ai /path/to/source user@host:/path/to/destination
```

---

### Post by jquis8411 on 2010-10-15
Thank you amac for helping me get the permission changed.just entering 777 is much easier then messing with the letters for that, and thank you CharlesA for the much simpler rsync code. now if I wanted to exclude trash would rsync -ai --exclude /trash  /pathto/blah/blah joe@blah/blah work? sorry for the silly questions, I'm still trying to figure out the syntax aspect of the CLI.

---

### Post by CharlesA on 2010-10-15
Yep. That's the way to exclude a folder. :)

You have to have the colon after the hostname for it to know where to put the files.

```
rsync -ai --exclude /trash /pathto/blah/blah joe@blah:/blah
```

---

### Post by jquis8411 on 2010-10-15
Perfect, thanks CharlesA and Ill try to remember the colon : ). All the help is greatly appreciated.

---

