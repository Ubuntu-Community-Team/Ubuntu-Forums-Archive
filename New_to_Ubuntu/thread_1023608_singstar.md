---
title: "singstar"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jannevanhecke on 2008-12-28
i installed singstar ng without any problem.
But i read i have to place the txt files in the songs directory but i cant move the files in there because the access is denied.
Can anyone help?

---

### Post by Michael.Godawski on 2008-12-28
hey, 

```
sudo mv /path/to/txtfile /path/where/you/want/the/file/to/be
```

---

### Post by jannevanhecke on 2008-12-28
ow sorry but i dont understand that

---

### Post by Michael.Godawski on 2008-12-28
no problem :P

open up the terminal

applications > accessories > terminal

now we use the command **mv** to move the files
the prefix **sudo** gives us the needed super user rights

so for instance your txt file is located on the Desktop an you want to move it to the directory /singstar (this is just an example, I do not know the exact location of your singstar installation), so to move the txt file we run this command in terminal

```
sudo mv /home/Desktop/txtfile /singstar
```basically it is

```
sudo mv /location_of_file /new_location_of_the_file
```

---

### Post by jannevanhecke on 2008-12-28
ok thanks, is iet the same for a directory?

---

### Post by Michael.Godawski on 2008-12-28
> **jannevanhecke said:**
> ok thanks, is iet the same for a directory?

Don't know what you mean :P

---

### Post by jannevanhecke on 2008-12-28
the answer works with a single file, but does iert work with a whole directory or map?

---

### Post by Michael.Godawski on 2008-12-28
It should work with a folder, too.
Another option is to use nautilus with root privileges.
> Some folders and files can only be edited/copied/moved by the super user, or "root user". To open a file manager session as the root user, type the following command in the terminal:
     Code:
     ```
gksudo nautilus 
```However, it'll be easier for you to move stuff simply by using the command line in the terminal, like this:

     Code:
     ```
sudo mv folder destination 
```


---

### Post by ugm6hr on 2008-12-28
> **Michael.Godawski said:**
> Another option is to use nautilus with root privileges.

I think I would advocate this.  It is much easier for most people to use the mouse than the keyboard, until they understand file systems.

---

### Post by jannevanhecke on 2008-12-28
janne@janne-laptop:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initializedNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:11907): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:11907): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:11907): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-share extension

---

