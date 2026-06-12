---
title: "Unifying User Ids using LDAP"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by doesntcount on 2013-10-20
Let me first state my requirements clearly:

I have multiple machines in my network. One of these machines is an NFS server that is exporting one directory to all machines. I want certain users to have different read/write permissions on these files that are available via NFS.

For this purpose, I have installed an LDAP server on the same machine running the NFS server. I thought that by doing this, I would be able to simply set the permissions of the files using chmod and chown on the server, and then use the same users on the other machine.

I have LDAP configured in such a way that my passwd is unified throughout the network, so that if I change it on one machine, it changes on another. So I know that authenication is being handled by the LDAP server.

However, my main requirement isn't satisfied, because files that are readable by userX on the LDAP server are NOT readable by userX on any of the clients. I think the root cause of this is because userX on the server isn't actually the same userX on the client. For exampl, when I type "id userX" on the server, it gives a different answer than on the client.

So I think my main question is how do I sync or unify my userids on all the systems in my network? I'm sure ldap can help with this somehow, but I have yet to find concise documentation that tells me how. If anybody has any suggestions to solving this problem, I'd be very interested in hearing it.

Thanks.

---

### Post by redmk2 on 2013-10-20
> **doesntcount said:**
> Let me first state my requirements clearly:

I have multiple machines in my network. One of these machines is an NFS server that is exporting one directory to all machines. I want certain users to have different read/write permissions on these files that are available via NFS.

For this purpose, I have installed an LDAP server on the same machine running the NFS server. I thought that by doing this, I would be able to simply set the permissions of the files using chmod and chown on the server, and then use the same users on the other machine.

I have LDAP configured in such a way that my passwd is unified throughout the network, so that if I change it on one machine, it changes on another. So I know that authenication is being handled by the LDAP server.

However, my main requirement isn't satisfied, because files that are readable by userX on the LDAP server are NOT readable by userX on any of the clients. I think the root cause of this is because userX on the server isn't actually the same userX on the client. For exampl, when I type "id userX" on the server, it gives a different answer than on the client.

So I think my main question is how do I sync or unify my userids on all the systems in my network? I'm sure ldap can help with this somehow, but I have yet to find concise documentation that tells me how. If anybody has any suggestions to solving this problem, I'd be very interested in hearing it.

Thanks.
The NFS server file security is really only*_ that  servers file system ownership and permissions_*.  By that I mean it is based only on that machine's file and directory UID/GID and permissions.  The LDAP data base is used to centralize the network users UID/GID.  This is authentication, but it is not the authorization.  Permissions are authorization.

Using an LDAP server allows you to centrally *authenticate* users only.  At the file system level you would have the choice of local users (as in /etc/passwd) and/or network users (in the LDAP user database) as the owner and group owners of the files.  The permissions (authorization) is at the file system level only.  Keep the local users in a separate ID range from the network users (i.e. 1000-1999 = local and 2000-2999 = network). 

User or Group Names are not relevant to NFS, only the UID and GID numbers.  As an example in my home network i made sure that all the local UID/GID numbers were the same for each user on all machines; no LDAP or NIS.  NFSv4 works perfectly.

What you need to do is rethink how you have implemented the use of the LDAP UID/GID (and therefore user/group names).    I see your choices as
[LIST]
[*]co-ordinate the LDAP UID/GID with the local UID/GID.  Essentially making LDAP useless.  
[*]Use a centralized LDAP database and do away with the local users on all machines (except for a fall back user (root?))
[*]Manually coordinate the local users (UID/GID) on all machines.  See the first choice   :-)
[/LIST]
In addition if you are going t have a common group for multiple users, you will need to set up group ownership inheritance.  This is not the default with Ubuntu or any other Debian based distro.

I'm sure I'm leaving somethings out,  so more thought and questions are needed on your part.  I can help you with everything but the LDAP implementation.  I have used LDAP before in the past,  but I don't use LDAP in my daily life at this point.

---

### Post by doesntcount on 2013-10-20
So, I don't see how co-ordinating uid/gid between the server and clients makes LDAP useless. There are still benefits to have a central place for authentication so that my password stays in sync across the network, right?

---

### Post by redmk2 on 2013-10-20
> **doesntcount said:**
> So, I don't see how co-ordinating uid/gid between the server and clients makes LDAP useless. There are still benefits to have a central place for authentication so that my password stays in sync across the network, right?

I think all the other items mentioned are more important than co-ordinating passwords.  How often do you change your passwords in a simple LAN.  Is this a large network?  If it is large enough for you to need LDAP,  then you really don't want users to have the ability to "log in locally".  I always had access to a local host as a systems administrator with root, but you could have an local user (uid=1000) to do that using sudo.  There is no need for more local users if you are correctly using LDAP.

In reality you either want all users to use a local login or you want them to use a network login (LDAP, NIS etc.), not a blending of both.

