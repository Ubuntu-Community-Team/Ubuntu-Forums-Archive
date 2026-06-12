---
title: "Re-installed, how to keep old users?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-12-05
I have just done a fresh install, and want to keep the old users from my last install. Everything was on a separate /home partition, and user id 1000 is working fine. How do I add the other users?

---

### Post by celticbhoy on 2009-12-05
OK just an update...

1. tried to use my /etc/passwd & /etc/group files as was suggested before I re-installed, but that just renders GDM with NO users.

2. tried to edit the above files and add any mentions of all other users outside of main user. GDM list all users but I can only login as user 1000 (named during install). I can goto admin/users and change the passwords for all other users (all listed), but still getting 'Authentication failure...' at GDM.

Anyone any help?

---

### Post by mikechant on 2009-12-05
If you were copying /etc/passwd & /etc/group from the previous release, I would expect you would have to copy /etc/shadow as well, since this contains the actual passwords (they were removed from /etc/passwd to a separate file for security reasons a long time ago).

However, I'm not sure that this would actually work either. Things are a lot more complex that in old Unix command line days and there may well be other files with references to userids which you would need to copy as well.

---

### Post by astoltz on 2009-12-05
First undo whatever changes you made to /etc/passwd and /etc/groups.  Then just add the old users back - Administration -> Users and Groups.  Make sure the User ID (under the Advanced tab) matches the old user ID. 

If you do a "ls -l /home", you'll see the user ID associated with each user's home directory:

```
drwxr-xr-x 37 gid  uid   4096 2009-11-25 13:26 user1 
drwxr-xr-x 41 gid  uid   4096 2009-12-02 17:37 user2
```
"user1" and "user2" are the directory names and the "gid", "uid" are the group IDs and user IDs (something like 1003, 1004 - yours may be different).

---

### Post by whitethorn on 2009-12-05
I'm not sure this'll work but.. You need to add the users you want to keep from your old /etc/passwd and your /etc/group.  But to be able to use the users you still need to add a password, the password usually get's written to /etc/shadow.  So if you still have your /etc/shadow.  If not then you need to update the password for the users. Run the following command and change the username to whichever ones you need.  

```
sudo passwd username
```

I don't think it's a good idea to just take the old /etc/passwd and /etc/group, I would just add the lines you need for the different users/groups.

But after running the passwd you should be able to log in as the different users.  Then you can give them the new password and tell them to run passwd as their own users to change the password to what they want.

---

### Post by celticbhoy on 2009-12-05
> **astoltz said:**
> First undo whatever changes you made to /etc/passwd and /etc/groups.  Then just add the old users back - Administration -> Users and Groups.  Make sure the User ID (under the Advanced tab) matches the old user ID. 

If you do a "ls -l /home", you'll see the user ID associated with each user's home directory:

```
drwxr-xr-x 37 user1  1002   4096 2009-11-25 13:26 
drwxr-xr-x 41 user2  1003   4096 2009-12-02 17:37
```
"user1" and "user2" are the directory names and the "1002", "1003" are the user IDs (yours may me different).

That was my initial approach but whenever I tried to add a user it asked for a different home directory.

---

### Post by celticbhoy on 2009-12-05
> **whitethorn said:**
> I'm not sure this'll work but.. You need to add the users you want to keep from your old /etc/passwd and your /etc/group.  But to be able to use the users you still need to add a password, the password usually get's written to /etc/shadow.  So if you still have your /etc/shadow.  If not then you need to update the password for the users. Run the following command and change the username to whichever ones you need.  

```
sudo passwd username
```

I don't think it's a good idea to just take the old /etc/passwd and /etc/group, I would just add the lines you need for the different users/groups.

But after running the passwd you should be able to log in as the different users.  Then you can give them the new password and tell them to run passwd as their own users to change the password to what they want.

Enter new UNIX password: 
Retype new UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged
gary@gary-desktop:~$ 


Any more options..

---

### Post by celticbhoy on 2009-12-05
Sorted.

Edited /etc/shadow and simply copied the entry for the default install user for each old user, changing the username at the start of the line. This basically set everyones password to mine, and then I could just change them using either above command line method or through users GUI

Thanx for the help folks..

---

### Post by astoltz on 2009-12-05
OK, sorry.  I just tried it and realized when you add a user with the Users and Groups utility, it will complain that the home directory already exists and then go no further.  So open a terminal and then:

```
sudo adduser --uid 1003 --gid 1003
```replace the "1003" with whatever the correct uid and gid is for that user (see my last post).

[edit] looks like you figured it out faster than I could type...

---

### Post by sisco311 on 2009-12-05
EDIT: never mind.

---

