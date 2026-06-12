---
title: "Smb write issues for a single user"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by Andy_Martin on 2014-08-06
Hi everyone,

I've finally had to finally resort to posting a plea for help on the forum! I've managed many years without doing so, using other people's posts and answers to figure out what I've done wrong, but this time I'm really stuck!!!

I'm attempting to share a folder from my media centre to the rest of the network. However I only want two authorised users to be able to write to it and everyone else gets read. The folder is simply to store our family pictures, etc and so I only want trusted accounts to be able to modify the files. We often have friends over, and I'm not 100% sure how clean their Windows machines are! I work in the AV industry, so I've seen what happens when it goes wrong!

Anyway, I ramble! So I've got two Unix accounts, andy and sara which are both members of the sambashare group. The folder to be shared is under /media/Pictures and my smb.conf file is configured as follows (abridged version):

```

[global]
security = user
workgroup = WORKGROUP


[Pictures]
comment = Personal Pictures
path = /media/Pictures
browsable = yes
write list = @sambashare
valid users = @sambashare
guest ok = no
admin users = andy
read only = no
create mode = 0664
directory mode = 2775
```

The folder can be read and written to by both accounts, andy and sara (tested via su and a terminal). The share works fine when logging on with 'andy' and I can read and write to the files without any problems, however it does not work for sara. She can access the share and read it's contents, but cannot write anything to it, not even to a folder/file with her direct permissions on it (or set to 777).

The permissions on the Pictures folder are:
```
drwxrwsr-x  22 andy sambashare 4096 Aug  5 21:34 Pictures
```

And looking down the list of folders within the share the following is set:
```
andy@media:/media/Pictures$ ls -l
total 244
drwxrwsr-x 13 andy sambashare   4096 Mar  1 03:02 2011
drwxrwsr-x 14 andy sambashare   4096 Aug  4 12:09 2012
drwxrwsr-x 14 andy sambashare   4096 Dec 25  2013 2013
drwxrwsr-x 10 andy sambashare   4096 Aug  4 12:04 2014
drwxrwsr-x  2 andy sambashare   4096 Jun 24 15:20 Scanned
drwxrwsr-x  3 sara sambashare   4096 Aug  5 21:30 test
drwxrwsrwx 16 sara sambashare   4096 Aug  2 16:18 To print
drwxrwsrwt 20 andy sambashare   4096 Aug  5 21:12 To sort

```



Looking at the Unix group memberships for both users:
```
andy@media:/media/Pictures$ groups
andy adm cdrom sudo dip plugdev lpadmin sambashare mythtv

sara@media:/media/Pictures$ groups
sara adm sudo lpadmin sambashare
```

At this rate I'm thinking of sharing it with guest and then using the Unix permissions to prevent anyone but andy or sara from writing to it, but I don't really want to have to do it that way if I can help it. I'll feel that I'm missing something stupid, so any pointers, things to check, help would be greatly appreciated.

Many thanks in advance,
Andy

---

### Post by bab1 on 2014-08-06
> **Andy_Martin said:**
> Hi everyone,

I've finally had to finally resort to posting a plea for help on the forum! I've managed many years without doing so, using other people's posts and answers to figure out what I've done wrong, but this time I'm really stuck!!!

I'm attempting to share a folder from my media centre to the rest of the network. However I only want two authorised users to be able to write to it and everyone else gets read. The folder is simply to store our family pictures, etc and so I only want trusted accounts to be able to modify the files. We often have friends over, and I'm not 100% sure how clean their Windows machines are! I work in the AV industry, so I've seen what happens when it goes wrong!

Anyway, I ramble! So I've got two Unix accounts, andy and sara which are both members of the sambashare group. The folder to be shared is under /media/Pictures and my smb.conf file is configured as follows (abridged version):

```

[global]
security = user
workgroup = WORKGROUP


[Pictures]
comment = Personal Pictures
path = /media/Pictures
browsable = yes
write list = @sambashare
valid users = @sambashare
guest ok = no
admin users = andy
read only = no
create mode = 0664
directory mode = 2775
```

The folder can be read and written to by both accounts, andy and sara (tested via su and a terminal). The share works fine when logging on with 'andy' and I can read and write to the files without any problems, however it does not work for sara. She can access the share and read it's contents, but cannot write anything to it, not even to a folder/file with her direct permissions on it (or set to 777).

The permissions on the Pictures folder are:
```
drwxrwsr-x  22 andy sambashare 4096 Aug  5 21:34 Pictures
```

And looking down the list of folders within the share the following is set:
```
andy@media:/media/Pictures$ ls -l
total 244
drwxrwsr-x 13 andy sambashare   4096 Mar  1 03:02 2011
drwxrwsr-x 14 andy sambashare   4096 Aug  4 12:09 2012
drwxrwsr-x 14 andy sambashare   4096 Dec 25  2013 2013
drwxrwsr-x 10 andy sambashare   4096 Aug  4 12:04 2014
drwxrwsr-x  2 andy sambashare   4096 Jun 24 15:20 Scanned
drwxrwsr-x  3 sara sambashare   4096 Aug  5 21:30 test
drwxrwsrwx 16 sara sambashare   4096 Aug  2 16:18 To print
drwxrwsrwt 20 andy sambashare   4096 Aug  5 21:12 To sort

```



