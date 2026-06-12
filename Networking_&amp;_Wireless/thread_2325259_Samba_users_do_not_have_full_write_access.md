---
title: "Samba users do not have full write access"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by jamarsh123 on 2016-05-20
Trying to set up a samba server on Ubuntu server with groups and users. Mostly working, but users don't seem to have correct write access. I can rename the file but not edit and save the changes. If I create a new file, the permissions are different.
Here is the smb.conf file:

```

[beaconFiles]
comment = beaconFiles Share
path = /srv/samba/beacon/beaconFiles
valid users = @beaconFiles
writeable = Yes
guest ok = no
create mask = 0777
directory mask = 0777
browseable = Yes
writeable = yes
#public = yes

[finance]
comment = finance Share
path = /srv/samba/beacon/finance
valid users = @finance
writeable = Yes
guest ok = no
create mask = 0777
directory mask = 0777

[foothills]
comment = foothills Share
path = /srv/samba/foothills
valid users = @foothills
read only = no
guest ok = no
writeable = yes
create mask = 0777
directory mask = 0777
browseable = Yes
#public = yes

```
Here is a view of the file permissions
```

drwxrwx--- 15 manager beaconFiles 4096 May 20 11:47 beaconFiles
drwxrwx---  6 manager finance     4096 Oct  7  2015 finance

```

---

### Post by bab1 on 2016-05-20
> **jamarsh123 said:**
> Trying to set up a samba server on Ubuntu server with groups and users. Mostly working, but users don't seem to have correct write access. I can rename the file but not edit and save the changes. If I create a new file, the permissions are different.

It's hard to tell exactly what you have going on here.  The ownership and permissions set when a file is created locally (by a Linux user) is determined by the User Private Groups (UPC) and the umask.  For Ubuntu this means <user>:<usergroup> for ownership (e.g. john:john or jane:jane or some such) with permissions of 775 for directories and 664 for files.  You never need to resort to 777 for and directory or file.  The X for directories allows the user to descend into the directory while th r allows the user to read the contents.  This means r-x (5) allows a user to read but not write to the contends of a directory.  This works for most global users (others).  There is absolutely no reason to allow a user the ability to create a eXecutable file in any shared directory.  Imagine if that logged in user created a script that when executed would delete all the files in the shared directory.

This is even worse for remote users of the shared directory.  Allowing  a remote user the ability to create malicious eXecutable scripts subverts all of the Linux security conventions.

This is more appropriate for a typical Linux file system that is going to be shared using Samba```
        create mask = 0664
        directory mask = 0775

``` 
If you want to limit the access to the owner and  user-group you can use this```
        create mask = 0660
        directory mask = 0770

```
You can set a directory user-group ownership to a user-group that contains multiple users, but you will need a method to "inherit" the user-group of that directory.  You can do that by setting th sgid bit.  I usually set the ownership first (chown) and then set the permissions (chmod) from the root of that file system (say /srv/samba/beacon) with this ```
chmod -R ug=rwX,o=rX  /srv/samba/beacon
```
Did you mean to create a separate file system branch at */srv/samba/foothils *?

Now all that is left is for you to set the sgid but with this command```
sudo chmod g+s /srv/samba/beacon
# Note the above is only needed on the root directory (the shared directory)
``` 
 > 
All of this should be done by the root user (via sudo).  It helps to do this in the order I described.  Things don't go well if you do don't follow the order of the commands.

Here is the smb.conf file:
To be honest, this is only part of the smb.conf.  Plenty can go wrong in the [global] section.  ;-)> 
```

[beaconFiles]
comment = beaconFiles Share
path = /srv/samba/beacon/beaconFiles
valid users = @beaconFiles
writeable = Yes
guest ok = no
create mask = 0777
directory mask = 0777
browseable = Yes
writeable = yes
#public = yes

[finance]
comment = finance Share
path = /srv/samba/beacon/finance
valid users = @finance
writeable = Yes
guest ok = no
create mask = 0777
directory mask = 0777

[foothills]
comment = foothills Share
path = /srv/samba/foothills
valid users = @foothills
read only = no
guest ok = no
writeable = yes
create mask = 0777
directory mask = 0777
browseable = Yes
#public = yes

```
Here is a view of the file permissions
```

drwxrwx--- 15 manager beaconFiles 4096 May 20 11:47 beaconFiles
drwxrwx---  6 manager finance     4096 Oct  7  2015 finance

```
The directory contents ownership and permissions is just as important as that if the parent directory's.

---

### Post by jamarsh123 on 2016-05-21
Hi bab1:
Thanks for your detailed response. I am going into the office to day to implement your suggestions. I will report back with the results.

Just a few answers to your questions. Re: file permissions. I will implement changes to remove executable. The file permissions were set recursively; that is why I posted just the top level. My smb.conf file was picked from some tutorial site, so I am guessing is generic, but I will post the global share as well.

