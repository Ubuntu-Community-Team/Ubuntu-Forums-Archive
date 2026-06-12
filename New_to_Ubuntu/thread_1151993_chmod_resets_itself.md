---
title: "chmod resets itself"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by buddykadri on 2009-05-07
Hello

I would like to allow anyone on my internal network (using Win XP) to read/write/execute any files within a folder called /storage on my ubuntu 8.04, so I do:

sudo chmod -R 777 /storage

this works but only for a little while and I can't figure out why :( ! How do I make this a permanently?

Thanks

---

### Post by cmnorton on 2009-05-07
Is this directory being mounted (/etc/fstab) or shared out through samba?

---

### Post by bodhi.zazen on 2009-05-07
Sounds as if you are using samba.

Are you asking about permissions on the server or on the client ?

[Samba Server]("https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html#id2540411")

---

### Post by buddykadri on 2009-05-07
> **bodhi.zazen said:**
> Sounds as if you are using samba.

Are you asking about permissions on the server or on the client ?

[Samba Server]("https://help.ubuntu.com/5.10/ubuntu/faq/C/sect-samba-server.html#id2540411")

Hello cmn, Samba Server

Yes I am using Samba. The PC with Ubuntu is the file server and I am trying to read/write/execute by windows XP. The only way I seem to be achieve this is by rebooting my ubuntu server then sudo chmod 777 again. Help .. this is driving me nuts :confused:

---

### Post by bodhi.zazen on 2009-05-07
Well, execute is different for files and directories ;)

At any rate, I am guessing you need to configure your share properly.

See :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Probably something like :

```
[your_share_name_goes_here][FONT=monospace]
[/FONT]
comment = Put any comments you wish here[FONT=monospace]
[/FONT]path = /full/path-to/yoru_share
read only = no
create mask = 0666[FONT=monospace]
[/FONT]directory mask = 0777
```The create mask is for files, directory is for directories. You can use 644 and 755 if you want to be more secure.

---

### Post by buddykadri on 2009-05-08
I believe that I did configure my Ubuntu server shared options correctly as per [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Interestingly I may getting somewhere... I found a way to overcome this problem but it is not an elegant one: I am not able to modify or add new files to a sub folder if I go directly to it (for example through mounting a network drive on windows XP) UNLESS I go via the top folder and pretend to put (ie: add then delete) a file or folder in it! For example, within a shared folder structure of /files/storage/2009/ I wouldn't be able to go to /files/storage/2009 and add or modify within unless I first add and delete a new folder in /files. I can't understand why this is so..

I then figured out that the add/delete bit in the top directory is not necessary, it is just me testing if it works..

---

