---
title: "shortcut / link and change permissions of folder"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by anatak on 2009-08-14
Hello,

I recently installed Ubuntu and LAMP.
Everything works but I have two (maybe) simple questions.

I created a folder in the www directory of Apache. The name of the folder is bike.
1 How can I change the permissions to that folder so that I can write and modify files in the folder with my normal user ?
I only want to give write / modify access to my user and not to other users of the system.

2 how can I create a shortcut or link on my desktop to the bike folder ?

Thank you

---

### Post by jrox717 on 2009-08-14
1. (Ok, I don't know anything about Apache but I'm assuming that your bike folder acts like any other in ubuntu.. someone correct me if I'm wrong, please!)
you will want the permissions on the folder to be rw------- aka you can Read and Write but no one else has any access. (You can see the current permissions if you 
```
 cd /path/to/www_directory
ls -l 
```
Also it should be recursive so the same permissions will apply in the sub-directories. 
```
 chmod -R u=rw,go= /path/to/bike 
``` 
should be what you want. If you're not already the owner you will have to do
```
 sudo chown -R username /path/to/bike 
```
first.


2. To make a symbolic link, you will use
```
 ln -s /path/to/bike /home/username/Desktop/ 
```

for more information (or if my suggestions don't work.. I'm away from a linux computer right now, sorry), look at the man pages for chmod, chown, and ln. good luck!

---

### Post by anatak on 2009-08-16
I created the link and gave myself rwx access to the folder and files.

but if I want to open a file with the browser I get error 403 forbidden access
I changed permissions to 744 but that did not help.
Now I changed the permissions to 755 and I can open the files in the webbrowser but now I wonder if that is safe to do ?
giving execute permissions to everybody seems a bit dangerous.

any comments ?

kind regards
anatak

---

### Post by jrox717 on 2009-08-17
Whoops, I'm sorry. Directories need to have both read and execute permissions to open them graphically. It seems like you did that, though, and you still couldn't access them? Are you sure you own the files? If so then having the permissions be rwx------ (which is chmod 700, by the way) should be fine... I'm sorry I don't know more.
Oh, and if you don't want all your files (besides the directories) to be executable, then you might want to change them to 600, rw-------

---

### Post by anatak on 2009-08-17
thank you,

I got everything to work like I want it for now.
I ll experiment with the folder settings a bit more once I get the data in the folder and see what happens.

is there a close thread or solved thread option on this forum ?

---

### Post by anatak on 2009-08-19
Is it possible to setup the permissions so that files created in a directory are created with the same permissions as the directory ?

the directory has 755 permissions (read and execute for group and all) but when I create a file it is created with 744 permissions (only read for group and all)

How can I change this ?

---