I did mean to have 2 file system branches as there are actually 2 businesses under the same ownership and on the same server.

I suspect you identified my problem when you mentioned the sgid. This is new to me and I will have to investigate this further.
Regards,
jamarsh123

---

### Post by jamarsh123 on 2016-05-22
Something I forgot to mention before: All users in a group need to be able to access the same set of files, which also requires the need for file locking.
jamarsh123

---

### Post by bab1 on 2016-05-22
> **jamarsh123 said:**
> Something I forgot to mention before: All users in a group need to be able to access the same set of files, which also requires the need for file locking.
jamarsh123
This is built into Samba.  There are some tuneable parameters if needed.  The mount options (via script or fstab) will set most of what you need.

---

### Post by jamarsh123 on 2016-05-23
I have made the changes you suggested. Here is the latest version of the shares in smb.conf, including global
```

[beaconFiles]
comment = beaconFiles Share
path = /srv/samba/beacon/beaconFiles
valid users = @beaconFiles
writeable = Yes
guest ok = no
create mask = 0660
directory mask = 0770
browseable = Yes
write list = maindesk frontdesk guy john spa
#public = yes

[finance]
comment = finance Share
path = /srv/samba/beacon/finance
valid users = @finance
writeable = Yes
guest ok = no
create mask = 0660
directory mask = 0770
write list = maindesk guy john spa
directory mask = 0770

[foothills]
comment = foothills Share
path = /srv/samba/foothills
valid users = @foothills
writeable = yes
guest ok = no
create mask = 0660
directory mask = 0770
write list = maindesk guy john spa spa2
browseable = Yes

[global]
   workgroup = WORKGROUP
   create mask = 0644
   directory mask = 0755
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 100
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

```
Also, I have set the group sticky bit recursively for all three of the group folders. The problem at present is there is no file locking, so more than one person can open and edit the same file. I added the word "mand" to the fstab, but this does not seem to have made any difference.

---

### Post by bab1 on 2016-05-23
> **jamarsh123 said:**
> I have made the changes you suggested. Here is the latest version of the shares in smb.conf, including global

The global section should be at the top.  I believe the file is parsed from top to bottom with the last setting being used.  The directory and create mask directives should be in each share definition only.
> 
Also, I have set the group sticky bit recursively for all three of the group folders. The problem at present is there is no file locking, so more than one person can open and edit the same file. I added the word "mand" to the fstab, but this does not seem to have made any difference.
Setting "mand" is only part of what you have to do.  You will need to configure the directory or individual file for mand.  See [**here**]("http://www.thegeekstuff.com/2012/04/linux-file-locking-types/") for a start down that road.

---

### Post by jamarsh123 on 2016-05-23
Hi bab1:
Thanks for the reply, I read the article. Let me go back a step, since this is my first set up of a server. When I transferred files to the server, I created an account for myself named manager. I gave manager ownership of all the company files. Should they instead be assigned to the root?

---

### Post by bab1 on 2016-05-23
> **jamarsh123 said:**
> Hi bab1:
Thanks for the reply, I read the article. Let me go back a step, since this is my first set up of a server. When I transferred files to the server, I created an account for myself named manager. I gave manager ownership of all the company files. Should they instead be assigned to the root?
Root is the only administrator of the system.  On Ubuntu this is implemented temporarily via sudo (switch user and do).  With what you are doing with sgid, the owner is not relevant.  The access to the file or directory is provided by group ownership.  Root may have ownership but the group also has ownership.  The 2 entities should have the same access (rwx for directories and rw for files).  When you use sgid, the user creates a file with the ownership of owner:group.  The owner is the creator and the group will be the user group with all the other users in in it. 

There are only 3 types of users on a Ubuntu Linux system.  They are:[LIST]
[*]root user (uid=0) able to do anything on the system
[*]mortal user (human (uid 1000 >)) login and home directory
[*]system user (uid 1 - 999) no login or home directory
[*]
[/LIST]
Why did you create a user named manager?  Is that user also a sudo user.  If not, that user is no different than any other mortal user on the system.

All of this is very different from the way Windows works.  What is it that you don't understand?

[COLOR="#0000CD"]Edit:  What type of data do you have that needs file locks?[/COLOR]

---

### Post by jamarsh123 on 2016-05-25
manager is just a generic user name I came up with  - he is a mortal  user. I changed back all the file names for the 3 groups so that they are owned by  manager. I've tried the sticky bit on and off to no avail. All file  types found in the group directories need to be accessed, modified and  saved by any member. Primarily, we use text files and Libre Office file  types. The problem persists. If a group member creates a file, the new  file does not belong to the group and is locked from further editing.  Below is an example of a new file created called XTEST. While all the other files have the correct permissions, the new file does not. The user is the number id for user spa that is identified as such by the server.
```

-rwxrws--- 1 spa           1011    2208 Jun 13  2015 To Do.rtf
-rwxrws--- 1 spa           1011   43406 Mar 21 16:05 To Do Today.rtf
-rwxrws--- 1 spa           1011    6329 Apr 19 15:53 Voice Message.rtf
-rw-rwSr-- 1 1004         1011    0        May 25 14:27 XTEST

```

