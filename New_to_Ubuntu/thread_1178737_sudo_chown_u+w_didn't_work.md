---
title: "sudo chown u+w didn't work?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by punkbohemian on 2009-06-04
I'm trying to change the permissions on a certain folder. I have to be able to add/edit files to/in this folder in order to mod a game. IIRC, sudo chown u+w should let me change the permissions of the folder, or at least let me add some files to it. But after running that line, I still can't do anything with this folder. I'm sure it's an error on my part, but I'm not sure what I did wrong. Does anyone else know? Thanks.

---

### Post by Celauran on 2009-06-04
You want chmod, not chown.

---

### Post by shifty_powers on 2009-06-04
chown changes ownership. look at chmod command...

---

### Post by punkbohemian on 2009-06-04
So would "sudo chmod u+w foldername" work or am I supposed to do "sudo chmod -R foldername"? I want to make absolutely sure I know what I'm doing before I start fiddling about.

---

### Post by Celauran on 2009-06-04
```
sudo chmod u+w directory
```
will add the write bit to that directory. If you want to do it recursively, try this:

```
find . -type d -exec chmod u+w {} \;
```

---

### Post by lswb on 2009-06-04
"sudo chmod u+w DirectoyName" will allow the user (owner) to write to the directory. If the folder is owned by root, a non-root user will still not necessarily be able to write to the directory. "sudo chmod o+w DirName" will allow any user to write to the directory. "write" in the context of a directory means to be able to create or delete a file in that directory. If there are pre-existing files in that directory owned by other users, they may or may not be readable/writeable depending on their permission settings.

The -R option to chmod will perform the operation recursively through the directory, changing the permissions to all files and subdirectories.

See the man page for chmod (type "man chmod" in a terminal) for all the gruesome details, if you have questions post again. HTH.

---

