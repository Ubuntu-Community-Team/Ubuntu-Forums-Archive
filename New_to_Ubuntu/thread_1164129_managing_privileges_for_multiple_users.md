---
title: "managing privileges for multiple users"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Saghaulor on 2009-05-19
I have been looking for a solution without much success. From my research it seems that the only way to modify user privileges is through the user itself. This is not a very efficient way to grant or revoke privileges if you must create multiple accounts bearing the same privileges. 

Is there a way to create a user privilege template or setup privileges through groups and then add the user to the group or some other mechanism that I am not aware of that would make delegating privileges to multiple users easier? 


Please advise. I thank you in advance.

---

### Post by pro003 on 2009-05-19
no it's not, cause when you go to system > administration > users and groups - you can unlock it with your root passwd and gain super user control of managing user accounts including root its own...

---

### Post by Mornedhel on 2009-05-19
If you're into hardcore documentation, I suggest a reading session on ACLs, chmod and others :

man acl (general documentation on POSIX ACLs, not an easy read)
man chmod (changing file permissions)
man chown (changing file ownership)
man chgrp (changing file group ownership)
man adduser/deluser (adding/removing users)
man usermod (changing user properties such as what groups they belong to)
man groupmod/groupadd/groupdel (managing groups)

Quick primer on basic ACLs (the full ACLs cover more than this) :

Files have three types of rights : owner rights, group rights, other rights
Those rights can be specified as any combination of read/write/execute for any of the above. Thus, you can put several users in a group, chgrp a file to have it belong to that group, and all users in the group can access it as the file's group rights specifies.

Full POSIX ACLs allow you to do fun stuff like masks.

---

### Post by Saghaulor on 2009-05-19
> **pro003 said:**
> no it's not, cause when you go to system > administration > users and groups - you can unlock it with your root passwd and gain super user control of managing user accounts including root its own...

But then I still have to go to each individual user and modify their privileges accordingly. I don't want to do that. I want to be able to specify the privileges, and then assign that privilege template to as many users as I want.

What I'm saying is, right now I have to open up each user's properties, go down the list and check off the following:

[LIST=1]
[*]Connect to Internet using a modem
[*]Connect to wireless and ethernet networks
[*]Use audio devices
[*]Use modems
[/LIST]

But I have to do this for multiple users. This becomes very time consuming. There must be an easier way to assign the aforementioned privileges to multiple users.

---

### Post by Saghaulor on 2009-05-19
> **Mornedhel said:**
> If you're into hardcore documentation, I suggest a reading session on ACLs, chmod and others :

man acl (general documentation on POSIX ACLs, not an easy read)
man chmod (changing file permissions)
man chown (changing file ownership)
man chgrp (changing file group ownership)
man adduser/deluser (adding/removing users)
man usermod (changing user properties such as what groups they belong to)
man groupmod/groupadd/groupdel (managing groups)

Quick primer on basic ACLs (the full ACLs cover more than this) :

Files have three types of rights : owner rights, group rights, other rights
Those rights can be specified as any combination of read/write/execute for any of the above. Thus, you can put several users in a group, chgrp a file to have it belong to that group, and all users in the group can access it as the file's group rights specifies.

Full POSIX ACLs allow you to do fun stuff like masks.

Thanks. That's helpful, but not exactly what I was looking for, at least I think.

It is helpful if these privileges are tied to specific files, because then all I need to do is add a group to the file, say 'fieldstaff' and then add the users to said group, and presto, mission accomplished. However, if such files do exist, I do not know what they are or where to find them.

---

### Post by Celauran on 2009-05-19
```
cat /etc/group | grep $yourusername
```
That should show you which groups you belong to, and the names are generally self-explanatory. You can then add users to the appropriate groups from the command line. Hope that helps some.

---

### Post by Mornedhel on 2009-05-19
> **Celauran said:**
> ```
cat /etc/group | grep $yourusername
```That should show you which groups you belong to, and the names are generally self-explanatory. You can then add users to the appropriate groups from the command line. Hope that helps some.

Your command works, but just typing 'groups' is easier :)

Saghaulor: Please clarify ? Privileges are always tied to files in the basic model. You can make use of the find command (or just execute chmod recursively where you need to, dangerous when operating in the filesystem root) to chmod your files in a smarter fashion. If your needs are more complicated, you'll have to go into shell scripting. Could you provide a use case for your problem ?

---

### Post by Celauran on 2009-05-19
> **Mornedhel said:**
> Your command works, but just typing 'groups' is easier :)
Except that groups will only show which groups you belong to, as opposed to listing the groups you belong to along with a list of other members in those groups. Might make things a little easier as he'll be able to see the changes made to other users as well.

```
svn:x:501:steve,bob,josie
```

Either way, though.

---

### Post by Saghaulor on 2009-05-19
> **Mornedhel said:**
> Your command works, but just typing 'groups' is easier :)

Saghaulor: Please clarify ? Privileges are always tied to files in the basic model. You can make use of the find command (or just execute chmod recursively where you need to, dangerous when operating in the filesystem root) to chmod your files in a smarter fashion. If your needs are more complicated, you'll have to go into shell scripting. Could you provide a use case for your problem ?

Okay, I've found a solution, though it's not exactly what I wanted.

Here's what I'm doing.

I've added several folders to /etc/skel so that when I run 
```
sudo useradd -m username
```
each new user has the same default desktop experience.

Well, since I'm already using 'useradd' I can just specify the groups trigger, like this
```
sudo useradd -m -G netdev,dip,audio,dialout username
```
and it adds the user to the privilege groups that I specified in my previous post.

To clarify, what I meant by privileges was the groups listed in the 'User Privileges' tab under 'User Settings' which is found in 'Users and Groups' in the 'Administration' menu in Gnome.

I believe that you are correct in that some sort of scripting would make my job easier, say a script that prompts me for the new user name and new user password and presto, a new user with custom template privileges is created. Thanks for the help everyone. I'm marking this thread as solved.

---

### Post by nandemonai on 2009-05-19
Groups man groups :)

What's easier? Managing 30 users individually or 3 groups with said 30 users split among them?

Of course the numbers will change but the concept remains the same.. on all multi-user operating systems I might add.

---

### Post by Saghaulor on 2009-05-19
> **nandemonai said:**
> Groups man groups :)

What's easier? Managing 30 users individually or 3 groups with said 30 users split among them?

Of course the numbers will change but the concept remains the same.. on all multi-user operating systems I might add.

The least amount of grinding the better. Do you have any suggestions?

I've considered scripting to [LIST=1]
[*]cat users into /etc/passwd
[*]mkdir /home/username
[*]chown /home/username to username
[*]somehow append username to appropriate groups
[/LIST]

But that seems like a lot of work too. I want minimal work for maximum effect.

---

### Post by Mornedhel on 2009-05-19
> **Saghaulor said:**
> I've considered scripting to
[LIST=1]
[*]cat users into /etc/passwd
[*]mkdir /home/username
[*]chown /home/username to username
[*]somehow append username to appropriate groups
[/LIST]


Then you want the adduser command.

---

### Post by Saghaulor on 2009-05-19
> **Mornedhel said:**
> Then you want the adduser command.

Now we're talking.

I can just modify /etc/adduser.conf to include my default groups, and presto minimal work.

---