I'm really confused.
jamarsh123

---

### Post by bab1 on 2016-05-25
> **jamarsh123 said:**
> manager is just a generic user name I came up with  - he is a mortal  user. I changed back all the file names for the 3 groups so that they are owned by  manager.  I've tried the sticky bit on and off to no avail. All file  types found in the group directories need to be accessed, modified and  saved by any member. Primarily, we use text files and Libre Office file  types. The problem persists. If a group member creates a file, the new  file does not belong to the group and is locked from further editing.  Below is an example of a new file created called XTEST. While all the other files have the correct permissions, the new file does not. The user is the number id for user spa that is identified as such by the server.
```

-rwxrws--- 1 spa           1011    2208 Jun 13  2015 To Do.rtf
-rwxrws--- 1 spa           1011   43406 Mar 21 16:05 To Do Today.rtf
-rwxrws--- 1 spa           1011    6329 Apr 19 15:53 Voice Message.rtf
-rw-rwSr-- 1 1004         1011    0        May 25 14:27 XTEST

```

I'm really confused.
jamarsh123
I don't see what this has to do with file locking at all, so I guess I'm confused too.  ;-)

Lets set this up in a more controlled way.  Wandering around trying random settings is never profitable.

First lets look at what mortal users are on the server.  All Samba users must be a Ubuntu user.  Post the output of this command```
 tail -n15 /etc/passwd|grep 100
```
Now we need to see what groups you have created.  Post the output of this command```
 tail -n15 /etc/group|grep 100
```
Let's see how many of these users have administrative capability.  Post the output of this command```
getent group sudo
```
All of these users should also be Samba users.  Post the output of this command```
sudo pdbedit -L
```

I think it is best if we walk through setting up a test directory that we then share.  It has been my experience that what works best is to:[LIST]
[*]Add the users to the system and the Samba database
[*]Create the directory that you are going to share
[*]Configure that directory for shared use (ownership, permissions and sgid)
[*]Configure the Samba share parameters
[*]
[/LIST]
So lets create test directory that will be the root of the "test" share file system.  This should create the directory at /srv/samba/test ```
sudo mkdir -p /srv/samba/test
```...This directory will be owned by root and the group will be root.
Test your work.  Post the output of this command```
ls -l /srv/samba
```
After I see what you have done we will continue on.

---

### Post by jamarsh123 on 2016-05-26
I am beginning to think that the problem is not samba but something wrongly configured in Linux. None of the users can write to the group directory. Here is an example of user "spa"
```

spa@spa_1:/mnt/beaconFiles_57$ touch xtest
touch: cannot touch ‘xtest’: Permission denied

```
But despite the message, the file is created with the wrong permissions. The file can be deleted, but not edited
```

drwxrws---  2 spa  1011       0 May 16 15:23 UDX
-rw-rw-r--  1 1004 1011       0 May 26 16:19 xtest
drwxrws---  9 spa  1011       0 May 20 14:46 z-miscellaneous

```
Just to show that spa is a member of beaconFiles, here is the list of members of the group
```

beaconFiles:x:1011:manager,frontdesk,maindesk,guy,john,spa

```.
And here is a listing of the directory beaconFiles:
```

manager@ubuntu:/srv/samba/beacon$ ls -l
total 8
drwxrws--- 15 manager beaconFiles 4096 May 26 16:23 beaconFiles
drwxrws---  6 manager finance     4096 May 26 14:05 finance


```

---

### Post by bab1 on 2016-05-26
> **jamarsh123 said:**
> I am beginning to think that the problem is not samba but something wrongly configured in Linux.
That's what I said in the previous post.  If you follow the instructions in that post I'm sure we can figure it out.

---

### Post by jamarsh123 on 2016-05-27
I might need to close thread and open a new one. Group users can write to files, but they cannot create a new file. If I "touch" a new file, this is the response:
```

spa@spa_1:/mnt/beaconFiles_57$ touch xtest
touch: cannot touch ‘xtest’: Permission denied

```
But then, despite the comment, the new file (xtest) is created but with a different set of permissions that do not match the group permissions.
```

spa@spa_1:/mnt/beaconFiles_57$ ls -l
total 9216
drwxrws---  2 spa  1011       0 May 16 15:23 UDX
-rw-rw-r--  1 1004 1011       0 May 27 14:43 xtest
drwxrws---  9 spa  1011       0 May 20 14:46 z-miscellaneous

