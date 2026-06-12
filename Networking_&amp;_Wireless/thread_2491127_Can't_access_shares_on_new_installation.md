---
title: "Can't access shares on new installation"
date: 2023-09-26
forum: Networking &amp; Wireless
---

### Post by peyre on 2023-09-26
(Sorry, I accidentally overwrote my OP here.  I'll recreate the broad strokes.)

I had to wipe my drive and reinstall from scratch, and now my shares aren't accessible.  I installed samba and added the lines below to /etc/samba/smb.conf.  I even ran **sudo smbpasswd -a leon** and made the credentials match those to log into my desktop here.  Yet neither our Windows 10 desktop (on ethernet) or my Linux laptop can access them.  They demand credentials then reject them when I supply them.

> [HomeFolder]
comment = Home folder share
path = /home/leon
read only = no
browsable = yes
guest ok = no
writable = yes
create make = 0644
directory mask = 0755
valid users = %S
min protocol = SMB3

[Storage]
comment = Storage share
path = /media/Storage
read only = no
browsable = yes
guest ok = no
writable = yes
create make = 0644
directory mask = 0755
valid users = %S
min protocol = SMB3 

---

### Post by Morbius1 on 2023-09-27
In both cases the problem is your use of:
> valid users = %S

The %S parameter refers to the name of the service ( share name ). It is used in a [homes] share where the share name = the user name of the user who owns his home folder.

The way you are using it the only user that can access the [HomeFolder] share for example is literally the user HomeFolder which doesn't exist.

Remove the valid users = %S line and restart smbd: ```
sudo service smbd restart

```
Or, explicitly state the valid users you want to allow access:

valid users = leon

***[COLOR="#FF0000"]Side notes:[/COLOR]***

[1] You have a typo in your share definitions: It's **[COLOR="#0000CD"]create mask[/COLOR]** not **[COLOR="#B22222"]create make[/COLOR]**

[2] The **[COLOR="#B22222"]min protocol[/COLOR]** in is the wrong place and is being ignored. It doesn't really matter since the min will default to SMB2.1 anyway.

[3] Any time you edit smb.conf I suggest you run the following command that will test for any syntax errors:
```
testparm -s
```

---

### Post by peyre on 2023-09-27
That worked!  Thanks!

---

