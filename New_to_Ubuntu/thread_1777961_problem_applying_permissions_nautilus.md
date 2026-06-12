---
title: "problem applying permissions nautilus"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by iansane on 2011-06-08
Hi, I know this is an ongoing problem because I found bug reports and other articles about this as far back as ubuntu gutsy but no resolution to the problem.

I have a directory in /opt which I need my regular user to have read/write permissions to.

1. alt+F2 and gksudo nautilus and then navigate to the directory.
2. go to the directory permissions tab (owner is root)
3. select my users group under group permissions
4. choose read and write
Next step would be to apply permissions to all subdirectories and files but the "read and write" instantly changes back to "---" so the permissions do not apply.

I tried enabling advanced permissions in gconf-editor which shows the individual check boxes for read, write, and execute but even then I click on a check box and it instantly changes back to "-".

Has anyone figured out why this is not working?

Other wise can someone tell me how to apply permissions to a specific group in terminal. I know how but I think if I am using sudo the group permissions will apply to the root group. I want to apply the permissions to "lotus" group which my user is a member of but not apply the permissions to others.

Thanks

---

### Post by dFlyer on 2011-06-08
Have you tried assigning your member to the lotus group using user and groups under system settings/systems?

---

### Post by Gone fishing on 2011-06-08
It is a pain but use the terminal 

You need chmod something like ```
sudo chmod -R 777 /home/me/example
```

have a look at [http://www.thinkplexx.com/learn/article/unix/command/chmod-permissions-flags-explained-600-0600-700-777-100-etc](http://www.thinkplexx.com/learn/article/unix/command/chmod-permissions-flags-explained-600-0600-700-777-100-etc)

---

### Post by Morbius1 on 2011-06-08
> **Gone fishing said:**
> It is a pain but use the terminal 

You need chmod something like ```
sudo chmod -R 777 /home/me/example
```have a look at [http://www.thinkplexx.com/learn/article/unix/command/chmod-permissions-flags-explained-600-0600-700-777-100-etc](http://www.thinkplexx.com/learn/article/unix/command/chmod-permissions-flags-explained-600-0600-700-777-100-etc)
OOPS, I'm almost certain you meant:
```
sudo chmod -R a+rwX /home/me/example
```Doing a recursive 777 will make all files executable not just subdirectories.

---

### Post by iansane on 2011-06-08
thanks all for the replies,

Yes my user is a member of the lotus group but that's not the issue here.

777 applies the permissions to everyone when I only want to apply the permissions to members of the lotus group.

Basically I think morbius1 is close with 
```
sudo chmod -R a+rwX /opt/eclipse
```

But I want to apply those permissions specifically to the group lotus. If I do that command in terminal what group is it applying the permissions to? I think root.

-R 777 gives me this
```
drwxrwxrwx 9 root users 4096 2011-06-08 11:47 eclipse
```

I need where it says users to say lotus. I can sort out the recursive executable part. Just need to change the group and not give permissions to all users

Thanks

---

### Post by dFlyer on 2011-06-08
Change using sudo chown root:lotus

That changes user to lotus.

---

### Post by Gone fishing on 2011-06-08
Sorry I might have got the wrong end of the stick do you wish to add a user to a group?

Then:

sudo usermod -a -G group user

---

### Post by Morbius1 on 2011-06-08
> I need where it says users to say lotus.```
sudo chown :lotus /path/to/directory
```OR 
```
sudo chown -R :lotus /path/to/directory
```If you want it to change the group to everything in the directory

[COLOR=Blue]**EDIT:**[/COLOR] Do you want members of the lotus group to be able to read and write to each other's files. If you do you need 2 more changes to make that so.

---

### Post by Gone fishing on 2011-06-08
sudo chmod -R 770 /home/me/example

Sorry if I'm being daft

Do you also need to chown? to change the ownership of the directory?

---

### Post by iansane on 2011-06-08
OK found the answer.

Thanks for the replies all of you.

Here's what I needed

```
drwxrwxrwx 9 root lotus 4096 2011-06-08 11:47 eclipse

```

accomplished with
```
sudo chgrp -R lotus eclipse
```

Now when I apply permissions with chmod I can easily take all away from "users", let root stay the owner so it has full permissions, and still give what permissions I need to the group which is now "lotus".

Sorry if I was making it complicated but turns out the thing I was looking for was chgrp before chmod.

Thanks again :D

---

### Post by iansane on 2011-06-08
Marked this solved but really wish there was an answer to the problem in using nautilus. Even though I do prefer using terminal if I know the right commands, it would have been quick and easy if this did work right in nautilus permissions.

Oh well, accomplished the end goal via the preferred method so all is good :-)

---

### Post by Morbius1 on 2011-06-08
OK, so now you have /opt/eclipse at 
owner = root
group = lotus
mode = 770 or 777

When user morbius who is a member of the lotus group adds a file it will save as:
owner = morbius
group = morbius
mode = 644

User mary, who is also a member of the lotus group, can read the file ( oddly enough she can also delete the file ) but she cannot edit the file. If you want mary to have the ability to edit morbius' file you need to do a couple more steps.

---

### Post by iansane on 2011-06-08
> **Morbius1 said:**
> OK, so now you have /opt/eclipse at 
owner = root
group = lotus
mode = 770 or 777

When user morbius who is a member of the lotus group adds a file it will save as:
owner = morbius
group = morbius
mode = 644

User mary, who is also a member of the lotus group, can read the file ( oddly enough she can also delete the file ) but she cannot edit the file. If you want mary to have the ability to edit morbius' file you need to do a couple more steps.

Good points morbius1.

I'm changing the permissions from 777 to 760 for directories and 770 for files so only owner(root) and group lotus have any permissions at all to the file. I was not aware that if morbius was a member of lotus, a file written by morbius would be set to group morbius. I guess that is because morbius main group is set to morbius and lotus is just a secondary group?

What if I set all developers main group to lotus and don't let other user be members of lotus because they don't need to access /opt/eclipse unless they are developers who know better than to be making changes in the eclipse directory?

I don't know. This is a learning experience in granular permission settings for me

---

### Post by Morbius1 on 2011-06-08
If you want the new file to save with group = lotus then you need to set the "setgid bit":
```
sudo chmod 2770 /opt/eclipse
```[COLOR=Blue]**EDIT:**[/COLOR] No "-R" please 

The "2" will force every new file to inherit the group lotus ( in this case )

So now the file will save as:
owner = morbius
group = lotus
mode = 644

Mary still cannot edit the file however. If you want that to happen you need to do something further:

Edit /etc/profile as root:
```
gksu gedit /etc/profile
```Find the line at the bottom that references umask and change it to:
```
umask 002
```Logout and log back in again since profile is read only once at login.

Now when morbius adds a file it will save to :
owner = morbius
group = lotus
mode = 664 ( not 644 )

Mary can now edit the file.

---

### Post by iansane on 2011-06-08
Thank you for all the information morbius1.

I want to continue to learn how to deal with permissions on a granular level and never have to resort to the chmod 777 just because of not knowing anything else. 777 kinda defeats the purpose of having permissions in the first place.

After all that I had a similar issue with the jre and jdk I downloaded (I don't understand the point of open-jdk but that's another discussion I guess). Anyway, it turns out that eclipse will not read the directory to see the javaw in jdk without me taking ownership of the jdk directory. Just starting eclipse as a member of lotus with the jdk group set to lotus and lotus having rwx permissions was not enough when the owner was root. 

Well, everything is working now so I'm gonna read over the info you posted and play with some test directories till I fully understand it.

Thank you so much for your help :-)

---