```
Although the new file is created, it is locked for editing, even by the one who created it!

---

### Post by bab1 on 2016-05-27
Why start a new thread?  I keep telling you what to do, but you seem to be ignoring the instructions.  Do you want my help?

---

### Post by jamarsh123 on 2016-05-27
bab1: So sorry. Must have missed your last 2 replies and just found them. Here is the info requested:
SAMBA USERS
```

manager@ubuntu:~$  tail -n15 /etc/passwd|grep 100
libuuid:x:100:101::/var/lib/libuuid:
manager:x:1000:1000:manager,,,:/home/manager:/bin/bash
john:x:1001:1002:,,,:/home/john:/bin/bash
guy:x:1002:1003:guy,,,:/home/guy:/bin/bash
maindesk:x:1003:1004:maindesk,,,:/home/maindesk:/bin/bash
frontdesk:x:1005:1006:frontdesk,,,:/home/frontdesk:/bin/bash
spa2:x:1006:1008:spa2,,,:/home/spa2:/bin/bash
spa:x:1004:1001:spa,,,:/home/spa:/bin/bash

```
GROUPS
```

manager@ubuntu:~$  tail -n15 /etc/group|grep 100
manager:x:1000:
john:x:1002:
guy:x:1003:
maindesk:x:1004:
frontdesk:x:1006:
spa2:x:1008:
finance:x:1009:manager,spa,john,guy,maindesk
spa:x:1001:

```
Hey, I have 2 other groups: beaconFiles and foothills that are not showing up in the above search!

ADMIN CAPABILITY
```

manager@ubuntu:~$ getent group sudo
sudo:x:27:manager

```
SAMBA USERS
```

manager@ubuntu:~$ sudo pdbedit -L
[sudo] password for manager: 
frontdesk:1005:frontdesk
guy:1002:guy
john:1001:
manager:1000:manager
spa2:1006:spa2
spa:1004:spa
maindesk:1003:maindesk

```
HERE IS THE NEW DIRECTORY:
```

manager@ubuntu:~$ ls -l /srv/samba
total 12
drwxrwxrwx 4 root    root      4096 May 25 13:47 beacon
drwxrws--- 6 manager foothills 4096 May 27 12:46 foothills
drwxr-sr-x 2 root    root      4096 May 27 16:11 test

```

---

### Post by bab1 on 2016-05-27
> **jamarsh123 said:**
> bab1: So sorry. Must have missed your last 2 replies and just found them. Here is the info requested:
SAMBA USERS
```

manager@ubuntu:~$  tail -n15 /etc/passwd|grep 100
libuuid:x:100:101::/var/lib/libuuid:
manager:x:**[COLOR="#FF0000"]1000:1000[/COLOR]**:manager,,,:/home/manager:/bin/bash
john:x:1001:1002:,,,:/home/john:/bin/bash
guy:x:1002:1003:guy,,,:/home/guy:/bin/bash
maindesk:x:1003:1004:maindesk,,,:/home/maindesk:/bin/bash
frontdesk:x:1005:1006:frontdesk,,,:/home/frontdesk:/bin/bash
spa2:x:1006:1008:spa2,,,:/home/spa2:/bin/bash
spa:x:1004:1001:spa,,,:/home/spa:/bin/bash

```
How did you create these users and their primary groups?  With so few users the users and the groups should have had the same number sequence.  The user *manager *has what I expected (i.e. 1000:1000 (uid:gid) see red above).  The management of uid/gid across multiple machines can be a problem with out a centralized system.  It can be done, but you as the system administrator should be consistent.  My system at home has no NIS or LDAP centralized system.  I manage by having all users on all machines have the same uid:gid pairs.  In addition all users have the same login and password on all machines.> 
GROUPS
```

manager@ubuntu:~$  tail -n15 /etc/group|grep 100
manager:x:1000:
john:x:1002:
guy:x:1003:
maindesk:x:1004:
frontdesk:x:1006:
spa2:x:1008:
finance:x:1009:manager,spa,john,guy,maindesk
spa:x:1001:

```
Hey, I have 2 other groups: beaconFiles and foothills that are not showing up in the above search!
Heh!  Read the above reply from me again.  Do you see what the problem is? Hint; no centralized system for user groups.> 

ADMIN CAPABILITY
```

manager@ubuntu:~$ getent group sudo
sudo:x:27:manager

```
SAMBA USERS
```

manager@ubuntu:~$ sudo pdbedit -L
[sudo] password for manager: 
frontdesk:1005:frontdesk
guy:1002:guy
john:1001:
manager:1000:manager
spa2:1006:spa2
spa:1004:spa
maindesk:1003:maindesk

```
HERE IS THE NEW DIRECTORY:
```

manager@[COLOR="#0000CD"]**ubuntu**[/COLOR]:~$ ls -l /srv/samba
total 12
drwxrwxrwx 4 root    root      4096 May 25 13:47 beacon
drwxrws--- 6 manager foothills 4096 May 27 12:46 foothills
drwxr-sr-x 2 root    root      4096 May 27 16:11 test

