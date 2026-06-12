---
title: "Stop files being deleted"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by yanewby on 2009-01-25
I have a large number of music and image files that I would like to protect from accidental deletion.

I am aware that you can change the permissions on files and folders (using chmod) but I am not sure of the best settings and I would like some advice.

This is what I would like:

1) The files/folders should not be able to be deleted.
2) Folders should allow other items to be added to the same folder.
3) A command that I can use to alter the files/folders recursively through a number of levels of folder (as some of the image folders go down 4 or 5 levels) - for instance chmod 777 /home/user/Desktop/Pictures/*/*.jpg.

Thanks!

---

### Post by diablo75 on 2009-01-25
I think what I would do is open a terminal window and type:

```
sudo nautilus
```

This will open up a file browser as root.

Now browse to the folder(s) you want to protect.  Right-click>Properties>Permissions(tab).  Change the owner from yourself to root, and make everything read-only.  There's a button you can click near the bottom that will apply the settings across all files and sub-directories within.

---

### Post by yanewby on 2009-01-25
> **diablo75 said:**
> I think what I would do is open a terminal window and type:

```
sudo nautilus
```

This will open up a file browser as root.

Now browse to the folder(s) you want to protect.  Right-click>Properties>Permissions(tab).  Change the owner from yourself to root, and make everything read-only.  There's a button you can click near the bottom that will apply the settings across all files and sub-directories within.

Thanks for the quick reply but I don't think that would allow me to add new files/folders to the existing files/folders without using sudo every time.

Is there another way?

---

### Post by amauk on 2009-01-25
you can use the "Sticky bit" flag
see here for details
[http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php]("http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php")
> Sticky bits are mainly set on directories.
If the sticky bit is set for a directory, only the owner of that directory or the owner of a file can delete or rename a file within that directory.

change the ownership of all file/directories under the top music dir, to owner "root", group "users"
```
chown -R root:users /path/to/music
```

then change the permissions to allow full read/write access to all users, but use the sticky bit flag to restrict renaming and deletion to the owner (root)
```
chmod 1770 /path/to/music
```

Now, any user can read & write to locations under the top dir, but only root can rename or delete

---

### Post by diablo75 on 2009-01-25
> **amauk said:**
> you can use the "Sticky bit" flag
see here for details
[http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php]("http://www.techcuriosity.com/resources/linux/advanced_file_permissions_in_linux.php")


change the ownership of all file/directories under the top music dir, to owner "root", group "users"
```
chown -R root:users /path/to/music
```

then change the permissions to allow full read/write access to all users, but use the sticky bit flag to restrict renaming and deletion to the owner (root)
```
chmod 1770 /path/to/music
```

Now, any user can read & write to locations under the top dir, but only root can rename or delete

Much better solution.  I'll have to try this out myself.

---

### Post by yanewby on 2009-01-25
> **amauk said:**
> you can use the "Sticky bit" flag
see here for details


Thank-you!  I thought there must be something like this and this seems to be the perfect solution.

---

