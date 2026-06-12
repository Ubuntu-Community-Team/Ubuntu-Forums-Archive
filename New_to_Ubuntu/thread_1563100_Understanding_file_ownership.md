---
title: "Understanding file ownership"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by donescamillo on 2010-08-28
Hi,

Say User1, User2 and User3 belong to a group called (imaginatively) Users. If User1  creates a file, the user owning the file will be User1 (sorry for the repetition, just want to be precise) and the group owning the file will be Users. But what if User1 does not anyone else to have any rights regarding this file. Can User1 create group in which User1 is the only member and so prevents anyone from owning the file?
Is this the only way of making sure only one user (not group) owns the file?

thanks

---

### Post by skatinjj on 2010-08-28
> **donescamillo said:**
> Hi,

Say User1, User2 and User3 belong to a group called (imaginatively) Users. If User1  creates a file, the user owning the file will be User1 (sorry for the repetition, just want to be precise) and the group owning the file will be Users. But what if User1 does not anyone else to have any rights regarding this file. Can User1 create group in which User1 is the only member and so prevents anyone from owning the file?
Is this the only way of making sure only one user (not group) owns the file?

thanks

When a user is created a group with that user name is created as well.

When user1 creates a file he is the only owner.  Others have read only rights which you can change in the property window under the tab permissions.

You can create a new group and have user1 as the only member.

---

### Post by AlphaLexman on 2010-08-28
When you 'ls -l' a directory you will see permissions for owners, groups, and others.

If a file has read (+r) permissions for 'group' or 'other' i.e. [ -rw-r--r-- ] then anyone in the group can 'read' the file, but so can anyone 'other'!

For a user to NOT let any group member 'read' a file the user would enter:
```
chmod 600 filename.ext
```Which keeps groups and other out of the permissions.

---

### Post by AlphaLexman on 2010-08-28
Re-reading the original post, the best answer is, Yes. 

User1 could create a new group called 'user1' (different from group 'users') that user2 and user3 are not a part of. But it is just as easy to change the permissions of the file to dis-allow group-members from the file.

---

### Post by Vaphell on 2010-08-28
rwxrwxrwx - rwx for user, rwx for group, rwx for others

User1 belongs to groups User1 and Users
User1 creates a file - file is assigned to the user User1 and to the group User1
other users from the Users group fall into category 'others' because they are not in the default User1 group

when you do ls -l you can see owner's name twice, its because the second one is his group. You can change that with chown command ie chown User1:Users <file> - it will set group to Users thus users from that group are now in the second part of rwxrwxrwx
As you can see permissions allow for finetuning at 3 degrees of trust. Me, my friends, everybody else.
chmod +x make executable across all 3 categories
chmod g+x make executable for group
chmod o-rw remove read/write for 'others'. etc
often you see chmod with numbers from 0 to 7 (read=4, write=2, execute=1 - add stuff you want)

---

### Post by donescamillo on 2010-08-28
> But it is just as easy to change the permissions of the file to dis-allow group-members from the file.

This begs another question ( sorry I ask probably silly questions but I need to understand this rock solid):

If a user1, user2 and user3 are in a group USERS and this group can (for example) write to a file and I change permissions so that users user1 and user2 CANNOT write to the file, will group USERS be still owner (I mean, if some of its members cant write to the file)?

---

### Post by AlphaLexman on 2010-08-28
Permissions in linux were hard for me to figure out at first. The Owner of a file (the second to fourth characters in 'ls -l') can **r**ead, **w**rite and e**x**ecute the file in question. The fifth to eighth characters are for 'group' permissions, and the ninth to eleventh character are for  'other' or 'everyone'.

Ownership of a file is really the most powerful control over a file, allowing group permissions, should keep the file within a department, like marketing, or accounting. The 'other' permission really means it is free and open to the world.

---

### Post by donescamillo on 2010-08-28
Now that I think ( and read ) more of it it seems that permissions cant be assigned individually as per user except when this user is the owner, ie if user1 is an owner of a file (regardless of what permissions it has) we cant really specify (in chmod) something like 
**"yeah, user1 is the owner but I also want user2 and user3 to be able to write to the file"**
I mean, regarding individual rights, they can only be changed for the owner. If an user is not an owner, its permission for a file cant be changed on an individual basis.