```
The first thing to remember is that for the present we are only working only on the host ubuntu (see blue above).  The first thing should always be to setup the users on the server and match that on the other hosts (see my bullet chart in post #11.

Before we do anything more with the files, I would delete all the users and groups you added ([COLOR="#FF0000"]**do not delete the user**[/COLOR] *[Bnamed ]manager[/B]*.  Then we can add them back in a meaningful way.  To add the users back you should use this command (where <user> is whatever username you choose)```
sudo adduser <user_name>
```...I suggest adding all the users before you add any specialized user-groups.

In order to not get in the way of the UPG (User Private Groups) you should use some numbering for system groups that are not part of the 1000 or >.  I would use a system gid number in the 500 to 699 sequence.  To add a system group you can use this command```
sudo addgroup --gid 500 <user-group>
```...to add a second system group you just increment the gid and use a different system group name.  Remember system groups are not UPG groups for individual users.

After you sort the all the users and UPG along with adding any system groups, please post the output of these commands```
getent passwd

getent group
```...mostly I'm looking for the users > 1000 and the groups in the 500 range.

---

### Post by jamarsh123 on 2016-05-29
[HTML]
How did you create these users and their primary groups?
[/HTML]
I used the tool “adduser”. However, rather than add all users at the same time, as you recommend, I added the users for a particular group and then created the group. After one group was created, I went on to the second group. I think this might have been the problem. From now on, I will follow the order in your bullet points.

I've followed your instructions. Here is the output of the 2 getent commands:
```

manager@ubuntu:~$ sudo getent passwd 
[sudo] password for manager:  
root:x:0:0:root:/root:/bin/bash 
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin 
bin:x:2:2:bin:/bin:/usr/sbin/nologin 
sys:x:3:3:sys:/dev:/usr/sbin/nologin 
sync:x:4:65534:sync:/bin:/bin/sync 
games:x:5:60:games:/usr/games:/usr/sbin/nologin 
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin 
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin 
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin 
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin 
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin 
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin 
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin 
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin 
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin 
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin 
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin 
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin 
libuuid:x:100:101::/var/lib/libuuid: 
syslog:x:101:104::/home/syslog:/bin/false 
messagebus:x:102:107::/var/run/dbus:/bin/false 
dnsmasq:x:103:65534:dnsmasq,,,:/var/lib/misc:/bin/false 
landscape:x:104:111::/var/lib/landscape:/bin/false 
sshd:x:105:65534::/var/run/sshd:/usr/sbin/nologin 
libvirt-qemu:x:106:106:Libvirt Qemu,,,:/var/lib/libvirt:/bin/false 
libvirt-dnsmasq:x:107:113:Libvirt Dnsmasq,,,:/var/lib/libvirt/dnsmasq:/bin/false 
manager:x:1000:1000:manager,,,:/home/manager:/bin/bash 
john:x:1001:1001:john,,,:/home/john:/bin/bash 
spa:x:1002:1002:spa,,,:/home/spa:/bin/bash 
frontdesk:x:1003:1003:frontdesk,,,:/home/frontdesk:/bin/bash 
maindesk:x:1004:1004:maindesk,,,:/home/maindesk:/bin/bash 
guy:x:1005:1005:guy,,,:/home/guy:/bin/bash 
spa2:x:1006:1006:spa2,,,:/home/spa2:/bin/bash

```
```

manager@ubuntu:~$ sudo getent group (edited)
manager:x:1000:
john:x:1001:
spa:x:1002:
frontdesk:x:1003:
maindesk:x:1004:
guy:x:1005:
spa2:x:1006:
beacon_files:x:500:
finance:x:501:
foothills:x:502:

```

---

### Post by bab1 on 2016-05-30
> **jamarsh123 said:**
> [quote=bab1]
How did you create these users and their primary groups?

I used the tool “adduser”. However, rather than add all users at the same time, as you recommend, I added the users for a particular group and then created the group. After one group was created, I went on to the second group. I think this might have been the problem. From now on, I will follow the order in your bullet points.
[/QUOTE]
Add user is the correct tool.  As you saw it can be used incorrectly.  When you go to add users on another Linux host with users that are managed locally to that host you can provide the uid instead of just accepting what is serially handed out.  So if you wanted to ( and you do want to) create a user with a specific uid:gid you would use this command ```
sudo adduser -uid <nnnn>
```...let's say on the second host you need to add the user spa, the incantation would be```
sudo adduser -uid=1002
```
Although this user is not the same user as on the server it has all the attributes of that user.  The user name and uid:gid matches and that is all that is required.
> 
I've followed your instructions. Here is the output of the 2 getent commands:
```

