---
title: "Cannot access Samba share from XP machine"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2013-11-18
Cannot access SAMBA share on Ubuntu 12.04 box from XP box.

SAMBA is up and running on the Ubuntu box. smb.conf has the correct windows workgroup name in it, and I can see the Ubuntu box from the XP machine. 

On the Ubuntu box, I have set up a UNIX username "CCD1" with a password for the purposes of sharing. I have added a Samba username in Samba Server Configuration of UNIX name: ccd1, Windows Username: Mike (username on the XP box), and put in password (same as used for the UNIX username). 

I have given access to the Samba shared folder for this username. 

On the XP box I can browse the Network Neighborhood, drill down to the workgroup shares and see the Ubuntu box. I can see the shared folder on the Ubuntu box. It is also sharing printers. I can access the printers, I cannot access the shared folder. 

Here is how /etc/samba/smb.conf lists the two shares:

[PRINT$]
    comment = all printers
    browseable = no
    path = var/spool/samba
    printable = yes
;   guest ok = no
;   read only = yes
    create mask = 6766

[CCD_Staff_Dailies]
    comment = Shared Folder
    path = /media/HDD 1/CCD/CCD_Staff_Dailies
    writeable = yes
;   browseable = yes
    valid users = sysadmin, ccd1

If I attempt to view the contents of the shared folder from the XP box it doesn't ask for my credentials, I just get: "\\Ccd-files-linux\CCD_Staff_Dailies is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. Access is denied."

---

### Post by TheFu on 2013-11-18
Space issue? Try 
path = "/media/HDD 1/CCD/CCD_Staff_Dailies"
It is best to avoid spaces in both directories and filenames.

Also, the "mike" account on XP has ZERO to do with the login for samba.  I always have to initially set the samba password for my account using the **smbpasswd** command. I do not know if this is just my issue or not.

---

### Post by Rocket J Squirrel on 2013-11-18
TheFu: thanks, you are right, I don't know what I was thinking when I named that HDD "HDD 1", it was silly. So I edited smb.conf and added the quotes as suggested, restarted smbd and nmbd but, alas, the XP machine is still being refused access. This isn't supposed to be that difficult, I don't know what the problem is.

---

### Post by TheFu on 2013-11-18
The only other thing that jumped out as "odd" was the 
create mask = 6766
line, but that shouldn't have anything to do with authentication. These are what I use in a writable share here:```

  create mask = 0644
  directory mask = 0755 
  valid users = %S
```
I think the way masks work in samba is different than the umask setting we all know and love. For some sorts of documents, it is easier to use **bindfs** to control samba share permissions.

That doesn't say anything about the global options ... which control authentication.

Are you running samba 3.x or 4?  I looked at 4 a few weeks ago when I needed to setup a new temporary box with CIFS sharing - after 20 minutes, I gave up. To complicated for me.  3 minutes later and my v3.x samba install was sharing and working perfectly. I've been running samba since around 1995.

---

### Post by bab1 on 2013-11-18
> **Rocket J Squirrel said:**
> TheFu: thanks, you are right, I don't know what I was thinking when I named that HDD "HDD 1", it was silly. So I edited smb.conf and added the quotes as suggested, restarted smbd and nmbd but, alas, the XP machine is still being refused access. This isn't supposed to be that difficult, I don't know what the problem is.

What are the permissions set along the path /media/HDD 1/CCD/CCD_Staff_Dailies ?  If the user is not the owner or in the group anywhere on the path then the execute bit has to be set on those directories in the path.  At a very minimum all the directory permissions should be 755.

As @TheFu has said, the user has to be in the Samba users database.  You can check that with this```
sudo pdbedit -L
```

The same user must be a Linux user too.  To check that you can use this command```
getent passwd
```

The same username should appear in both databases for access to a share controlled by the "valid user" parameter.

---

### Post by Rocket J Squirrel on 2013-11-19
@bab1 and @TheFu -- thanks for looking at this. 

> What are the permissions set along the path /media/HDD  1/CCD/CCD_Staff_Dailies ?  If the user is not the owner or in the group  anywhere on the path then the execute bit has to be set on those  directories in the path.  At a very minimum all the directory  permissions should be 755.

Likewise with TheFu's uggestions, isn't this something that  Samba-Server-Configuration should be taking care of? I've read several  "how to" for using Samba-Server-Configuration and they don't get into  anything more complicated than setting up a UNIX username, a Samba  username, and configuring the share to accept those usernames. None address setting permissions from / on down nor do any of them use examples in the root directory.

```
drwxr-xr-x   4 root root  4096 Nov 18 11:46 media
drwx------ 1 sysadmin sysadmin 4096 Nov 12 15:38 HDD 1
drwx------ 1 sysadmin sysadmin      0 Nov 12 12:57 CCD
```
and /media/HDD  1/CCD/CCD_Staff_Dailies is shown as 
```
-rw------- 1 sysadmin sysadmin 48121 May  2  2011
```

I'm not clear on how to get permissions in numeric format.

I'm running Samba 3.x, not 4.

    ```
