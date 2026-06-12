---
title: "Samba security questions"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by lakeshore2985 on 2016-04-07
So I was asking myself how secure is setting up Samba for sharing files within my local network. Stumbled upon a rather interesting video from Nixie Pixel ([https://www.youtube.com/watch?v=-wUfzdiE4m8](https://www.youtube.com/watch?v=-wUfzdiE4m8)), but not sure if all steps described in the video are really necessary (or even what they mean). So I'll start listing some of the steps and questions below:

- Do I really need to create a new user account just for samba (e.g "sambaguest") ?
- Is it really necessary to disable /bin/bash for "sambaguest" ? And what does it even mean?
- What are the disadvantages (or possible threats) to not doing such procedures described in the video?

Any additional information on the matter is pretty much welcome!

Thanks!

---

### Post by bab1 on 2016-04-08
> **lakeshore2985 said:**
> ...

- Do I really need to create a new user account just for samba (e.g "sambaguest") ?

Not really, but every user of Samba services must be a Linux user on the host.  If you have no user and Samba is configured for "guest access" then the user "nobody" is used.  The guest user is a configurable parameter so you don't have to use the user "nobody" if you don't want to.  The user nobody has no interactive login.
> 
- Is it really necessary to disable /bin/bash for "sambaguest" ? And what does it even mean?
- What are the disadvantages (or possible threats) to not doing such procedures described in the video?

If you don't have an interactive login (no /bin/bash) then the user can't login to the server directly or via ssh or gain access by exploit.  I didn't watch the video.  If you have additional questions ask away.

---

### Post by lakeshore2985 on 2016-04-08
> **bab1 said:**
> Not really, but every user of Samba services must be a Linux user on the host.  If you have no user and Samba is configured for "guest access" then the user "nobody" is used.  The guest user is a configurable parameter so you don't have to use the user "nobody" if you don't want to.  The user nobody has no interactive login.

If you don't have an interactive login (no /bin/bash) then the user can't login to the server directly or via ssh or gain access by exploit.  I didn't watch the video.  If you have additional questions ask away.

Thanks!

So basically what it does is it creates an additional layer of "protection". It's just still kind of messy when it comes to permissions though, for which I have yet another question: does it mean I wouldn't need to create user accounts on the host for every user accessing the samba services if I create just one "sambaguest" account?

If so then I wonder what would the "smbshared.conf" look like (I prefer using a separate .conf file for folder sharing parameters).

---

### Post by bab1 on 2016-04-08
> **lakeshore2985 said:**
> Thanks!

So basically what it does is it creates an additional layer of "protection". 
You could say that.  More to the point is that the user is a system user.  The account is not used to directly interact with the OS .> 
It's just still kind of messy when it comes to permissions though, for which I have yet another question: does it mean I wouldn't need to create user accounts on the host for every user accessing the samba services if I create just one "sambaguest" account?
It doesn't affect permissions at all.  A system user has access just as a mortal user does.  There already is a guest account for users.  By default it is the user "nobody"  You can configure your *sambaguest* account.  It might be helpful to separate in you thoughts the human who uses the computer from a user account.  We are dealing with the user account, no matter who uses the account.  There are 3 types of accounts on a Linux host.  They are ```
root = uid0 (the only administrator of the host
system = uid1 to 999 (on Ubuntu)(no login )
mortal = uid1000 > interactive shell (login)(on Ubuntu) 
```> 
If so then I wonder what would the "smbshared.conf" look like (I prefer using a separate .conf file for folder sharing parameters).
Are you referring to an include file with just the share definitions?

In the end you should
[LIST]
[*]Add user account(s) -- Linux and Samba
[*]Configure the data store ownership and access permissions
[*]Configure the Samba daemon (smbd) and define the Samba share
[*]
[/LIST]
This is the most efficient way to think about and implement file sharing.

---

### Post by SeijiSensei on 2016-04-08
You can also block users from getting shell access by setting their shells to /usr/sbin/nologin rather than /bin/bash in /etc/passwd.  Here, for instance, is the entry for the "www-data" user that the Apache web server runs under:
```
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
```
This enables the Apache server to spawn "listeners" that handle web requests running as user www-data, but that user cannot get a shell.  You can apply the same logic to ordinary users if you want to limit them to just Samba access.

---

### Post by lakeshore2985 on 2016-04-09
Thank you for the replies! 

Well since creating a single "sambaguest" account would mean not having to create dozens of other accounts on the host machine then I think it's at least worth a try!

If you guys could patiently guide me through this I'd appreciate it!

So here's what my "smb.conf" looks like (would prefer to do this without a GUI):

```
[global]
  server string = Samba Server
  workgroup = <XXX>
  netbios name = <XXX>
  security = user
  encrypt passwords = yes
  guest account = nobody
  name resolve order = bcast host
  include = /etc/samba/smbshared.conf
```

What is it I have to change here? The "security" and "guest account" lines?

---

### Post by bab1 on 2016-04-09
> **lakeshore2985 said:**
> Thank you for the replies! 

Well since creating a single "sambaguest" account would mean not having to create dozens of other accounts on the host machine then I think it's at least worth a try!

If you guys could patiently guide me through this I'd appreciate it!

So here's what my "smb.conf" looks like (would prefer to do this without a GUI):

```
[global]
  server string = Samba Server
  workgroup = <XXX>
  netbios name = <XXX>
  security = user
  encrypt passwords = yes
  guest account = nobody
  name resolve order = bcast host
  include = /etc/samba/smbshared.conf
```

What is it I have to change here? The "security" and "guest account" lines?
Before you rush off and do this I would suggest you fully flesh this idea out.  Are you trying to get away from making lots of shares (one for each user)? On the other hand are you willing to allow all users access to the same files in a single file share share? Or are you after a single file share that the users work is owned by that user while the user-group is a common group?  It is also possible to create a single share that expands the user name and then shares the logged in users private home directory to that user only.

There is no reason to change the security parameter.  In fact there is no security parameter that will work for your situation with Samba4.  The guest account can be changed to your smbguest account but I don't see why you need to do that.  The guest account needs no login to the share so the only thing you are changing is the ownership of the files and directories in the share.

What you are using the file sharing for will make a big difference in the share parameters you use.

---

### Post by lakeshore2985 on 2016-04-15
> **bab1 said:**
> Before you rush off and do this I would suggest you fully flesh this idea out.  Are you trying to get away from making lots of shares (one for each user)? On the other hand are you willing to allow all users access to the same files in a single file share share? Or are you after a single file share that the users work is owned by that user while the user-group is a common group?  It is also possible to create a single share that expands the user name and then shares the logged in users private home directory to that user only.

There is no reason to change the security parameter.  In fact there is no security parameter that will work for your situation with Samba4.  The guest account can be changed to your smbguest account but I don't see why you need to do that.  The guest account needs no login to the share so the only thing you are changing is the ownership of the files and directories in the share.

What you are using the file sharing for will make a big difference in the share parameters you use.

Hey! So I've been thinking about this, been thinking about a lot. Maybe you know what I really want to do is to have permissions such as certain folders only accessible under specific set of permissions; for example, on my main computer there are roughly two users, one is "root" (myself) and the other(s) are standard users. On this same computer I got two physical hard disks, one is an Msata for the OSes and the other drive is used for storage (separate physical partition or whatever). I use Ubuntu on this machine and have two user accounts (as said, one "root" and other "standard"). But the problem is whenever I mount that separate physical partition (storage drive) on either user accounts, the other account cannot access that same storage partition anymore. So how do I fix this? Since the storage partition is owned by me ("root" or administrator) and not the other standard accounts. Maybe put the "root" and "standard" account in the same group?

This is getting tricky (and messy).

---

### Post by bab1 on 2016-04-15
> **lakeshore2985 said:**
> Hey! So I've been thinking about this, been thinking about a lot. Maybe you know what I really want to do is to have permissions such as certain folders only accessible under specific set of permissions; for example, on my main computer there are roughly two users, one is "root" (myself) and the other(s) are standard users. On this same computer I got two physical hard disks, one is an Msata for the OSes and the other drive is used for storage (separate physical partition or whatever). I use Ubuntu on this machine and have two user accounts (as said, one "root" and other "standard"). But the problem is whenever I mount that separate physical partition (storage drive) on either user accounts, the other account cannot access that same storage partition anymore. So how do I fix this? Since the storage partition is owned by me ("root" or administrator) and not the other standard accounts. Maybe put the "root" and "standard" account in the same group?

This is getting tricky (and messy).
It's fairly easy to resolve your user issues.  However, you can be your own worst enemy if you aren't careful.  You should not use the root account to do anything but system administration duties.  File ownership and  permissions are the access control mechanism already.  The directory hierarchy along with ownership/permissions is how you will control users access.  To give  multiple users access to a directory you change the group ownership to a user-group that all the users are members of.  An example of this would be something like this```
ls -l /data
total 8
drwxrwsr-x 3 root [COLOR="#FF0000"]all_users[/COLOR] 4096 Sep 28  2015 share
drwxrwsr-x 5 root [COLOR="#FF0000"]www_devs[/COLOR] 4096 Jun 20  2015 www

```...in the above the users in the group *_all_users_* have read,write and execute access to the directory *share*, while only the users in the group *_www_devs_* have access to the directory *www*.

The mount of any partition is really the mount of a portion of a file system on that partition to the OS file system at a point you have designated (the mount point).  The permissions can be set administratively by the root user.  On the above example the permissions were modified to what you see by the root user.  That is not how they are by default.  In fact not of that structure exists by default on an Ubuntu install.  Not the directory (/data/www or /data/share) or the user-groups (all_users or www_devs).

The idea to put users in a common user group is the right idea.  You never have to add root to any group as root always has access to the files.  The directory in question should should be mounted so the mortal user (human users) has group ownership.  If this is a NTFS formatted partition you need to set the user-group ownership in the mount command.  If this is a ext4 formatted partition the ownership can be modified by the root user at any time.

Try and think only of the user work flow, not the Linux ownership and permissions.  Once that is worked out I can show you how to apply ownership and permissions to accommodate your users.

---