manager@ubuntu:~$ sudo getent passwd 
[sudo] password for manager:  
root:x:0:0:root:/root:/bin/bash 
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin 
bin:x:2:2:bin:/bin:/usr/sbin/nologin 
sys:x:3:3:sys:/dev:/usr/sbin/nologin 
sync:x:4:65534:sync:/bin:/bin/sync 
games:x:5:60:games:/usr/games:/usr/sbin/nologin 
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin 
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin 
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin 
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin 
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin 
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin 
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin 
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin 
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin 
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin 
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin 
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin 
libuuid:x:100:101::/var/lib/libuuid: 
syslog:x:101:104::/home/syslog:/bin/false 
messagebus:x:102:107::/var/run/dbus:/bin/false 
dnsmasq:x:103:65534:dnsmasq,,,:/var/lib/misc:/bin/false 
landscape:x:104:111::/var/lib/landscape:/bin/false 
sshd:x:105:65534::/var/run/sshd:/usr/sbin/nologin 
libvirt-qemu:x:106:106:Libvirt Qemu,,,:/var/lib/libvirt:/bin/false 
libvirt-dnsmasq:x:107:113:Libvirt Dnsmasq,,,:/var/lib/libvirt/dnsmasq:/bin/false 
manager:x:1000:1000:manager,,,:/home/manager:/bin/bash 
john:x:1001:1001:john,,,:/home/john:/bin/bash 
spa:x:1002:1002:spa,,,:/home/spa:/bin/bash 
frontdesk:x:1003:1003:frontdesk,,,:/home/frontdesk:/bin/bash 
maindesk:x:1004:1004:maindesk,,,:/home/maindesk:/bin/bash 
guy:x:1005:1005:guy,,,:/home/guy:/bin/bash 
spa2:x:1006:1006:spa2,,,:/home/spa2:/bin/bash

```
```

manager@ubuntu:~$ sudo getent group (edited)
manager:x:1000:
john:x:1001:
spa:x:1002:
frontdesk:x:1003:
maindesk:x:1004:
guy:x:1005:
spa2:x:1006:
beacon_files:x:500:
finance:x:501:
foothills:x:502:

```
So now on your machine we need to add some of these users to a group that will manage the /srv/samba/test directory.  There is a built in user group named ***users*** (users:x:100:).  We need to add your user (*manager*) and the user *spa* to the user-group ***users***.  We do that with this command```
sudo addgroup <user_name> <user-group>
```...for your two users the commands are```
sudo addgroup manager users

sudo addgroup spa users
```
To see your work please post the output of this command```
getent group users
```

---

### Post by jamarsh123 on 2016-05-30
Output of getent group users
```

manager@ubuntu:~$ getent group users
users:x:100:manager,spa

```

---

### Post by bab1 on 2016-05-30
> **jamarsh123 said:**
> Output of getent group users
```

manager@ubuntu:~$ getent group users
users:x:100:manager,spa

```
Great.   Now we need to setup the /srv/samba/test file system branch.  First we need to set the correct permissions with this command```
sudo chmod 0775 /srv/samba/test
```
Then we want to add the sgid bit.  We use this command to do that```
sudo chmod g+s /srv/samba/test
```
Now let's change the user-group of */srv/samba/test* with this command ```
sudo chgrp users /srv/samba/test
```

At this point the users group has ownership an read/write and eXecute permissions.  The directory should look like this```

drwxrwsr-x  2 root  users 4096 May 30 14:41 test

```
Try creating files using both user logins.  It should all work.

This is all local to this host.  I set up my other host's users that same as this one so that when I ssh to this host (ubuntu) I have the same abilities.  If you need to do this on another Ubuntu machine, now is the time to do that.  Samba does use the login name to ID but I never take chances.  I try and be consistent.

The next step is to set up a Samba users and Create a share on this host.  First add the users with this command ```
sudo smbpasswd -a <user-name>
```...Let's just add manager and spa at this point.

Next we add the share.  It should look like this```

[Test]
        comment = Test share (password needed)
        path = /srv/samba/public
        browseable = yes
        valid users = [COLOR="#FF0000"]@users[/COLOR]
        force group = users
        writeable = yes
        create mask = 0664
        directory mask = 2775

```
Note that you only need to add the users group (not the individual users (see red)).  You will need to restart the Samba file sharing daemon with this command for it all to work```
sudo service smbd restart
```
We can apply all of this to your specific needs.  This is just a simple test to help you see all the steps.  Let me know how it goes.  If you have questions please feel free to ask.

---

### Post by jamarsh123 on 2016-05-30
Did you mean for this to be 
path = /srv/samba/test     ?
```

path = /srv/samba/public

```

I changed it to test. 
On the server, I can log in as either spa or manager and create and delete files.  I then went to the spa computer and connected with the following mount code:
```

sudo mount -t cifs -o username=spa,passwd=none23 //192.168.0.57/test /mnt/test