Looking at the Unix group memberships for both users:
```
andy@media:/media/Pictures$ groups
andy adm cdrom sudo dip plugdev lpadmin sambashare mythtv

sara@media:/media/Pictures$ groups
sara adm sudo lpadmin sambashare
```

At this rate I'm thinking of sharing it with guest and then using the Unix permissions to prevent anyone but andy or sara from writing to it, but I don't really want to have to do it that way if I can help it. I'll feel that I'm missing something stupid, so any pointers, things to check, help would be greatly appreciated.

Many thanks in advance,
Andy

if you use Samba *guest ok = yes* all files will be created as the user *nobody* with the group as *nogroup*.  This really doesn't help you in your situation at all.  even if you used *force group = sambshare* you won't get whet you want.

What is the permissions on the /media and /media/Pictures directories?  I would not use Samba to cure basic Linux user rights.  Think of Samba as handling the authentication (who are you?) and the Linux permission as the authorization (what are you allowed to do).

I know ow many who would say just chmod everything 777 and use Samba force user, but I believe that this will ultimately bite you in the end some day.

---

### Post by Andy_Martin on 2014-08-07
[FONT=arial]Hi BAB,

Thanks for the reply, the permissions on /media/Pictures is:[/FONT]
drwxrwsr-x  22 andy sambashare 4096 Aug  5 21:34 Pictures

[FONT=arial]I don't have access to the server atm to find the permissions on the /media directory, but it should just be the default Ubuntu set - although I will confirm when I'm able to.

Really it boils down to:
1. Smb auth is working - sara can log into the share
2. Unix permissions on the directory should be OK, since locally sara can write to the folder

It's only when logging in through samba as sara can I not write to the share. I must have done something wrong somewhere, but I'm not sure if it's samba itself or the file/folder permissions. As you say, I don't really want to do 777 or force user, it kind of defeats the object. I shall check the permissions on the directories and get back to you.

Cheers again

[/FONT]

---

### Post by Andy_Martin on 2014-08-07
Part 2:

Permissions on /media are:
drwxr-xr-x   9 root root  4096 Jul 20 10:28 media

---

### Post by bab1 on 2014-08-07
> **Andy_Martin said:**
> [FONT=arial]Hi BAB,

Thanks for the reply, the permissions on /media/Pictures is:[/FONT]
```
drwxrwsr-x  22 andy sambashare 4096 Aug  5 21:34 Pictures
```

[FONT=arial]I don't have access to the server atm to find the permissions on the /media directory, but it should just be the default Ubuntu set - although I will confirm when I'm able to.

Really it boils down to:
1. Smb auth is working - sara can log into the share
2. Unix permissions on the directory should be OK, since locally sara can write to the folder

It's only when logging in through samba as sara can I not write to the share. I must have done something wrong somewhere, but I'm not sure if it's samba itself or the file/folder permissions. As you say, I don't really want to do 777 or force user, it kind of defeats the object. I shall check the permissions on the directories and get back to you.

Cheers again

[/FONT]

Part 2:

Permissions on /media are:
```
drwxr-xr-x 9 root root 4096 Jul 20 10:28 media
```

My mistake.  Missed the part about sara being able to write to the shared directory when local.  When you use Windows sharing (Samba) you are actually mounting the remote resource (the share) to the local machine (the client).  I would see what the permissions are at the client for sara vs your mount of the same share.

The directory above the share (/media) looks okay.  The eXecute bit set on directories allows the user to traverse that directory.  That is;  see the directory listings and the sub directories).  There is an eXecute bit set for all users(root:root:others).  So we are good there.

Also you have the sgid bit set so the group is always the inherited from the directory group owner.

In looking at my own multiple user shares I see I have a note about using *create mode* causing problems.  I use this instead```
        create mask = 0664

```... I know it's subtle, but it is the only thing I can see from the Linux side.  *After checking the client side permissions* for correctness, you might try to simplify the parameters to something like this  ```

[Pictures]
comment = Personal Pictures
path = /media/Pictures
browsable = yes

guest ok = no

read only = no
create mask = 0664
directory mode = 2775

