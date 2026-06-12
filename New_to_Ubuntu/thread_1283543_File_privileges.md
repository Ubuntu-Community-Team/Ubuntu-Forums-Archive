---
title: "File privileges"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by Eldis on 2009-10-05
My situation is that I have created files with user A but I want to be able to modify and specifically delete them with user B. Is there some way I could give user B the rights to do so ?

The files user A creates are automated so doing chown on every file is not feasible.

This is most likely a no brainer for most linux users but not to me for some reason.

---

### Post by SuperSonic4 on 2009-10-05
Root (obtainable through sudo) can do anything.

```
sudo chown [-R] B:B [/directory/]file
```

If I were in this situation I'd make sure A and B were in a common group and then chown things to that group

---

### Post by Eldis on 2009-10-05
Thanks, i'm aware of chown. I'll look into the group thing. Problem is still that the files get created with a user as their owner.

Any way I could create a file as a user so that a group would be the owner by default instead of the user who created it ?

---

### Post by ajgreeny on 2009-10-05
You can do it with chmod, which changes permissions on files.  Have a look at man chmod for more details .

Here is a summary of the meanings for individual octal digit values; the first three letters relate to owner, the second three to group and the third three to root:

0 --- no permission
1 --x execute 
2 -w- write 
3 -wx write and execute
4 r-- read
5 r-x read and execute
6 rw- read and write
7 rwx read, write and execute

These are the examples from the Symbolic notation section given in octal notation:

    * "-rwxr-xr-x" would be represented as 755 in three-digit octal.
    * "-rw-rw-r--" would be represented as 664 in three-digit octal.
    * "-r-x------" would be represented as 500 in three-digit octal.

So from that, I think you could use ```
chmod -R 775 /path/to/folder
```but be very careful with this as it is not very secure, and I don't think it is a good way to proceed, personally.

---

### Post by bigboy_pdb on 2009-10-05
You can create a new group G and put both users into that group. Then you'll need to edit the file so that it's group is G and following that you'll need to change the permissions so there's group read and write permissions.

The group can be created under Administration -> Users and Groups. Press the "Unlock" button to make changes (and enter your password). Then press the "Manage Groups" button and then the "Add Group" button and you should be able to take it from there.

You can change the file's permissions by right clicking on the file, selecting "Properties", and by clicking the "Permissions" tab under the new window.

You can also do this using access control lists (ACLs) if groups aren't an option, but you'd need to enable them on your drive first.

**EDIT**: You don't need to use root to change the file's group because the owner can change the file's group to one that he/she is a part of.

---

