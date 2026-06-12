---
title: "Bulk file permission changes"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-01-12
I recently installed karmic on my laptop, overwriting hardy

I took a back-up of my /home dir , then copied them back into my /home from my ext drive

But i forgot the permissions are different and the only way to access them is through sudo

There a a look of directories and even more files with those that i nee to change the permissions on to make life easier

what is the easiest way to do this as a batch/ bulk change

---

### Post by Ankur Dave on 2010-01-13
To bulk-change the ownership of a directory, try the following command in a terminal:

```
sudo chown -R $USERNAME: <directory>
```

The [FONT="Courier New"]-R[/FONT] option is short for [FONT="Courier New"]--recursive[/FONT]; it changes the permissions of the directory and everything it contains. The colon (":") after the username tells [FONT="Courier New"]chown[/FONT] to change the user *and* the group.

Make sure to replace "<directory>" with the directory you want to change. That's probably [FONT="Courier New"]/home/$USERNAME[/FONT], or [FONT="Courier New"]~[/FONT], in this case.

Hope that helps!

---

### Post by audiomick on 2010-01-13
Hallo.
My home has a few things in it belonging to root.
They are
.dbus  directory   drwx------
.ure   directory   drwxr-xr-x
karmic.list   text file   -rw-r--r--
.nvidia-settings-rc   text file   -rw-r--r--

If you have any of these, I would suggest leaving them like that.

---

### Post by Ducatiboy Stu on 2010-01-13
> **Ankur Dave said:**
> To bulk-change the ownership of a directory, try the following command in a terminal:

```
sudo chown -R $USERNAME: <directory>
```

The [FONT="Courier New"]-R[/FONT] option is short for [FONT="Courier New"]--recursive[/FONT]; it changes the permissions of the directory and everything it contains. The colon (":") after the username tells [FONT="Courier New"]chown[/FONT] to change the user *and* the group.

Make sure to replace "<directory>" with the directory you want to change. That's probably [FONT="Courier New"]/home/$USERNAME[/FONT], or [FONT="Courier New"]~[/FONT], in this case.

Hope that helps!

Thanks

Worked a treat, I know there was an easy way, just could remember the command

:popcorn:

---