```

I can connect and see files, but I cannot create or delete files without using the sudo command.

Are you saying that I need change the uid on the spa computer to match the uid for spa on the server?

---

### Post by bab1 on 2016-05-30
Yes the path should have been /srv/samba/test.

The mount command is not right.  The gid has to be expressly stated.  Try this```
sudo mount -t cifs -o username=spa,passwd=none23,[COLOR="#FF0000"]**gid=100**[/COLOR]  //192.168.0.57/test /mnt/test
```

[QUOTE=jamarsh123]Are you saying that I need change the uid on the spa computer to match the uid for spa on the server? 
[/QUOTE]
[COLOR="#0000CD"]Edit: [s]If you mean should you match the uid:gid of the users on the host spa to those on the host ubuntu, then I would say yes if you want to use other remote access protocols such as ssh or nfs.  When using Samba you can set the uid and gid at mount time.[/s]

I have rethought this.  Simply stated; [SIZE=3]**There is no substitute for doing things the correct way.**[/SIZE]    Manage the users as you would in a single domain.  Sync all username/password, uid/gid on all the Linux machines and match the username/passwords on the Windows machines to the Linux users
  [/COLOR]

---

### Post by jamarsh123 on 2016-05-31
How about this, adding both the uid and gid at mount time:
```

sudo mount -t cifs -o username=spa,passwd=none23,uid=1007,gid=100  //192.168.0.57/test /mnt/test

```
Would this solve the problem of matching of matching the uid of the server? I'm wondering if this could be the answer. I'm in a different location today, so I won't have time to try it until this evening.

---

### Post by bab1 on 2016-05-31
For those readers following along or who find this later on; I think it is best if I restate the edit from the previous post.  

[SIZE=5][COLOR="#800080"][CENTER]There is no substitute for doing things the correct way.[/CENTER][/COLOR][/SIZE][COLOR="#800080"]  
[CENTER]Once you start hacking the system to solve a near term problem you set yourself up for unintended consequences later on. [/CENTER][/COLOR]
When you manage multiple Linux/Unix hosts in a network you should either centralize the user management to synchronize the user attributes (username/password/uid/gid/group membership/etc) or ***manually*** perform this on each host.

The networked Linux hosts are a single domain and should be managed that way.  This network does not have to be a DNS domain (hostname.domainname.TLD).  When users (usernames) interact across hosts it is expected that the user information is identical.  Windows machines do not have this uid/gid setup but at least the username and password should be match if they are interacting in this network.

> **jamarsh123 said:**
> How about this, adding both the uid and gid at mount time:
```

sudo mount -t cifs -o username=spa,passwd=none23,uid=1007,gid=100  //192.168.0.57/test /mnt/test

```
Would this solve the problem of matching of matching the uid of the server? I'm wondering if this could be the answer. I'm in a different location today, so I won't have time to try it until this evening.
No.  Read the above carefully.  You have the ability to redo the username/uid:gid for all the users.  I feel that you should do just that.

After some further thought I don't think the fstab entry is going to do work for your situation either.  There are some problems with using fstab to mount SMB/CIFS file systems.  For one thing it will hang the machine when you try and shut down.  The second thing is what if the user is not the one specified in the fstab.  

I do not directly use fstab for mounting shares.  First I add the options "users" and "noauto" to the fstab line.  This allows non-rout users to use the mount command but doesn't mount the share at boot time.  Then I use a script that the user controls the mount.

The fstab line *could* be```
sudo mount -t cifs -o users,noauto,username=$USER,credentials=$HOME/.smbcred,gid=100  //192.168.0.57/test /mnt/test
```... the .smbcred file is in the users home directory and provides the username, password and domain (WORKGROUP)

The script then just has to be```
mount <mount_point> 
# i.e /mnt/test in this case
```
My script is much more complex as it does error checking (e.g is the server on and such), but that is the gist of the whole thing.  

On the other hand if you have Windows hosts in this mix, the mount the shares via the GUI.  I don't see why you can't do that too.  IMO I'd advise that you just set this all up without fstab or scripts and allow the shares to be browsed to and mounted graphically just like you would do with a Windows machine.  The gvfs (GUI) subsystem works fine for most uses.

So, sync all the Linux users across all the Linux hosts plus make sure that on the Windows machines the username and password is the same as the Linux users.  Drop the idea of using fstab to mount the share at boot time unless you have dedicated machines for each user.

---

### Post by jamarsh123 on 2016-05-31
[HTML]So, sync all the Linux users across all the Linux hosts plus make sure  that on the Windows machines the username and password is the same as  the Linux users.  Drop the idea of using fstab to mount the share at  boot time unless you have dedicated machines for each user.[/HTML]

I know I'm looking at bit thick, but I'm trying to understand what you mean by sync. Do you mean go on to each linux station that connects to the server and change the uid to match the server?

By the way, for the most part there is only one user on each workstation.

---

### Post by bab1 on 2016-05-31
You don't need to add [noparse][HTML][/HTML][/noparse] blocks for the test you want to quote.  You can use the [noparse]> [/noparse] blocks for that.  Or plain old "  " works too!

"So, sync all the Linux users across all the Linux hosts plus make sure  that on the Windows machines the username and password is the same as  the Linux users.  Drop the idea of using fstab to mount the share at  boot time unless you have dedicated machines for each user."
> **jamarsh123 said:**
> I know I'm looking at bit thick, but I'm trying to understand what you mean by sync. Do you mean go on to each linux station that connects to the server and change the uid to match the server?

Yes,  In the end ***each of the usernames*** on all machines will have the same uid:gid and password.  If the server is the only machine with all of the users then so be it.  The users on each of the clients should match a user on the server manager for manager or spa for spa as examples.  Another way to look at is: manager on any machine will always be 1000:1000 with the same password.
> 
By the way, for the most part there is only one user on each workstation.
You have to be exact.  For the most part is not an exact notion.  There is or is not.  If not, does that mean 2 users may use that machine?

Through all of this you have not mentioned Windows machines.  Are there Windows machines in the mix?

---

### Post by jamarsh123 on 2016-05-31
Thanks for patience; I think I'm getting it. There is only one user per computer. I was anticipating a time in the future when a workstation might be shared by more than one person. 

There are Windows computers on the network, although under my influence, the numbers are diminishing

---

### Post by bab1 on 2016-05-31
> **jamarsh123 said:**
> Thanks for patience; I think I'm getting it. There is only one user per computer. I was anticipating a time in the future when a workstation might be shared by more than one person. 

There are Windows computers on the network, although under my influence, the numbers are diminishing
You can have both NFS exports and Windows style shares.  These can both share the same data to the remote users at the same time.  My file servers do just that.

[COLOR="#0000CD"]Edit: NFS is used to share UNIX/Linux native file systems.[/COLOR]

---

### Post by jamarsh123 on 2016-06-02
I found a tutorial with the following commands to change the uid/gid:
```

