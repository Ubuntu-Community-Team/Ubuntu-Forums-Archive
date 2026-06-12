---
title: "[SAMBA] - Problem with different user accounts (Windows Acess)"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by TI_do_11 on 2015-10-27
Hello everyone,

I belive my problem has a simple solution, but I hasn't been able to identified. 

So I have a Samba Server with** security = share**, and I really want to keep it like that.

I have a public folder, where everyone has full acess, and a another folder (/comsoc) where should be public for read, but require credentials for writing privileges.
Here is the .conf

```

[ComSoc] 
path = /etc/samba/comsoc 
browseable = yes 
guest ok = yes 
read only = guest nobody 
write list = @comsoc 
create mask = 0755

```

Everything looks fine, when acessed by a Windows machine, it allows me to read everything and denies me the write privileges.

However, since it's "guest ok = yes" **it never asks me for credentials**, so even that the group @comsoc has the privileges, they can never write, since Windows doesn't asks for the credentials.

Att,

---

### Post by bab1 on 2015-10-27
> **TI_do_11 said:**
> 
...I have a Samba Server with** security = share**, and I really want to keep it like that.

This means that the only security is the ownership and permissions set by the OS for the directory and files.
> 
I have a public folder, where everyone has full acess, and a another folder (/comsoc) where should be public for read, but require credentials for writing privileges.
Here is the .conf

```

[ComSoc] 
path = /etc/samba/comsoc 
browseable = yes 
guest ok = yes 
read only = guest nobody 
write list = @comsoc 
create mask = 0755

```

Everything looks fine, when acessed by a Windows machine, it allows me to read everything and denies me the write privileges.

However, since it's "guest ok = yes" **it never asks me for credentials**, so even that the group @comsoc has the privileges, they can never write, since Windows doesn't asks for the credentials.

Att,
The  share parameter of "guest ok = yes" does a few things.  First as you noted it eliminates the ability to log in to the share.  Every user is always converted to the guest account.  Secondly, since all users are now seen as the user 'nobody' and they are in the group 'nogroup', they would only have the permissions of nobody:nogroup.  This means you can't have differing access for some other users if you are managing a Samba share that has the "guest ok = yes" parameter.

IMO you should set up 2 shares and use the default security of "security = user".

---

### Post by TI_do_11 on 2015-10-28
Hmm, thank you. That is very enlightening... I've been struggling with this for quite a while now. =(

I don't understand how setting up 2 shares would solve my issue. 

What I need is a folder, where everyone in the network can see (read, download, etc) the files, but only a user can upload/delete the files (IOW write privileges). As I understand, I could do this with "security = user" and "map to guest = bad user". However, there are a lot of persons in my job who are not "computer friendly" (if you know what I mean) and would struggle with a credential request. My phone wouldn't stop ringing for a week. :frown:

---

### Post by bab1 on 2015-10-29
> **TI_do_11 said:**
> Hmm, thank you. That is very enlightening... I've been struggling with this for quite a while now. =(

I don't understand how setting up 2 shares would solve my issue. 

What I need is a folder, where everyone in the network can see (read, download, etc) the files, but only a user can upload/delete the files (IOW write privileges). As I understand, I could do this with "security = user" and "map to guest = bad user". However, there are a lot of persons in my job who are not "computer friendly" (if you know what I mean) and would struggle with a credential request. My phone wouldn't stop ringing for a week. :frown:

Well, I never said that the setting up 2 shares would solve *your *issue.  It appears that your issue has more to do with you not being inconvenienced  at work.  I'm sorry, I don't have much sympathy for that.  After all , it looks like IT support is part of what you job is.  ;-)

What I did say was;  I think you need is to use 2 shares if you have multiple user needs.  I've never see a situation where valuable data has been put in the hands of someone who might make it go away without having the original data saved somewhere else.  That way, if the user that accidentally deletes data they are only deleting a copy.

Part of the problem with your configuration is there are only 2 user groups by (owner (nobody) and all others) with guest access.  No mortal user (human) should be part of the *nogroup* group.

If you need to have a public folder that all can read and no one can delete you can try a directory that has the sticky bit set.  An example of that is the /tmp directory.  Only the owner and root may delete files in that directory.  You can see this with the following command```
ls -l / | grep tmp
```...There are limitations to this use.  The biggest limit is that the sticky bit will only apply to directories you manually set.

You can try and use ACL's, but that will become very confusing real quick.  Once you set the ACL's there is no obvious notation of what the settings are. 

I have no idea what your information flow is like so I can't really comment, except in broad generalities.

---

### Post by TI_do_11 on 2015-10-29
> **bab1 said:**
> Well, I never said that the setting up 2 shares would solve *your *issue.  It appears that your issue has more to do with you not being inconvenienced  at work.  I'm sorry, I don't have much sympathy for that.  After all , it looks like IT support is part of what you job is.  ;-)

What I did say was;  I think you need is to use 2 shares if you have multiple user needs.  I've never see a situation where valuable data has been put in the hands of someone who might make it go away without having the original data saved somewhere else.  That way, if the user that accidentally deletes data they are only deleting a copy.

Part of the problem with your configuration is there are only 2 user groups by (owner (nobody) and all others) with guest access.  No mortal user (human) should be part of the *nogroup* group.

If you need to have a public folder that all can read and no one can delete you can try a directory that has the sticky bit set.  An example of that is the /tmp directory.  Only the owner and root may delete files in that directory.  You can see this with the following command```
ls -l / | grep tmp
```...There are limitations to this use.  The biggest limit is that the sticky bit will only apply to directories you manually set.

You can try and use ACL's, but that will become very confusing real quick.  Once you set the ACL's there is no obvious notation of what the settings are. 

I have no idea what your information flow is like so I can't really comment, except in broad generalities.

Well, to be straight, IT support is not part of my job, but I do it nevertheless. That is hardly the point though.

My intention is to provide a folder where everyone could see the files without a credencial request. (Because if it asks for a credencial I'm going to have a lot of people calling me and a bunch of others who won't even use the system since they don't have a login and password - That's about making the system more "user friendly", not only about convenience). And only one user should have write privileges, since he is the one who should make the content avaiable.

I haven't said that the data isn't saved elsewhere, but if that was done in a public folder where everyone can write, the data could be edited/deleted making it unavailable for others until the owner put them back in that folder.

I also have a Public Folder already, in that same system, if the only way to do it is 
through security = user, I'm going to do it in a second share, however, if there is another solution, that would be better.

The problem with "sticky bit", to my understanding, is that it would only prevent users from deleting the data, however they would be able to put other files in the directory or edit the ones already there.

Anyway, I thank you for the answer and I'm still looking for a solution, if you, or anyone else, can help, I would appreciate.

---