[COLOR="#0000FF"]**Edit:** In re-reading your response I am even more confused with your thoughts.  LDAP doesn't co-ordinate uid/gid's.  It takes the place of the local machine uid/gid's for the network user.  The file system uid/gid will be whatever the NFS exports are setup for by the administrator.  They must be consistent with the expectations of the user logging in (his of her uid/gid).
[/COLOR]

---

### Post by doesntcount on 2013-10-20
I agree that all those other items are more important than cooridating passwords, but I don't really get why i can't have both. It seems to me that my only problem right now is that my userids are not in-sync. If they were, userX on a client would be able to access files owned by userX on the NFS server.

So my next quesiton is, what's the best way to get them in sync? Do I just open up /etc/passwd and start changing UIDs? Or is there something that does this automatically? I think NIS does that? But can I use NIS at the same time as LDAP? Will they stomp on each other?

Thanks a lot for your help, by the way.

---

### Post by redmk2 on 2013-10-20
> **doesntcount said:**
> ...
So my next quesiton is, what's the best way to get them in sync? Do I just open up /etc/passwd and start changing UIDs? Or is there something that does this automatically? I think NIS does that? But can I use NIS at the same time as LDAP? Will they stomp on each other?

That's what I'm trying to tell you.  You should **not** have a mix of local users and network users.  ***One or the other***. 

In the local machine you  have them all in each host's (machine) /etc/passwd and /etc/group files.  These would all need to be sync'd between all machines.  i just edit the passwd and group files directly.  But then again I have been doing this for many years.  All of the GUI and command line tools end up editing these two files.  