usermod -u <NEWUID> <LOGIN>    
groupmod -g <NEWGID> <GROUP>
find / -user <OLDUID> -exec chown -h <NEWUID> {} \;
find / -group <OLDGID> -exec chgrp -h <NEWGID> {} \;
usermod -g <NEWGID> <LOGIN>

```

Are there any risks? Should I perform a backup of the OS beforehand?

---

### Post by bab1 on 2016-06-02
> **jamarsh123 said:**
> I found a tutorial with the following commands to change the uid/gid:
```

usermod -u <NEWUID> <LOGIN>    
groupmod -g <NEWGID> <GROUP>
find / -user <OLDUID> -exec chown -h <NEWUID> {} \;
find / -group <OLDGID> -exec chgrp -h <NEWGID> {} \;
usermod -g <NEWGID> <LOGIN>

```

Are there any risks? Should I perform a backup of the OS beforehand?
There are always risks.  They start with "I found a tutorial".  I can't see what is in that tutorial.  I can't see any reason to backup the OS itself, maybe the data on each local host (the  /home directories).

I assume that ```
usermod -u <NEWUID> <LOGIN>    
groupmod -g <NEWGID> <GROUP>
```...means this in Linux speak```
usermod -u <uid> <username>    
groupmod -g <gid> <group>
```
The uid and gid are the new numbers.  Remember that you can't user a number that is already in use.  The numbers do not become available (released) or applied (new) without at least logging out.  

Deleting the users while saving the directory (use deluser with no options) is also an option.  You as the system admin always have access to the /home directories and should be able to change the ownership to the new user (uid:gid).

I would not use this ```
find / -user <OLDUID> -exec chown -h <NEWUID> {} \;
find / -group <OLDGID> -exec chgrp -h <NEWGID> {} \;

```These can change ownership on files outside of  users home directory.   At this point this is not what you want to do.

To reiterate, follow these points [LIST]
[*] Backup the users data
[*]  Remove all the users other than root (uid=0) and yourself (manager (1000:1000)) 
[*] Add the users back like we have done before
[*] Change ownership on each users home directory to what should be.
[/LIST]

---

### Post by jamarsh123 on 2016-06-08
bab1:
Thanks for your help. Synchronizing the workstation uid/gid with the server was the issue. Everything is now working as it should be.
Regards,
jamarsh123

PS I don't know how, but this thread can be marked "solved."

---

### Post by bab1 on 2016-06-08
> **jamarsh123 said:**
> bab1:
Thanks for your help. Synchronizing the workstation uid/gid with the server was the issue. Everything is now working as it should be.
Regards,
jamarsh123

PS I don't know how, but this thread can be marked "solved."
Only you can mark it "solved".  Look under "Thread Tools" at the top of the editor.

---

