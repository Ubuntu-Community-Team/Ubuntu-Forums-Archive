---
title: "Samba Permission Problems"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by neurostu on 2010-02-26
I'm trying to setup a samba server to host files for several people. 

I don't want to mess around with 3rd party authentication as I'd like to keep this as simple as possible. 

The way I have things setup is as follows, I create each user an account on the server but don't give them their password. They then set a password using 
```

smbpasswd -a <username>

```

Under the /shares/ directory I've created an account for each user and given them ownership over the directory and its contents.

People can all connect just fine but the problem lies in how the linux handles permissions.

Let say I create John and Sam accounts in that order. John's user ID is 1000 and Sam's is 1001. But Sams' user ID on his machine is 1000 so when he mounts the samba shares he is given ownership over the directory that has user ID of 1000 which is johns directory.

I have no clue how to solve this and have be reading the samba man pages and scouring Google but haven't been able to figure out how to solve this problem.

Any help will be greatly appreciated


Here is copy of my /etc/samba/smb.conf file:
```


[global]
# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = myworkgroup
	netbios name = sambaserver
	server string = Ubuntu Samba Server
	security = user
	encrypt passwords = yes
	local master = no

#======================= Share Definitions =======================
[shares]
   comment = shares
   path = /shares/
   valid users = John Sam
   public = no
   writable = yes
   create mask = 0770
   browsable = yes

```

---

### Post by Gone fishing on 2010-02-27
Why not just get samba to share their home directories? If you set the samba box as a pdc you could even get the machines to log and mount the shares as a drive?

I'm currently using ldap but this looks like how I've done it in the past