---

### Post by AlphaLexman on 2010-08-28
That is where MANY groups can be effective. User2 and User3 must be in a group that can access the file OR, NOT be members of a group to not read the file.

I think you are confused about group permissions...

Please read:
```
man chmod
```

---

### Post by donescamillo on 2010-08-28
There are probably aspect that I dont understand that is why I am asking :D.
If I have this setup:

1. user1, user2, user3 in group1
2. user1, user2 in group2
3. group1 is owner of file1 and it can read, write and execute
4. because of point 3 group2 is others. lets assume the others have no permissions at all

This means that  
a) user1 and user2 can read, write and execute as members of group1. 
b) user1 and user2 have no permissions at all as members of group2.

Which one is true?
I think it is a)

Thanks

---

### Post by Vaphell on 2010-08-28
they have rwx rights
it wouldn't make any sense otherwise - you can assign only 1 group to a file and any other group would throw users into the 'other' box - and users belong to many.

is user the owner? yes -> owner permissions
does user belong to the given owner group? yes -> group permissions
if no was the answer for the above -> other permissions

---

### Post by AlphaLexman on 2010-08-28
> **donescamillo said:**
> 3. group1 is owner of file1 and it can read, write and execute
You are confused :o only users can 'own' a file, a group cannot own the file, only a member of the group. 

Think of ownership like this:
```
+ owner
   - group
   - other

```
The owner doesn't have to be a member of the group to open the file, (s)he own's it. The owner will set group(s) to read and/or write the file based on the owners permissions. The only user that can override the user, is root.

---

### Post by Morbius1 on 2010-08-28
> If User1  creates a file, the user owning the file will be User1 (sorry  for the repetition, just want to be precise) and the group owning the  file will be Users.That statement is incorrect. If User1 creates a file the file will have ownership of:
owner = user1
group = user1
And permissions of 644:
owner can read and write
group can only read
world can only read.
> But what if User1 does not anyone else to have any rights regarding this file. Then user1 will have to change the permissions on that file to 600 as stated above, or place it in a directory that no one else can open:
Create a directory with permissions of 700 and place that file in it:
Owner can open, add to , and delete from that directory but no one else will even be able to open the folder.
> Can User1 create group in which User1 is the only member and so prevents anyone from owning the file?He already is in a group where he is the only member. But because the newly created file has permissions of 644, anyone else ( the last "4" ) can now read that file.

---

### Post by Vaphell on 2010-08-28
1 thing intrigued me though. What happens when conditions are met for user and a group and group has more privileges than the owner. Does it pick one or does it sum up the permissions of user/group. Usually permissions are in a descending order from user to group to other, so if it sums up, you'd never know. The answer is it picks only one set.

If you set ownership/permissions to you:you rw-r-x--- you won't be able to execute the file because the owner part is what counts and it doesn't matter that you belong to a group which gets +x. At least that's what my small tests show :-)

---

### Post by AlphaLexman on 2010-08-28
Well it is possible to set file permissions to 064, or 004, but why would you want to?

---

### Post by donescamillo on 2010-08-28
> If you set ownership/permissions to you:you rw-r-x--- you won't be able  to execute the file because the owner part is what counts and it doesn't  matter that you belong to a group which gets +x. At least that's what  my small tests show

Yes,
I tried it, too.
Apparently the rights are sort of AND-ed. 
I guess the best way to get the most comprehensive answer is to look into the kernel code ](*,).

Thank you

---

### Post by Vaphell on 2010-08-28
> **AlphaLexman said:**
> Well it is possible to set file permissions to 064, or 004, but why would you want to?

it was just an academic question. It might not be too useful, but it gives a possibility of setting permissions by exclusion, not by inclusion.

if you have one user/users who is not allowed and 100 who are, you can make that user/users an owner/group, set it to 0 and others to 7. Oddball approach but should work :)

---

