---
title: "Permissions and the ls command"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Rubi1200 on 2010-10-25
The output means that the chmod -R  700 command you ran worked.

[COLOR=Red]drwx[/COLOR]:

to break it down:
d = directory
rwx = you, and only you, have read, write, and execute privileges.
No other user can read or access these directories.
Try it as another user and you will see what I mean.
The warnings are nothing to be concerned about (as far as I am aware).

All files that were in the directories at the time also had their permissions changed recursively.

But, any new file you add will not have 700 permissions.

However, because the directory has 700 permissions, no other user will be able to access the files.

I hope this helps explain things for you.

---

### Post by sisco311 on 2010-10-25
~/.gvfs is a virtual filesystem, so you can ignore the *Permission denied* error. 


> **Rubi1200 said:**
> 
All files that were in the directories at the time also had their permissions changed recursively.


Making all files executable is not only a security risk, but may cause other problems too, e.g. see: [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread].

I would change the permissions back to the default ones:
```
find ~ -type d -exec chmod 0755 '{}' +;
find ~ -type f -exec chmod 0644 '{}' +;
```

then change only the permissions of the home directory:
```
chmod 0700 ~
```

For more info about Unix/Linux file and directory permissions check out:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Rubi1200 on 2010-10-25
> **sisco311 said:**
> ~/.gvfs is a virtual filesystem, so you can ignore the *Permission denied* error. 




Making all files executable is not only a security risk, but may cause other problems too, e.g. see: [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread].

I would change the permissions back to the default ones:
```
find ~ -type d -exec chmod 0755 '{}' +;
find ~ -type f -exec chmod 0644 '{}' +;
```then change only the permissions of the home directory:
```
chmod 0700 ~
```For more info about Unix/Linux file and directory permissions check out:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

@sisco311: I understand the security concern you are talking about by making ALL files executable in the home directory.

But, I have 1 problem and 2 questions.

Problem1: I just tried on a test version of Ubuntu to change permissions with and without the -R switch. It does not work without using the -R switch!?! In other words, I ran these commands:
chmod 700 ~ (had no effect)
chmod -R 700 ~ (changes permissions as seen above)
chmod 755 ~ (attempt to change permissions back again has no effect)
chmod -R 755 ~ (worked)

Q1: how is this possible?

Q2: how can permissions be changed to make the home directory 700 without recursively changing permissions for files within the directory?

I would appreciate any input you have about this matter because it is of some concern to me (and most likely other users).

---

### Post by Rubi1200 on 2010-10-26
@sisco311:

Further testing has revealed something interesting. The ```
chmod 700 ~
``` command does work, but it does not show when running the```
 ls -l 
```command. In other words, whether I use 700 or 755 permissions, the ls command still shows the following for the home directory: > drwxr-xr-x 2 If I log out and then back in as another user, the second user cannot access my home directory when the permissions are set to 700 (as one would expect).

Is this deliberate, a bug in the ls command, or something else?

I would appreciate any input about this.

Thanks in advance.

---

### Post by sisco311 on 2010-10-26
Are you sure, you are listing the correct directory? ~ stands for the user's home directory, usually /home/username. So you need to list the content of the /home directory:
```
ls -l /home
```
or use the -d option to list only the directory entry:
```
ls -ld ~
```

---

### Post by CharlesA on 2010-10-26
Tested it on one of my VMs:

```
charles@mars:~$ su test
Password:
test@mars:/home/charles$ cd ..
test@mars:/home$ ls -l
total 44
drwxr-xr-x 3 charles charles 36864 2010-10-23 19:30 charles
drwxr-xr-x 2 test    test     4096 2010-10-26 07:37 test
drwxr-xr-x 2 user    user     4096 2010-10-26 07:37 user
test@mars:/home$ chmod 700 ~
test@mars:/home$ ls -l
total 44
drwxr-xr-x 3 charles charles 36864 2010-10-23 19:30 charles
drwx------ 2 test    test     4096 2010-10-26 07:37 test
drwxr-xr-x 2 user    user     4096 2010-10-26 07:37 user
test@mars:/home$ su user
Password:
user@mars:/home$ ls -l
total 44
drwxr-xr-x 3 charles charles 36864 2010-10-23 19:30 charles
drwx------ 2 test    test     4096 2010-10-26 07:37 test
drwxr-xr-x 2 user    user     4096 2010-10-26 07:37 user
user@mars:/home$ ls test
ls: cannot open directory test: Permission denied
user@mars:/home$

```

---

### Post by Rubi1200 on 2010-10-26
> **sisco311 said:**
> Are you sure, you are listing the correct directory? ~ stands for the user's home directory, usually /home/username. So you need to list the content of the /home directory:
```
ls -l /home
```or use the -d option to list only the directory entry:
```
ls -ld ~
```
Yes!! You are absolutely correct; both commands show the correct permissions after changing to 700 as being drwx (which is what I wanted).

Thank you very much :)

I am marking this as Solved.

EDIT: by the way, if you have the time and inclination to look at this thread it would be much appreciated:
[http://ubuntuforums.org/showthread.php?t=1600817](http://ubuntuforums.org/showthread.php?t=1600817)

---