```...This should rely only on the Linux file permissions.

---

### Post by Andy_Martin on 2014-08-08
Thanks BAB1, 

I'll give that a try tonight and see what happens. Will let you know.

---

### Post by Andy_Martin on 2014-08-11
Thanks BAB1,

I've tried that, but it's still failing when connecting as sara. My smb.conf file (extract) looks like the following:

[FONT=system][Pictures]
comment = Personal Pictures
path = /media/Pictures
browsable = yes
guest ok = no
read only = no
create mask = 0664
directory mode = 2775
[/FONT]
Just  in case I didn't mention, the clients I'm testing with are another  14.04 connecting via dolphin (smb://sara@media/Pictures/) and a Windows 7  machine. Any more ideas or things to try would be greatly appreciated.

Thanks
Andy

---

### Post by bab1 on 2014-08-11
> **Andy_Martin said:**
> ...
Just  in case I didn't mention, the clients I'm testing with are another  14.04 connecting via dolphin (smb://sara@media/Pictures/) and a Windows 7  machine. Any more ideas or things to try would be greatly appreciated.

Thanks
Andy
From the remote Linux host (remote from the Samba server) post the output of this command```
smbclient \\\\media\\Pictures -U Sara -d3
```

If you get a prompt like this```
smb: \>
```...then you have successfully logged in.

You can exit the SMB: \> prompt with the command: exit.

It's been so long and I've been busy so correct me if I'm wrong, but if the user can log in then the permissions on the share determine whether you have rw rights.  Are you sure that the user is in the group.  Post the output of ```
getent group sambashare
```

As a test set sara as the owner of the directory ```
sudo chown sara:sambashare /media/Pictures
```
Since both of you should be in that group the share should operate the same regardless of who is the owner of the directory,

---

### Post by Andy_Martin on 2014-08-14
Hi BAB1,

Appreciate the continued help :)

1. smbclient from my Kubuntu client works fine and connects leaving me at the smb prompt.
2. Running the getent group command on the media server shows the following:

```
andy@media:~$ getent group sambashare
sambashare:x:124:andy,sara
```

3. I've run the chown command and confirmed that the ownership has been applied:

```
andy@media:/media$ ls -l
total 22
drwxrwsr-x  22 sara sambashare 4096 Aug 11 21:22 Pictures
```

Unfortunately I still cannot write to the share as sara, but can still write as andy. 

I have created a new user cunningly called 'test' and add it to the sambashare group and user smbpasswd to add it to samba. I can login, but again I cannot write via the share, but can write locally:

```
test@media:/media$ groups 
Test sambashare
test@media:/media$ cd Pictures/
test@media:/media/Pictures$ touch testfile.txt
test@media:/media/Pictures$ ls test*
testfile.txt
```

Something odd is happening within smb, it's like it's not mapping the smb user to the local user account? Are there some settings around this that I could look at?

Thanks BAB1,
Andy

---

### Post by bab1 on 2014-08-14
> **Andy_Martin said:**
> Hi BAB1,

Appreciate the continued help :)

1. smbclient from my Kubuntu client works fine and connects leaving me at the smb prompt.
2. Running the getent group command on the media server shows the following:

```
andy@media:~$ getent group sambashare
sambashare:x:124:andy,sara
```

3. I've run the chown command and confirmed that the ownership has been applied:

```
andy@media:/media$ ls -l
total 22
drwxrwsr-x  22 sara sambashare 4096 Aug 11 21:22 Pictures
```

Unfortunately I still cannot write to the share as sara, but can still write as andy. 

I have created a new user cunningly called 'test' and add it to the sambashare group and user smbpasswd to add it to samba. I can login, but again I cannot write via the share, but can write locally:

```
test@media:/media$ groups 
Test sambashare
test@media:/media$ cd Pictures/
test@media:/media/Pictures$ touch testfile.txt
test@media:/media/Pictures$ ls test*
testfile.txt
```

Something odd is happening within smb, it's like it's not mapping the smb user to the local user account? Are there some settings around this that I could look at?

Thanks BAB1,
Andy
I've not had any problems with Samba (smbd).  I've not had any problems with Gnome Nautilus mounts of Samba shares.  KDE's file manger  to me is the big unknown here.

So let's use only the GVFS (Gnome Virtual File System).  You should be able to install Gigolo from the repos and use it to mount and manipulate the shares.  To install Gigolo use this command from the Ubuntu client CLI```
sudo apt-get install gigolo
```

When you open Gigolo you will find all the file manager tools from Nautilus at your disposal.  If this works then for sure the problem is with KDE's file manager.  Let me know how it works out.  I have other thoughts but I think we need to do this one step at a time.  We are diagnosing the problem as we go along here.

---

### Post by Andy_Martin on 2014-09-01
Will give it a try, but as mentioned I get the same problem from a Windows machine using explorer, so I doubt it's anything to do with the client-side software. 

Shall get back to you when I've had a chance to try it.

Thanks again BAB1

---

### Post by Andy_Martin on 2014-12-15
WOOT!

I've finally found the problem!

The share name was Pictures and the folder being shared was Pictures... apparently smb doesn't like it when you share something with the same name. Changing the share to [Picture] works perfectly.

Gah! Sometimes I hate working with Linux.

Thanks very much for your help BAB1, I hope you have a great Christmas.

---

