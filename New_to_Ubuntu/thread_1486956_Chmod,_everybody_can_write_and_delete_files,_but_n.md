---
title: "Chmod, everybody can write and delete files, but not the others files"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by happy.smiler on 2010-05-18
Hi Guys,

Great OS, great web site.

I have been learning Ubuntu for a couple of weeks now, and really liking it.


I don't understand how I set a permission so that it will allow all the users to write and delete files in a folder and then specify that the users "user and group" cannot delete the "other" files? (I have done a search around, and looked at various help manuals)

I guess the way to do it is create a folder, set the permissions so that all users can read, write, and execute. (I'm ok up to this point) Then specify all the files can be read, and executed by any user, this will stop the deletion if the user is not the owner????

I'm a bit confused!

thanks

---

### Post by RiceMonster on 2010-05-18
I'm not sure what you mean by "the other files". If you give write access to eveybody, than anybody can delete it. The only way to prevent users from deleting a file is not to give write access.

If you want to prevent users from deleting specific files within a directory, then you'll have to allow read and write on the whole directory, but not allow write access on those specific files.

---

### Post by da burger on 2010-05-18
I can delete a file I can't write to. It seems weird but I just tested it. Create a file, chmod it to 000, chown it to root:root and then delete it. rm asks you if you want to "remove write-protected regular file" but that's it.

---

### Post by lavinog on 2010-05-18
> **da burger said:**
> I can delete a file I can't write to. It seems weird but I just tested it. Create a file, chmod it to 000, chown it to root:root and then delete it. rm asks you if you want to "remove write-protected regular file" but that's it.

```

sudo touch testfile
ls -l testfile
-rw-r--r-- 1 root root       0 2010-05-18 12:43 testfile

rm testfile 
rm: remove write-protected regular empty file `testfile'? y
rm: cannot remove `testfile': Operation not permitted

sudo chmod 000 testfile
---------- 1 root root       0 2010-05-18 12:43 testfile
rm testfile 
rm: remove write-protected regular empty file `testfile'? y
rm: cannot remove `testfile': Operation not permitted


```

Edit: I did the above in the /tmp folder

After doing the same steps in my home folder I am able to remove it.

Edit2:
If you are the owner of the containing folder, you get to remove files that you do not own, but not write to them.
I guess this could seem messed up, but if you are the owner of the folder, you shouldn't have other users files in them.
If you have root owned files in your home folder, it could mean something is messed up.

---

### Post by da burger on 2010-05-18
Thank you. That explains it.

---

### Post by 8Kuula on 2010-05-18
> **happy.smiler said:**
> I don't understand how I set a permission so that it will allow all the users to write and delete files in a folder and then specify that the users "user and group" cannot delete the "other" files? (I have done a search around, and looked at various help manuals)

So way I understand this is that you wan't to make directory where all users in system can create/modify/delete files. And then deny create/modify/delete files from that directory from some group in system?

Only way I think it can be done is put all users in system to some group, lets say "vipgrp", and then:

```
mkdir directory
chgrp vipgrp directory
chmod 775 directory
chmod g+s direcotry (do not know octal for that ;)
```

So now just remove user from that "vipgrp" and that user can't create files under that directory. On files in that directory that user handled with their "other" bit, so it needs to be zero so that person can't read/write them either, so for files chmod 660 *filename*
File creator needs to see that when he/she creates file and gives group permissions "vipgrp" write bit too, since owner can only change file permissions (excluding root ofc.).

Far as I know in linux systems do not have "deny" bit in file permissions. What I think you mean there.

More detail in [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by happy.smiler on 2010-05-18
thanks guys for the answers

> **8Kuula said:**
> So way I understand this is that you wan't to make directory where all users in system can create/modify/delete files. 

Yes

And then deny create/modify/delete files from that directory from some group in system?

The user "other" can not have its files deleted by "user" or "group" 
but they (other, user, group) can delete their files

Only way I think it can be done is put all users in system to some group, lets say "vipgrp", and then:

```
mkdir directory
chgrp vipgrp directory
chmod 775 directory
chmod g+s direcotry (do not know octal for that ;)
```

So now just remove user from that "vipgrp" and that user can't create files under that directory. On files in that directory that user handled with their "other" bit, so it needs to be zero so that person can't read/write them either, so for files chmod 660 *filename*
File creator needs to see that when he/she creates file and gives group permissions "vipgrp" write bit too, since owner can only change file permissions (excluding root ofc.).

Far as I know in linux systems do not have "deny" bit in file permissions. What I think you mean there.

More detail in [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

thanks

---

### Post by happy.smiler on 2010-05-18
> **happy.smiler said:**
> thanks guys for the answers

Originally Posted by 8Kuula  
So way I understand this is that you wan't to make directory where all users in system can create/modify/delete files. 

Yes

And then deny create/modify/delete files from that directory from some group in system?

The user "other" can not have its files deleted by "user" or "group" 
but they (other, user, group) can delete their files

Only way I think it can be done is put all users in system to some group, lets say "vipgrp", and then:

Code:
mkdir directory
chgrp vipgrp directory
chmod 775 directory
chmod g+s direcotry (do not know octal for that ;)
So now just remove user from that "vipgrp" and that user can't create files under that directory. On files in that directory that user handled with their "other" bit, so it needs to be zero so that person can't read/write them either, so for files chmod 660 filename
File creator needs to see that when he/she creates file and gives group permissions "vipgrp" write bit too, since owner can only change file permissions (excluding root ofc.).

Far as I know in linux systems do not have "deny" bit in file permissions. What I think you mean there.

More detail in [http://www.comptechdoc.org/os/linux/..._ugfilesp.html](http://www.comptechdoc.org/os/linux/..._ugfilesp.html)

thanks

I´ve just worked out that the "chgrp" command wont work for me, as this changes the group and I need it to be "other"

---