[http://poormanstech.blogspot.com/2007/02/making-samba-your-primary-domain_08.html](http://poormanstech.blogspot.com/2007/02/making-samba-your-primary-domain_08.html)

I found webmin to be handy for adding users (all be it more than a few) and then automatically making them samba users etc.

---

### Post by Morbius1 on 2010-02-27
I'm not sure I understand the nature of the problem. Are you trying to prevent Sam from editing John's files on the server?

If so, why not create two shares:

[john]
   comment = shares
   path = /shares/john
   valid users = John Sam
   public = no
   writable = no
   write list = John
   create mask = 0770
   browsable = yes

[sam]
   comment = shares
   path = /shares/sam
   valid users = John Sam
   public = no
   writable = no
   write list = Sam
   create mask = 0770
   browsable = yes

Sam will have read only access to the [john] share. When Sam mounts [john] to his local machine he will have the authority to write to his local copy of that file if he wishes to do that but Samba will prevent him from saving it back to the [john] share on the server.

---

### Post by Morbius1 on 2010-02-27
Actually, there might be another way to accomplish this if you'd rather just have the one [share] share:

Leave the samba part as it but change the linux permissions on the shared directory.

**sudo chmod 1777 /share**

What should happen with the "1" "sticky" bit is to allow the owner to have  full rights to files and directories created by him, but others will have read-only rights to files and directories they don't own.

---

### Post by neurostu on 2010-02-28
So the real issue I'm trying to overcome is the mapping of user ID's from their personal linux computers to the Samba server...

So if my userID is 1023 on the samba server but 1000 on my computer I want files I create on the samba server to be owned by 1023 but when I connect I'm given permission to read the files owned by 1023 because they are mine.

The issue is when I mount the samba shares on my computer the file permissions are not translated but read directly by the file system on my computer which doesn't know that my UID on the samba share is different than that on my local machine....

---

### Post by neurostu on 2010-02-28
I also tried creating an individual share for every user but they keep running into permission problems. 

When I set the create mask to 0777 each person can create folders but not files with those folders

I tried changing the create mask to 1777 and the same problem persists.

---

### Post by neurostu on 2010-02-28
ok so here is the explanation from the smb.conf man page:
```

 This parameter may be thought of as a bit-wise MASK for
           the UNIX modes of a file. Any bit not set here will be removed from
           the modes set on a file when it is created.

```
the problem is that the create mode on the user's local machine matters, if they create a file as 0700 then it will be 0700 on the samba server.  Here in lies my problem....


If the local account is 1001 and their account on the samba machine is 1020 when they create the file its ownership is  1020 not 1001.  As their file system doesn't know who 1020 is they can't access the file on their local machine.

---

### Post by asmoore82 on 2010-02-28
> **neurostu said:**
> ... but the problem lies in how the linux handles permissions.
Famous last words :razz:

> **neurostu said:**
> Let say I create John and Sam accounts in that order. John's user ID is 1000 and Sam's is 1001. But Sams' user ID on his machine is 1000 so when he mounts the samba shares he is given ownership over the directory that has user ID of 1000 which is johns directory.
I gather from this info that the machines connecting to the linux samba server
are running linux as well. That sounds like a problem to me.
Samba is great for a mixed Linux/Windows environment but if
it's Linux/Linux then it's just the wrong tool for the job.

Use NFS.

This will also greatly increase performance which is not a Samba issue,
it's a problem with the GVFS system which NFS with forgo altogether.

**P.S.** NFS will exacerbate the UID problem which samba shouldn't have at all...
but you really do need to synchronize UID's across all of the Linux machines.
It is extremely easy to do as you can manipulate the /etc/{passwd,groud,shadow} files directly.

---

### Post by Morbius1 on 2010-02-28
> **neurostu said:**
> If the local account is 1001 and their account on the samba machine is 1020 when they create the file its ownership is  1020 not 1001.  As their file system doesn't know who 1020 is they can't access the file on their local machine.
Maybe it's because every time I read your posts it's the end of my day and not when I'm at least a little more coherent, but I'm still confused.

Tell me if I got this right:

John on the client is 1001
John on the server is 1020

> when they create the file its ownership is  1020 not 1001I assume you mean when John on the client (1001) creates and saves a file to the server it's saved as owner = John (1020). That's what you want to happen. There would be chaos if that where not so.
> As their file system doesn't know who 1020 is they can't access the file on their local machine.This is where I short circuit. The client doesn't know who owns anything on the server. That's between what samba authorizes one to access and what linux permits one to access. From the client, owner,group,and permissions are "unknown" If they can't access the file from their local machine on the server, it's not because samba is stopping them ( based on your original share definition ) it's because linux on the server is stopping them.

What ownership / permissions are set on the target directory:

**ls -dl /share**

---

### Post by neurostu on 2010-03-01
> **asmoore82 said:**
> Famous last words :razz:

**P.S.** NFS will exacerbate the UID problem which samba shouldn't have at all...
but you really do need to synchronize UID's across all of the Linux machines.
It is extremely easy to do as you can manipulate the /etc/{passwd,groud,shadow} files directly.

I guess I'm looking for the option that will reduce my workload. I'm on a network with ~20 linux machines that are run by people with relatively little linux experience.  The last thing I want to be doing is keeping track of what UID's are and going around and changing them on everybod's machines.

Honestly I'm starting to think that having everybody just ssh into the machine and mount their remote directories using sshfs.   Why is this not a good option?   Will this cause the same UID problems?

---

### Post by neurostu on 2010-03-01
> 

I assume you mean when John on the client (1001) creates and saves a file to the server it's saved as owner = John (1020). That's what you want to happen. There would be chaos if that where not so.


This is correct. So John's newley created file is owned by 1020 on the server. When John mounts the share locally the owner of the file is listed as 1020 and b/c john's system is unaware of a user with UID 1020 it no longer considers it john's file.

I completely understand that this problem can be solved by giving every user a unique UID. I just shiver every time I think about doing this across 20 systems....

---

### Post by Morbius1 on 2010-03-01
Then add uid=1001 to the mount command on the client.

Can you provide the mount command you are using?

---

