---
title: "How Do I Recreate User Account After Reinstallation?"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by mapes12 on 2009-12-30
I have

/
/home
/swap 

all on their own partitions.

I recently crashed my system and to save time hunting down the problem I simply reinstalled from my Live CD. At the partitioning stage I set the partitions manually so that only / was formatted and I told the installer where /home was but not to format it so as to keep all my settings. Everything worked OK and I was up and running again in no time.

However, on my previous configuration I set up a User Account for my daughter. After the reinstallation /home/molly (my daughters account) is still sitting happily on the /home partition with all her folders in it but when I try to recreate her account in System>Administration>Users and Groups and I enter her name in the Username section of Account Basic Settings I get a prompt telling me I need to select a different path. So I'm stuck trying to recreate her account and using the same /home/molly folder I had before :confused:

I know I could just backup her stuff, delete the /home/molly folder then recreate the account and restore her stuff, but that seems a long way round to pointing to her perfectly good User folder.

Any suggestions would be greatly appreciated.

Mark

---

### Post by lloyd_b on 2009-12-30
> **mapes12 said:**
> I have

/
/home
/swap 

all on their own partitions.

I recently crashed my system and to save time hunting down the problem I simply reinstalled from my Live CD. At the partitioning stage I set the partitions manually so that only / was formatted and I told the installer where /home was but not to format it so as to keep all my settings. Everything worked OK and I was up and running again in no time.

However, on my previous configuration I set up a User Account for my daughter. After the reinstallation /home/molly (my daughters account) is still sitting happily on the /home partition with all her folders in it but when I try to recreate her account in System>Administration>Users and Groups and I enter her name in the Username section of Account Basic Settings I get a prompt telling me I need to select a different path. So I'm stuck trying to recreate here account and using the same /home/molly folder I had before :confused:

I know I could just backup her stuff, delete the /home/molly folder then recreate the account and restore her stuff, but that seems a long way round to pointing to her perfectly good User folder.

Any suggestions would be greatly appreciated.

Mark

Use the backup method.  This doesn't have to be as complex as you think.  In a terminal window:```
sudo mv /home/molly /home/mollyback
```then create the user "molly", and then in a terminal window:```
sudo rm -rf /home/molly
sudo mv /home/mollyback /home/molly
sudo chown -R molly /home/molly
```(note that the last step may or may not be redundant - it depends on whether the user "molly" gets the same user number as on the previous install.  Better safe than sorry...)

Lloyd B.

---

### Post by Paqman on 2009-12-30
You can add a user with an existing home folder from the command line:
```
sudo adduser username --no-create-home
```

If your user has the same uid as the original account, all will be well. If you know what the uid should be you can specify it when you create the account using the command above (just put -u and the uid at the end) 

If you don't know the right uid then you can take the bulldozer approach:
```
sudo chown -R username:username /home/username
```

---

### Post by MLX on 2009-12-30
I found this thread because I did a fresh install of Ubuntu 9.10 from 8.04 and have a separate home partition like the OP. I am now also trying to re-create user accounts. I am trying to learn from this and have 2 questions.

1 The commands given for setting ownership (chown) are different in the examples given, the first uses the -R option and the second does not and the second uses owner:group and the first only uses owner. Please explain the differences.

2 It is widely recommended here to use a separate root and home partition but I did not see anything about this issue after a fresh install. Is there anything that should be done before installation to make this easier? Obviously making note of the UID of each user...anything else?

Thanks

---

### Post by Paqman on 2009-12-30
> **MLX said:**
> 
1 The commands given for setting ownership (chown) are different in the examples given, the first uses the -R option and the second does not and the second uses owner:group and the first only uses owner. Please explain the differences.


My mistake, i've corrected it. The -R stands for recursive, meaning the command applies itself to all files and folders within the one it is applied to.

> 
2 It is widely recommended here to use a separate root and home partition but I did not see anything about this issue after a fresh install. Is there anything that should be done before installation to make this easier? Obviously making note of the UID of each user...anything else?


Nope, pretty much just that. Note that the user you create during installation will be given the uid 1001. So it's easiest for your user accounts to avoid this uid, so that you can recreate their accounts easily. After recreating the user accounts you should make sure at least one of them has admin privileges before deleting the account with uid=1001.

---

### Post by MLX on 2009-12-30
Thanks Paqman
I just found this and it may also help someone learning about user accounts. 
[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)

---

### Post by warfacegod on 2010-01-05
Okay, stupid question.

Can't you just change the name of the/Molly folder, make account, and then change the name back?

Two stupid questions actually.

Why not use a different user name such as "mollygirl" and then move the /molly folder contents the / mollygirl folder?

---

### Post by avid0g on 2010-01-14
@warfacegod              **Re:  **Two stupid questions - not.

 
> >Can't you just change the name of the/Molly folder, make account, and then change the name back?In Lloyd B's examples, the **mv** command *is* used to change the account directory name, twice.

> >Why not use a different user name such as "mollygirl" and then move the /molly folder contents the / mollygirl folder?Many of the hidden files, links and pathnames refer to the old user name "molly" explicitly.  Copying the contents of "molly" to "mollygirl" will leave the user with hidden, broken pathnames containing "molly", when the directory - and user is now "mollygirl".  

Besides, it is better to leave the user with nothing new to adjust to.

*@Mark AKA mapes12     On a separate issue*, some GUI versions of "User and Groups/Add User" have blocked recreation of the user because the user name still exists as a group id.  You have to delete some or all occurrences of the user's old **group id**, before you may succesfully recreate the user id again.  
try "User and Groups/Manage Groups" or 
gksudo gedit   /etc/group   /etc/passwd   /etc/shadow

avid0g

---