sysadmin@ccd-files-linux:/etc/samba$ sudo pdbedit -L
    [sudo] password for sysadmin: 
    nobody:65534:nobody
    ccd1:1001:CCD1 Jack Win
    sysadmin:1000:sysadmin
```

and

```
sysadmin@ccd-files-linux:/etc/samba$ getent passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
<snip>
sysadmin:x:1000:1000:sysadmin,,,:/home/sysadmin:/bin/bash
ccd1:x:1001:1001:CCD1 Jack Win,,,:/home/ccd1:/bin/bash
```

(I see smileys up there, hope they don't display that way.)

---

### Post by bab1 on 2013-11-19
> **Rocket J Squirrel said:**
> @bab1 and @TheFu -- thanks for looking at this. 



Likewise with TheFu's uggestions, isn't this something that  Samba-Server-Configuration should be taking care of? I've read several  "how to" for using Samba-Server-Configuration and they don't get into  anything more complicated than setting up a UNIX username, a Samba  username, and configuring the share to accept those usernames. None address setting permissions from / on down nor do any of them use examples in the root directory.

```
drwxr-xr-x   4 root root  4096 Nov 18 11:46 media
drwx------ 1 sysadmin sysadmin 4096 Nov 12 15:38 HDD 1
drwx------ 1 sysadmin sysadmin      0 Nov 12 12:57 CCD
```
and /media/HDD  1/CCD/CCD_Staff_Dailies is shown as 
```
-rw------- 1 sysadmin sysadmin 48121 May  2  2011
```

I'm not clear on how to get permissions in numeric format.

I'm running Samba 3.x, not 4.

    ```
sysadmin@ccd-files-linux:/etc/samba$ sudo pdbedit -L
    [sudo] password for sysadmin: 
    nobody:65534:nobody
    ccd1:1001:CCD1 Jack Win
    sysadmin:1000:sysadmin
```

and

```
sysadmin@ccd-files-linux:/etc/samba$ getent passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
<snip>
sysadmin:x:1000:1000:sysadmin,,,:/home/sysadmin:/bin/bash
ccd1:x:1001:1001:CCD1 Jack Win,,,:/home/ccd1:/bin/bash
```

(I see smileys up there, hope they don't display that way.)

The directory you are sharing is /CCD or CCD_Staff_Dailies?  The path you set in the share definition says *path = /media/HDD 1/CCD/CCD_Staff_Dailies *, but it looks to be a file.  In addition you need to provide eXecute bits on all of the directories in the path.  this is not good```

drwx------ 1 sysadmin sysadmin 4096 Nov 12 15:38 HDD 1 [COLOR="#FF0000"]<-- No eXecute bits for group and others[/COLOR]
drwx------ 1 sysadmin sysadmin      0 Nov 12 12:57 CCD     [COLOR="#FF0000"]<-- Same here[/COLOR]

```

---

### Post by TheFu on 2013-11-19
I have never used a shared "samba username" - that is against most security policies, so I don't want that in my home either. Each user has their own ID and credentials.

File/directory permissions are a different thing.  Perhaps a 30 minute tutorial on them would be good?  After all, 95% of all security on UNIX/Linux systems is based on file permissions. Google will find a tutorial.  

You ask why samba doesn't automatically fix the permissions?  What should it set them to? How will it know what you intend?  There are times for really strange permissions, slightly odd permissions and "normal" (for some value of normal). If samba changed them, I'd be pissed.  Yes, the administrator setting this stuff up should be responsible for controlling permissions. It has to be that way.

---

### Post by bab1 on 2013-11-19
> **TheFu said:**
> I have never used a shared "samba username" - that is against most security policies, so I don't want that in my home either. Each user has their own ID and credentials.

I think you misunderstand here.  We're not talking about 2 users using a "shared 'samba username'" at all.  All users of Samba (except the guest "nobody") must have an entry in both /etc/passwd (the Linux user) and in the database that is created when you use: *smbpasswd -a <username>*.  These below are the same user```

sudo pdbedit -L
    ccd1:1001:CCD1 Jack Win

getent passwd
ccd1:x:1001:1001:CCD1 Jack Win,,,:/home/ccd1:/bin/bash

```
 In other words a Samba user that can "login to a Samba Share" must be both a Linux user and a Samba user.  No sharing of anything except data that is in a public directory. 
> 
You ask why samba doesn't automatically fix the permissions?  What should it set them to? How will it know what you intend?  There are times for really strange permissions, slightly odd permissions and "normal" (for some value of normal). If samba changed them, I'd be pissed.  Yes, the administrator setting this stuff up should be responsible for controlling permissions. It has to be that way.

+1 to this.  Samba makes no assumptions as to where you store the data.  Both the upstream packager and Samba do assume that the standard umask (permissions) are used and there is an understanding of the ramifications of altering the permissions on directories and files.

---

