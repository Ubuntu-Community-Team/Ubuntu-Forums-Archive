---
title: "How To Change the Owner of directory in ubuntu"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by a_elsayed2010 on 2009-04-10
Hello ,

I'm new in Ubuntu linux 8.10
i install it after windows 
i have some files i want to delete them 
but it was created using windows before
i don't have permission to delete them
so what can i do to delete them

thanks in advance

---

### Post by Dougie187 on 2009-04-10
Well, if it is a directory that you what to change the owner of. You can type (in a terminal)
```
chown -R *username* *directoryname*
```

chown is "change owner", the -R flag applies the changes recursivly to all files and folders inside that folder. 

You might have to add sudo to the beginning to do that as root if you don't have permissions for it.

You can read the man page for more information.

---

### Post by drs305 on 2009-04-10
The safest way is probably do it via a file browser with root privileges:
```
gksudo nautilus
```

This will open up nautilus and allow you to delete any file on the system - including system files - so be careful. 

The deleted files will be owned by root as well, so you could delete them using SHIFT-DELETE, which bypasses the trash bin. If you use this method, any file you delete cannot be recovered, so again, be careful. The other way to get rid of root trash is to delete the files in the normal manner and when you are done, go to /root/.local/share/Trash and use SHIFT-DELETE to delete that folder. If you don't get rid of root trash before closing the browser they will remain in the root trash bin and take up space on your system. They won't be deleted by emptying your own trash bin in the normal manner.

---

### Post by drowner on 2009-04-10
> **drs305 said:**
> The safest way is probably do it via a file browser with root privileges:
```
gksudo nautilus
```

This will open up nautilus and allow you to delete any file on the system. Including system files - so be careful. The deleted files will be owned by root as well, so you could delete them using SHIFT-DELETE, which bypasses the trash bin. If you use this method, any file you delete cannot be recovered, so again, be careful.

That doesn't sound safe at all!

---

### Post by LowSky on 2009-04-10
> **drowner said:**
> That doesn't sound safe at all!

Its as safe a logging onto a WIndows XP computer and using Windows Explorer to find and delete files.

Just dont delete the improtant stuff.

---

### Post by drs305 on 2009-04-10
> **drowner said:**
> That doesn't sound safe at all!

Any tampering with system files can potentially harm a system. That is why the user in ubuntu can access only his/her files and not those of the system. It is a very safe way to run things.

If a user wants to delete or alter files not owned by him/her, the only way to do so is to temporarily gain administrator/root powers (or get the owner to do it). The options include:
1. Removing the files using a command with sudo.
I don't generally offer this as a solution, as a single typo can wipe out the entire system. Plus this method is not practical if the user wants to delete specific individual files.

2. Changing ownership of the files to the user, using the "chown" command with "sudo". Then deleting the files as a normal user.
I like this option, but the reality is the user still must use the sudo and chown commands simultaneously, and chowning the wrong folders can lead to a reinstall if not done properly.

3. Opening a file browser as root and then browsing the files via a gui and selectively highlighting the file(s) and deleting them. 
A user can certainly trash their system by deleting the wrong files, but a user is presented with a graphical file browser, which most users are comfortable with. My advice varies with the experience level of the user, and in this case is what I recommended.

4. One option I didn't mention and could have would be to go back into windows and do it from there. That would be a legitimate option. This being an ubuntu forum, I presented ubuntu methods of dealing with the issue.

One of the best things about linux is the multiple ways to accomplish the task. Others are always free to offer different solutions and frequently do so on these forums; in fact, I encourage it.

I don't disagree that any invocation of root powers involves the potential to do harm to the system. Life, and computer systems, are not risk free. We can just try to minimize the risk.

---