If you use LDAP to store the information you don't need the network user info in the /etc/passwd and /etc/group files.  You do need to modify the /etc/nsswitch.conf file (with caution).  See ```
man nsswitch.conf
```...this directs the OS to use LDAP data before the files (/etc/passwd and /etc/group).

To me the question: How do I sync the passwords is not the direction you need to go.  The passwords for network users need to be stored in LDAP and the local passwords are stored in /etc/shadow.  You don't sync shadow to LDAP at all.  The actual password sync is from PAM anyway.

I always used this as the following way to differentiate local from network accounts:  first_name=local account :: first_initial+lastname=network account.  This means John Smith might have a local account as *john*and would always have a network account as *jsmith*.  The network account used NFS to mount the /export/home directory.  The local user had the home directory at /home.

In a nutshell, any user in my network with a login of jsmith or somesuch is stored in LDAP -- once! Any user with a login of john or somesuch is a user local to that particular host and is stored in that hosts /etc/passwd, /etc/shadow and /etc/group files.  If you have 100 hosts then you have 100 different users named john and 1 user named jsmith. 

Does this make sense to you?

---

### Post by doesntcount on 2013-10-20
I guess my fundamental misunderstanding has been about how ldap works. I was under the impression that a local user was somehow mapped to a network user. But it seems like they are just fundamentally different.

And it probably means that I just want to ditch ldap altogether. 

This has definitely been enlightening. Thank you for your help.

---

### Post by doesntcount on 2013-10-27
Sorry to bring this thread back up, but I have another question about this, probably redmk2, but not necessarily:

If I am to understand you correctly about file permissions, then would it be possible for anybody in the LAN to fire up a machine, change their uid to the file owner's uid on the server, and then read those files over NFS?

This seems to me like a bit of a security flaw. Am I understanding this correctly?

---

### Post by redmk2 on 2013-10-27
> **doesntcount said:**
> Sorry to bring this thread back up, but I have another question about this, probably redmk2, but not necessarily:

If I am to understand you correctly about file permissions, then would it be possible for anybody in the LAN to fire up a machine, change their uid to the file owner's uid on the server, and then read those files over NFS?

This seems to me like a bit of a security flaw. Am I understanding this correctly?

It is not possible for just  *anybody *to change theirs or anybody else's uid.  On most production NFS servers the only user logins are for systems administrators.  It is true that if you are the root user or have been given the right to change uid/gid you can do that.  It is also true that NFS was designed to mount remote file systems with no more or less security than the user has on a local file system.  The uid/gid and subsequent permissions is the primary security on any Linux system.  

Are these security "flaws".  Not in my mind.  Shared computing resources is a risk on any system.  NFS is not an Internet technology anyway.  It's for LAN use only and a certain amount of collegial trust is to be expected when file systems are exported from an NFS server.

If there is a security flaw it will be with granting root access to someone who can do damage to the OS in far more insidious ways.

---

### Post by doesntcount on 2013-10-29
Okay, but anybody that has root privileges on their own machine, in theory, can access any file exported via NFS on another machine, regardless of the file permissions. If I understand you correctly, I believe that's what you're saying.

And ya, I agree, not that big of a deal, I was just surprised that this was how it worked. And I needed to confirm this to make sure I understood the underlying mechanisms of how all this works.

Thanks again. You've been very helpful.

---

### Post by redmk2 on 2013-10-29
> **doesntcount said:**
> Okay, but anybody that has root privileges on their own machine, in theory, can access any file exported via NFS on another machine, regardless of the file permissions. If I understand you correctly, I believe that's what you're saying.

At all times, for almost everything, the root user can take any action on a host.  No theory, any file system that is mounted locally can be manipulated by the root user.  Sudo or su is the mechanism for a mortal user (i.e. Joe or Jane) to switch to the root user.  Local host file permissions or ownership mean nothing to the local root user.  This means that allowing users root access is not a trivial thing on the client.  

Understand that the root user (user 0) on a [COLOR="#0000FF"]local host[/COLOR] is **not** the same user on a[COLOR="#FF0000"] remote host[/COLOR].  You can't get to the files above the root of the NFS export or the Samba share from the the client machine if the export of share is configured correctly.
> 
And ya, I agree, not that big of a deal, I was just surprised that this was how it worked. And I needed to confirm this to make sure I understood the underlying mechanisms of how all this works.

It is worth your while to read as much as you can on all of this, especially if you are going to have public facing hosts like web servers and the like somewhere down the road.

---

### Post by doesntcount on 2013-11-02
So here's a real world example of something i'm looking to support:

I have a NAS in my LAN that has a bunch of files.

In my LAN i have 2 clients to that NAS. One is my computer, that should have write access to the all of the files on the NAS. The other, is a roommate whom should have read access but not write access.

From what I'm learning here, NFS is not necessarily the way to go. I have no control over that roommate's computer, so I can't stop him from becoming su and deleting all of my files, whether by accident or maliciously.

What would you recommend I do to satisfy my scenario's requirements? I'm interested in your thoughts on this.

---

### Post by bab1 on 2013-11-02
> **doesntcount said:**
> So here's a real world example of something i'm looking to support:

I have a NAS in my LAN that has a bunch of files.

In my LAN i have 2 clients to that NAS. One is my computer, that should have write access to the all of the files on the NAS. The other, is a roommate whom should have read access but not write access.

From what I'm learning here, NFS is not necessarily the way to go. I have no control over that roommate's computer, so I can't stop him from becoming su and deleting all of my files, whether by accident or maliciously.

What would you recommend I do to satisfy my scenario's requirements? I'm interested in your thoughts on this.
Shared data is public data; not owned by anyone specifically.

I think it would help if you thought of this scenario in a different manner on a some of points.  Your data should be separated form other users.  There are also two types of NAS users.  Local and remote.

The NAS has files (data)  that are _only available to the local user_.  An example of this might be /bin or /usr/bin or /var.  These file systems are not available to be mounted remotely and therefore are not able to be modified by remote NFS users. 

Remote users only have access to the file system that is exported.  These might be /exports/<user_name> or /exports/public.

The administrator of the NAS should always have current backups of all data (exported or not).  Preferably the data would be stored on a separate device (hdd).  The location could be something like /srv/backups on the NAS. 

The administrator should be prepared to restore from backups all of the /exports/public at any time. 

To summarize; The NAS administrator doesn't have control of any data exported (shared) with others.  You should always be prepared to restore from *known good backups* all dirty or lost data.  The focus should be on insuring that the data you back up is clean enough for the remote users of the NAS.  Under no circumstances allow anyone but yourself to log in locally.  This includes via SSH or VNC or the like, as these are also local logins.   You can be the master of the NAS because only you can log in and become root on that host (the NAS).

In my installations I separate each users data into separate file systems.  For the user *john* I have /exports/john.  For the user *Diane* I have /exports/diane.  The remote users /etc/fstab file (or a script) is what determines what is export is mounted.  The data is theirs.   I then have a public export that everyone understands that others can modify or delete files in that area.

There are subtleties to this.  You can use **chattr** to make files immutable.  This means that even root can't just change a file.  But root can change the **chattr** settings and then change the file.  See ```
man chattr
```

[COLOR="#0000FF"]Edit: Some additional thoughts.  You room mate is an additional and separate category of user on your LAN.  Because you are not the administrator of that users computer, he is considered a foreign user on the LAN.  If you had configured that computer to only allow mortal user access (no root or sudo) it would be a peer on the LAN, but as it is not configured by you (the administrator) it is a foreign host.

If all of the users (and their computers) are going to be foreign you need to take some extra time to lock down your personal data that you are going to export for your own use.[/COLOR]

---

### Post by redmk2 on 2013-11-02
+1 to all that @bab1 has said.

One thing to add.  If the share is set up properly then **root_squash** is in effect and you can't su to the root user and modify the files.  Google: root squash NFS to see more on this subject.

I do like separating the private data from the public stuff.  And for sure you should have backups of the data.

---

### Post by doesntcount on 2013-11-03
Right, so I do have root_squash enabled, but if the roomate happens to have the same uid as my user, then he would be able to write to my files.

But ya, I'm getting the point. Thanks for the help.

---

