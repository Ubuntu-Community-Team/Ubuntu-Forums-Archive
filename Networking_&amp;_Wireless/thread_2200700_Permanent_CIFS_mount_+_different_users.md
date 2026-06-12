---
title: "Permanent CIFS mount + different users"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by Anthony_B on 2014-01-20
Hello,

I have 1 ubuntu PC connected to a unix server.
On both systems I try to have the same userids and groupids.

When I mount a CIFS share from the server to the PC using FSTAB, I have to state the _userid in FSTAB_
This means the CIFS share will always be connected with the same userid.

How can I configure the FSTAB in order to have the connection to the CIFS share done with the current userid ?
Maybe something like following ?
[COLOR=#333333]//serve/data  /media/share  cifs  username=[/COLOR]**CurrentUserID**[COLOR=#333333],password=[/COLOR]**CurrentPassword**[COLOR=#333333],iocharset=utf8,sec=ntlm  0  0[/COLOR]


Ultimately, 
when John is connected to the PC, I want the CIFS share to be done with John user
when Jack is connected to the PC, I want the CIFS share to be done with Jack user
when Jim is connected to the PC, I want the CIFS share to be done with Jim user
etc.

It seems to me like a basic requirement for network environment....

Thanks for your help.

---

### Post by Jason_Gibson on 2014-01-20
I don't think you can, at least with the fstab. It gets read well before any user login or selection takes place. What is the endgame here? Each user have their own directory on the server? What are you using for the shares... Samba? NFS?

---

### Post by TheFu on 2014-01-20
It is possible to mount storage many times to different mount points. Mount with each userid under their HOME directory.
I think that will work.

---

### Post by bab1 on 2014-01-20
> **Anthony_B said:**
> Hello,

I have 1 ubuntu PC connected to a unix server.
On both systems I try to have the same userids and groupids.

When I mount a CIFS share from the server to the PC using FSTAB, I have to state the _userid in FSTAB_
This means the CIFS share will always be connected with the same userid.

How can I configure the FSTAB in order to have the connection to the CIFS share done with the current userid ?
Maybe something like following ?
[COLOR=#333333]//serve/data  /media/share  cifs  username=[/COLOR]**CurrentUserID**[COLOR=#333333],password=[/COLOR]**CurrentPassword**[COLOR=#333333],iocharset=utf8,sec=ntlm  0  0[/COLOR]


Ultimately, 
when John is connected to the PC, I want the CIFS share to be done with John user
when Jack is connected to the PC, I want the CIFS share to be done with Jack user
when Jim is connected to the PC, I want the CIFS share to be done with Jim user
etc.

It seems to me like a basic requirement for network environment....

Thanks for your help.

Is there one PC that multiple people are using to connect to the CIFS share?  If so then you should use a common group and control the file and directory permissions using the group user ID, not the individual user ID.  Multiple users with one group ID.

The username in the fstab line (the mount command) is not used to provide file and directory ownership.  It's for Samba login authentication.  The file and directory ownership and permissions are set with uid=<some ID number> and gid=<some ID number>

Think about what you really want here.  Are the users going to read and write information to the share or only read the data that you provide ?  Either way the best way to provide any user access is via group permissions.  The users don't need to "own" the file.  Group access is as good as owner access.  I would put all the users (i.e. John, Jack and Jim) in the same user group.  Ubuntu provides a group named ***users *** for just this purpose.  Of course you could create your own group and add them all to that.  You will need to change group ownership and set the permissions to provide inheritance of that group for the share sub-directories.

If "shared" data is what you want this is the best way to do handle multiple user access.

---

### Post by Morbius1 on 2014-01-21
I'm not entirely sure what you are trying to achieve since access can be restricted on the client end of this but If I take your requirement literally:
> Ultimately, 
when John is connected to the PC, I want the CIFS share to be done with John user
when Jack is connected to the PC, I want the CIFS share to be done with Jack user
when Jim is connected to the PC, I want the CIFS share to be done with Jim user
etc.
That "etc" is a little spooky. Is this some kind of central client on a shop floor or something?

You could create separate lines in fstab one for each user but if you have a lot of users this could get cumbersome.

You might want to think about autofs for a blast from the past:

[1] Install autofs:
```
sudo apt-get install autofs
```
[2] Edit the auto.master file to define the central mount point:
```
gksu gedit /etc/auto.master
```
Add this line above the "+auto.master" line at the bottom:
```
/mnt/Samba /etc/auto.cifsshares --timeout=30 --ghost
```
[3] Then create the auto.cifsshares file to define the mount instead of in fstab:
```
gksu gedit /etc/auto.cifsshares
```
With this content:
```
Serve-Data -fstype=cifs,rw,[COLOR=#333333]sec=ntlm,[/COLOR]iocharset=utf8,credentials=${HOME}/serve.secret.txt,uid=${UID} ://serve/data
```
Then restart the autofs service:
```
sudo service autofs restart
```

Note:
*** The /mnt/Samba and /mnt/Samba/Serve-Data folders will be created automatically by autofs.

*** Each user will have to create his own credentials file, for example:

In /home/john, john will have to create his own serve.secret.txt file with his particular credentials:
```
username=john
password=johnspassword
```
*** Autofs does not mount at boot in the normal way. It mounts automatically when the mount point is accessed. So when "john" accesses /mnt/Samba/Serve-Data it will mount by passing his credentials at that moment. This will all be seamless to john - as far as he is concerned the share is already mounted.

This all assumes that all the users implied by "etc" in your original post are not all logged in at the same time.

---

### Post by Anthony_B on 2014-01-27
Thanks !
This looks to be what I was looking for.
However, I just have one more question:

> **bab1 said:**
> Group access is as good as owner access.  I would put all the users (i.e. John, Jack and Jim) in the same user group.

How do you do a "group access" ?
I guess I still need some password to connect to the CIFS share ?
(somehow I need to replace "[COLOR=#333333]*username=*[/COLOR]**CurrentUserID[COLOR=#333333],[/COLOR]**[COLOR=#333333]*username*[/COLOR]**[COLOR=#333333]=[/COLOR][B]CurrentPassword" **[/B]by something else, right ?)

Anthony

---

### Post by bab1 on 2014-01-27
> **Anthony_B said:**
> How do you do a "group access" ?

You don't *do group access*.  You _gain group access via the group permissions_.  If you are part of the group that is listed (e.g. the group *_users_*) and that group has read and write and eXecute (RWX) permissions, then you can read and write or create a file. 

> 
I guess I still need some password to connect to the CIFS share ?
(somehow I need to replace "[COLOR=#333333]*username=*[/COLOR]**CurrentUserID[COLOR=#333333],[/COLOR]**[COLOR=#333333]*username*[/COLOR]**[COLOR=#333333]=[/COLOR][B]CurrentPassword" **[/B]by something else, right ?)

Anthony
Do you want to use a group to set access permissions?  Why do you feel you need to mount the share via fstab?

---

### Post by Anthony_B on 2014-01-27
> **bab1 said:**
> Do you want to use a group to set access permissions?  Why do you feel you need to mount the share via fstab?

Well, I've been thinking that fstab was the easiest way to mount a share. But any other solutions may work for me.
What are my other options ?

---

### Post by TheFu on 2014-01-27
Use **autofs**, like Morbius1 outlines.  
[https://help.ubuntu.com/community/Autofs#Wildcard_characters](https://help.ubuntu.com/community/Autofs#Wildcard_characters)
Sometimes the easy isn't really the easy way.

---

### Post by bab1 on 2014-01-27
> **Anthony_B said:**
> Well, I've been thinking that fstab was the easiest way to mount a share. But any other solutions may work for me.
What are my other options ?

If the network is setup correctly, you can browse to the share and just click on the folder to mount that share.  How simple is that?  When the user does this the share is mounted with the correct permissions for that user.  Just what you originally wanted.

---

### Post by Anthony_B on 2014-01-27
> **bab1 said:**
> If the network is setup correctly, you can browse to the share and just click on the folder to mount that share.  How simple is that? 

How do you actually "browse the share" **before mounting** ?
If I look at Nautilus, on the left side I just have 2 lines : 1 or "Home" + 1 for "FileSystem"

---

### Post by Anthony_B on 2014-01-27
> **TheFu said:**
> Use **autofs**, like Morbius1 outlines.  
[https://help.ubuntu.com/community/Autofs#Wildcard_characters](https://help.ubuntu.com/community/Autofs#Wildcard_characters)
Sometimes the easy isn't really the easy way.

Well, like Morbius described, it seemed that the **autofs** solution comes with some configuration to be done.
I would need to have a credential file to be created for each user. And this I will need to do for each PC connecting to the same server. I understand it is not "a lot" of work, but I thought that something more straightforward existed.

I probably did not explain correctly what I need (by assuming that the userid should be mentioned during the mounting process).
Let's try to explain it this way:
I have a server where users John, Jack, Jim, ... exist
I also have a PC where users John, Jack, Jim, ... exist as well (with same uid/gid).
What is the standard way to mount a server share on the PC in order to achieve the following?
- permissions settings done on server files should be equally applicable on the PC (consistency between the user connected on the PC and the file located on the server)

Thanks,
Anthony

---

### Post by bab1 on 2014-01-27
> **Anthony_B said:**
> How do you actually "browse the share" **before mounting** ?
If I look at Nautilus, on the left side I just have 2 lines : 1 or "Home" + 1 for "FileSystem"

Open Nautilus >> Ctrl+L >> network:// (in the location bar)

This should display the local workgroup's servers.  The "Windows Network" icon holds any server that is NOT in the local workgroup.

---

### Post by bab1 on 2014-01-27
> **Anthony_B said:**
> What is the standard way to mount a server share on the PC in order to achieve the following?
- permissions settings done on server files should be equally applicable on the PC (consistency between the user connected on the PC and the file located on the server)

Thanks,
Anthony

There is no "standard way".  The 3 types of mounts we have been talking about are all in the end the same procedure (***mount*** ).  The OPTIONS and front-ends to ***mount*** are what is different.  Nautilus uses the same ***mount*** as fstab.  The Nautilus mounts are arbitrary in that you can't specify the options.  The Gnome developers have set that in stone.  The fstab file is the configuration file for ***mount*** to use upon boot up.  You can specify options there.  The fstab does not allow for variables.

If you insist upon each users share mounted differently you will have to script it yourself.

Samba **[COLOR="#008000"]AUTHENTICATION[/COLOR] **is not the same as directory and file permissions.  Permissions are [COLOR="#FF0000"]AUTHORIZATION[/COLOR] to manipulate the files and directories.  Samba authentication is at the server end and the file permissions are set at the time of mounting the share at the local machine's mount point.

---

### Post by Morbius1 on 2014-01-28
> **Anthony_B said:**
> Well, like Morbius described, it seemed that the **autofs** solution comes with some configuration to be done.
I would need to have a credential file to be created for each user. And this I will need to do for each PC connecting to the same server. I understand it is not "a lot" of work, but I thought that something more straightforward existed.
There's a lot of things you can do in a home LAN which would get you fired in an enterprise and this is more of an example of what you can do with autofs not what you should do but you can eliminate the need for the credentials file by making the username variable but hard coding the password:
```
Serve-Data -fstype=cifs,rw,[COLOR=#333333]sec=ntlm,[/COLOR]iocharset=utf8,username=${USER},password=same-password,uid=${UID} ://serve/data
```
When john accesses the folder the name "john" will be passed along with the password of "same-password". When agnes accesses the folder "agnes" will be passed along with the exact same password. I suppose as long as agnes and john don't know what that password is and there is only one share on that server everything will be fine but you're pushing this. Of course you've got some work to do on the server since you'll have to make everyone's samba password the same. 

Another way to do this is Gigolo: [http://ubuntuforums.org/showthread.php?t=1590825&p=9941016#post9941016](http://ubuntuforums.org/showthread.php?t=1590825&p=9941016#post9941016)

Gigolo allows a user to have a remote share automount at login if set up properly. It's using the gvfs backend however so you are forced to use the gvfs mount point of $HOME/.gvfs or /run/user/$USER/gvfs depending on what version of Ubuntu you are using. Gvfs has been rewritten since 12.04 and it's caused me nothing but grief which is why I've move on ( or back - autofs goes back decades )  to autofs but it may work for you.

You know, the more I read your requirements the more I think you are looking for something like LDAP or some kind of single-sign-on system. That’s a rung or 2 or 3 above my pay grade I'm afraid.

---

### Post by Anthony_B on 2014-01-29
> **bab1 said:**
> If you insist upon each users share mounted differently you will have to script it yourself.

Samba **[COLOR=#008000]AUTHENTICATION[/COLOR] **is not the same as directory and file permissions.  Permissions are [COLOR=#FF0000]AUTHORIZATION[/COLOR] to manipulate the files and directories.  Samba authentication is at the server end and the file permissions are set at the time of mounting the share at the local machine's mount point.


Well, I've been wondering whether or not continuing this post...
The thing is I really don't want to look like a fool (even though I may be). But somehow each post you provide me gives me more questions than answers.
Don't mistake me, I really appreciate  the time you take explaining all this, but I have not been able to figure out what I should do.

For instance, I now understand the 2 concepts authentification & authorization. But I 'm now wondering how do you state which userid is used for authentification and which one for authorization ? Is the "username" option from the mount command only related to authentification ? and then do we get authorization from the real uid of the user (even if this uid is not existing on the server) ?

Anyway, at the end, even if there are several solutions for connecting to my server & even if there is no standard way, What would _you_ do ?
I just want my server share to be automatically mounted and all my users to be able to see their files there...

Anthony.

---

### Post by Morbius1 on 2014-01-29
> What would _you_ do ?
Bab1 and I have a gentleman's agreement to stay out of each other's way in times like this since we tend to diverge a bit when it comes to the method of a solution and that confuses the user but I suggest you need to clearly define what your requirements are.

This:
> Ultimately, 
when John is connected to the PC, I want the CIFS share to be done with John user
when Jack is connected to the PC, I want the CIFS share to be done with Jack user
when Jim is connected to the PC, I want the CIFS share to be done with Jim user
[COLOR=#0000cd][I]Looks like you were trying to have each user authenticate himself to the server since john is allowed to do one thing on the server and Jack is allowed to do something else. That's why I suggested autofs and Gigolo.
[/I][/COLOR]
May or may not be entirely different than this:
> I just want my server share to be automatically mounted and all my users to be able to see their files there...

Ultimately, the question that needs to be answered in my mind can be stated as: What is the relationship between "John" and "Jack"?

Is John allowed to view Jacks files? Is he allowed to edit them? Or even delete them? Can jack only read and John can write? The answer will dictate how you access and mount the remote share and by who and how the remote share on the server is set up. What complicates this is that there are apparently many local login users on each client machine which implies ( at least it implied to me ) that each one had to authenticate himself to the server.

---

### Post by bab1 on 2014-01-29
> **Morbius1 said:**
> Bab1 and I have a gentleman's agreement to stay out of each other's way in times like this...

+1000 on this thought, and I try and respect that also.  Sometimes the answers can be very confusing coming from multiple users.
> 

...since we tend to diverge a bit when it comes to the method of a solution and that confuses the user but I suggest you need to clearly define what your requirements are


I wholeheartedly agree with this and the questions below. 
> 

Ultimately, the question that needs to be answered in my mind can be stated as: What is the relationship between "John" and "Jack"?

Is John allowed to view Jacks files? Is he allowed to edit them? Or even delete them? Can jack only read and John can write? The answer will dictate how you access and mount the remote share and by who and how the remote share on the server is set up. What complicates this is that there are apparently many local login users on each client machine which implies ( at least it implied to me ) that each one had to authenticate himself to the server.

Another way to state @Morbius1's questions is:  
  [LIST]
[*]Do you want the share to contain public information that is shared and can be modified or deleted?  Maybe like a public calendar or a text file that all users are going to modify.  
[*]  Or do you want each user to have a private share where only they can see and modify or delete their data?
[*]  Or something in between, such as a share that only a few users can see and manipulate.
[/LIST]


> **Anthony_B said:**
> ...What would _you_ do ?
I just want my server share to be automatically mounted and all my users to be able to see their files there [in]...


As you can see we need more information to advise you.

---

### Post by bab1 on 2014-01-29
> **Anthony_B said:**
> Well, I've been wondering whether or not continuing this post...


Please do continue.  Everyone starts out where you are now.  There is a learning curve to be sure.  Your questions are not silly or dumb.
> 
The thing is I really don't want to look like a fool (even though I may be). But somehow each post you provide me gives me more questions than answers.

You don't look like a fool to me.  The answer to any of these questions, if understood correctly, should create more questions in your mind.
> 
Don't mistake me, I really appreciate  the time you take explaining all this, but I have not been able to figure out what I should do.

Believe it or not, we are getting to the place where you will know what to do.
> 
For instance, I now understand the 2 concepts authentication & authorization. But I 'm now wondering how do you state which userid is used for authentication and which one for authorization ? Is the "username" option from the mount command only related to authentication ?   
and then do we get authorization from the real uid of the user (even if this uid is not existing on the server) ?

Yes.  You can see that by reading the man pages (man mount.cifs).  Here is the pertinent part```

**user=arg** [COLOR="#FF0000"]<-- This is for Samba authentication[/COLOR]
           specifies the username to connect as. If this is not given, then the environment
           variable USER is used. This option can also take the form "user%password" or
           "workgroup/user" or "workgroup/user%password" to allow the password and workgroup to
           be specified as part of the username.

               Note
               The cifs vfs accepts the parameter user=, or for users familiar with smbfs it
               accepts the longer form of the parameter username=. Similarly the longer smbfs
               style parameter names may be accepted as synonyms for the shorter cifs parameters
               pass=,dom= and cred=.


 **uid=arg** [COLOR="#FF0000"]<-- This sets the permissions for the user (authorization) [/COLOR]
           sets the uid that will own all files or directories on the mounted filesystem when the
           server does not provide ownership information. It may be specified as either a
           username or a numeric uid. When not specified, the default is uid 0. The mount.cifs
           helper must be at version 1.10 or higher to support specifying the uid in non-numeric
           form. See the section on FILE AND DIRECTORY OWNERSHIP AND PERMISSIONS below for more
           information.

**gid=arg** [COLOR="#FF0000"]<-- This sets the permissions for the **_group_** ownership (authorization) [/COLOR]
           sets the gid that will own all files or directories on the mounted filesystem when the
           server does not provide ownership information. It may be specified as either a
           groupname or a numeric gid. When not specified, the default is gid 0. The mount.cifs
           helper must be at version 1.10 or higher to support specifying the gid in non-numeric
           form. See the section on FILE AND DIRECTORY OWNERSHIP AND PERMISSIONS below for more
           information.

```
You must use the UID and GID of users that have accounts on the server.  This means that the Samba user must have a Linux account on the server and a Samba account on the same Samba server.

We will get to the correct (for you) method of setting up your Samba server, but as both @Morbius1 and I said, you need to provide use with the last little bit of information so we can advise you properly.

---

### Post by Anthony_B on 2014-01-30
> **Morbius1 said:**
> Ultimately, the question that needs to be answered in my mind can be stated as: What is the relationship between "John" and "Jack"?

> **bab1 said:**
> As you can see we need more information to advise you.

The purpose of my server is to store all files from every member of the family. Within the share, there are folders such as "public", "daddy", "mommy", "kid1", "kid2".
Each user, from any PC connected to the server, should have access to the datas (files & folder) for which he has permissions (read, write or execute).
For that, each file & folder within the share have the appropriate filepermissions settings

Ideally, when mounted on the PC, the share folder (and the files within) would behave exactly like any another folder within the PC. I know that a requirement for that is that my users should exist on both the PC and the server with the same uid : that, I already did.

From what I understand from the difference with Authorization & Authentification, my main issue is to mount the share in such a way that the authorization process is specific to each user.

Anthony

---

### Post by bab1 on 2014-01-30
> **Anthony_B said:**
> The purpose of my server is to store all files from every member of the family. Within the share, there are folders such as "public", "daddy", "mommy", "kid1", "kid2".

Each user, from any PC connected to the server, should have access to the datas (files & folder) for which he has permissions (read, write or execute).
For that, each file & folder within the share have the appropriate file permissions settings.


You will  find that it is  easier to create a public share and 4 private shares instead of trying to figure out what permissions to put on one directory or another inside of one share.
> 
Ideally, when mounted on the PC, the share folder (and the files within) would behave exactly like any another folder within the PC. I know that a requirement for that is that my users should exist on both the PC and the server with the same uid : that, I already did.

From what I understand from the difference with Authorization & Authentification, my main issue is to mount the share in such a way that the authorization process is specific to each user.

Samba has made tools just for what you are trying to accomplish.  You should make one share that is public.  That directory could be /srv/samba/[COLOR="#0000FF"]public[/COLOR].  Then you would make a directory for the private shares.  That could be /srv/samba/[COLOR="#FF0000"]private[/COLOR].  The public share directory would have a common user group.  Here is my /srv/samba/public permissions```
drwx[COLOR="#800080"]**rws**[/COLOR]r-x 9 root [COLOR="#800080"]**users**[/COLOR] 4096 Dec  4 10:04 **[COLOR="#800080"]public[/COLOR]**

```...all user that belong to this group have access and authorization to the directory.
Next is the private directories.  Samba internally can create the correct private share on the fly.  In other words, if kid2 logs in, their private share (and only their private share) is made available.  If daddy logs in then only his share is made available, and so on.  I believe this is what you want.  This special share is called the [homes] share.  You create this share once and it works for any user that is a Ubuntu user and a Samba user.  You need these Ubuntu and Samba users for the public share to be meaningful for user permissions (no anonymous guest access) so the  [homes] directory is easy to set up.

****************** Public share ************************

Here is the commands needed to _create the public share_.  First the Ubuntu file system infrastructure (after the # are comments and you don't need to add them) ```

sudo mkdir -p /srv/samba/public    # the public directory

sudo chown root:users /srv/samba/public     # change the group ownership

sudo chmod 2775    # set the group inheritance for all files and subdirectories

```  

Now you create the share by editing the smb.conf file```

sudo nano /etc/samba/smb.conf

```...Add this to the bottom of the file.  Then save and exit the nano editor.
```

[public]
        comment = Shared Data
        path = /srv/samba/public
        browseable = yes
        guest ok = yes
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775

```
I assume that all of the users ("daddy", "mommy", "kid1", "kid2") already have usernames in Ubuntu and Samba,  You can check the Ubuntu names (and uid/gid) with ```
getent passwd
```

You can check the Samba user database with this```
sudo pdbedit -L
```

Now you need to add all the users to the *users *group (gid=100) with this```
useradd -G users <username>
```...substitute the real user name for <username> above.

************************** Private shares ************************

Add the folders for all the usernames like this```

sudo mkdir -p /srv/samba/private/<username>

sudo chown <username>:<username> /srv/samba/private/<username>


```...once again substitute the user name needed for the <username> in the command.

The private ( [homes] ) share is defined and then commented out in the default smb.conf file.  I would reconfigure it to look like this
[COLOR="#0000FF"]Edited as per @Morbius1's suggestions.[/COLOR]
```


# his will share each user's private directory as [COLOR="#FF0000"]\\server\username[/COLOR]
[homes]
   comment = Private Directories
   path =  /srv/samba/private/%S
   valid users = %S
   browseable = yes
   read only = no

# File creation mask is set to 0700 for security reasons. 
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. 
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
   valid users = %S

```

The default code for the [homes] directory is commented out in the smb.conf file.  I would just add add the above to the smb.conf file and leave the commented part alone. 

I'm sure you now have a lot of questions.  The instructions may even need tweaking a bit (chime in here Morbius1).  Ask away and we will help.

---

### Post by Morbius1 on 2014-01-30
Well I guess it had to happen one day but that was exactly what I was thinking  :)

One thing to consider might be to make a modified [homes] by actually specifying the path to the /srv/share/private subfolders:
> [homes]
comment = Home Directories
path = /srv/samba/private/%S
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = No
You'd access it the same way by user-name but now the user is confined to one specific folder and can't mess with all the other stuff in the home directory.

Still leaves the problem of how to mount all this though. Can't do it on one line in fstab. It seems to me there are 4 options:

[1] Do nothing - each user can bookmark the share in nautilus, have it save their credentials, and when they want to access the share select the bookmark. It will pass their name and password and the server will do the rest.

[2] Have a line in fstab for each user specifying his own credentials and mounted to a different mount point with permissions that exclude everyone else locally.

[3] Gigolo - it will do [1] automatically but you will have to install and configure gigolo for every user on every machine.

[4] AutoFS - examples already given.

*BTW, to automount a [homes] share the /etc/auto.cifsshares file would look something like this:*
```
Serve-Home -fstype=cifs,rw,sec=ntlm,iocharset=utf8,credentials=${HOME}/serve.secret.txt,uid=${UID} ://serve/${USER}
```
[I]The values of HOME, UID, and USER will change to whoever is logged in at the moment.

[/I]Past my bedtime - see you all tomorrow.

---

### Post by bab1 on 2014-01-30
Oops!  I knew I would leave something out.  Thanks for catching the private share path (/srv/samba/private/%S)

> [3] Gigolo - it will do [1] automatically but you will have to install and configure gigolo for every user on every machine.
This may be a big +1 for sure.  Even if the machines are using Unity then Gigolo will work great!  It adds back all the functionality that was removed with Gnome3.  It allows the user to "browse" all the shares available and mount the one wanted without any fstab entries.

---

### Post by Morbius1 on 2014-01-31
> **bab1 said:**
> 
...Add this to the bottom of the file.  Then save and exit the nano editor.
[COLOR=#0000FF]Edit as per @Morbius1's suggestions.[/COLOR]
```

[public]
        comment = Shared Data
        path = /srv/samba/private/%S
        valid users = %S
        browseable = yes
        guest ok = yes
        force group = users
        writeable = yes
        create mask = 0664
        force directory mode = 2775

```
Did you mean to change it on the [homes] share instead of the [public] share?

---

### Post by bab1 on 2014-01-31
> **Morbius1 said:**
> Did you mean to change it on the [homes] share instead of the [public] share?
I guess I'm fighting more than just the flu here.  :-(  Yes, indeed you are correct.  The edit is for the [homes] share, not the [public] share.  I'll make the changes on the original post.

---

