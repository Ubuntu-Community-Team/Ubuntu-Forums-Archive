---
title: "how to change the permission of folder including all the files"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-08-19
Hello, 
I need to  change the permission of folder which contains a lot of files. How to do that ?
The permission should be change of files also not just folder

---

### Post by Lars Noodén on 2011-08-19
chmod -R 700 /path/to/directory

Substitute 700 for the permissions you actually want.  The -R will do it recursively.

---

### Post by Enigmapond on 2011-08-19
You can also simply right-click the folder and go to properties/permissions and set it that way. Just make sure it's applied to all files..(option at the bottom).

---

### Post by amityadav9314 on 2011-08-19
> **Lars Noodén said:**
> chmod -R 700 /path/to/directory

Substitute 700 for the permissions you actually want.  The -R will do it recursively.

it has done but left the inside folders unreadable. it can not even recognize whether it is  a folder (inside folders).I really need to do this because there are many folders in one folder like a chain.

---

### Post by amityadav9314 on 2011-08-19
> **Enigmapond said:**
> You can also simply right-click the folder and go to properties/permissions and set it that way. Just make sure it's applied to all files..(option at the bottom).

This is not working in my system.Option are not highlighted.

---

### Post by Morbius1 on 2011-08-19
Probably because you changed permissions and didn't change ownership.

Please post the output of the following command:
```
ls -al /path/to/folder
```
And tell us what you are trying to do.

BTW, you should never do a "chmod -R 700" to anything since it makes all your files executable.

---

### Post by Enigmapond on 2011-08-19
> **Morbius1 said:**
> Probably because you changed permissions and didn't change ownership.

Please post the output of the following command:
```
ls -al /path/to/folder
```
And tell us what you are trying to do.

BTW, you should never do a "chmod -R 700" to anything since it makes all your files executable.

+1 666 should be sufficient...read/write.

---

### Post by amityadav9314 on 2011-08-19
> **Morbius1 said:**
> 
And tell us what you are trying to do.

BTW, you should never do a "chmod -R 700" to anything since it makes all your files executable.

I just need to get the wordpress folder on my website for that I need to change the permissions.
Now I have done that by pasting the wordpress folder in windows drive and then to my FTP.
Thanks.

I probably did not change the ownership.

---

### Post by Morbius1 on 2011-08-19
That won't work either. With a 666 you won't be able to open any folders. Folders have to be an odd number and files need to be even. Octal mode (777 for example) done recursively isn't smart enough to differentiate between a file and a folder. 

You need to use another method:
```
chmod -R a+rwX /path/to/folder
```All folders will be 777
All files will be 666 except those that were already executable to begin with. That's what the big "X" does.

You have to love the madness that is UNIX. ;)

---

### Post by amityadav9314 on 2011-08-19
> **Morbius1 said:**
> That won't work either. With a 666 you won't be able to open any folders. Folders have to be an odd number and files need to be even. Octal mode (777 for example) done recursively isn't smart enough to differentiate between a file and a folder. 

You need to use another method:
```
chmod -R a+rwX /path/to/folder
```All folders will be 777
All files will be 666 except those that were already executable to begin with. That's what the big "X" does.

You have to love the madness that is UNIX. ;)

Wow, this had done exactly what i need.
Thank you.

---

### Post by amityadav9314 on 2011-08-19
> **Morbius1 said:**
> That won't work either. With a 666 you won't be able to open any folders. Folders have to be an odd number and files need to be even. Octal mode (777 for example) done recursively isn't smart enough to differentiate between a file and a folder. 

You need to use another method:
```
chmod -R a+rwX /path/to/folder
```All folders will be 777
All files will be 666 except those that were already executable to begin with. That's what the big "X" does.

You have to love the madness that is UNIX. ;)

Wow, this has done exactly what I needed.
Thanks!

---

### Post by tigron on 2011-09-28
I just had to post that I really appreciated this information.

---

