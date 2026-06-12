---
title: "Give permissions"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Funk66 on 2010-05-15
Hi

I had to reinstall ubuntu recently. After backup one of my folders remains without permissions, so I have to open nautilus as a sudo and give it permissions for me to open it, but it doesn't applies for all the subfolders.
Is there any command to do this for the folder and all its content or should I do it one by one?

Thank you

---

### Post by new_tolinux on 2010-05-15
You can do that in terminal:
```
chown -R username:group /path/to/folder
```Replace username and group with the username and groupname you want to give rights to. The -R option is for recursive.
After that:
```
chmod -R zzz /path/to/folder
```Replace zzz with the numbers of the rights you want to assign. Read = 4, Write = 2 and Execute = 1. So: if the owner can read+write+execute, the group can only read and "the rest of the world" has no access it will be:
```
chmod -R 740 /path/to/folder
```Replace /path/to/folder with the path to the actual folder.

Edit: you might have to use sudo before those commands, if the localuser has no rights to the specified folder and it's subfolders

---

### Post by Funk66 on 2010-05-15
Perfect, thank you again.

---

