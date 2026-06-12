---
title: "I thought there was no secrets in ubuntu but. . ."
date: 2009-07-22
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-07-22
I keep getting  this message:

**THE FOLDER  CONTENTS CANNOT BE DISPLAYED**
You do not have the permissions necessary to view the contents of "lost+found".


why do I get that? is there a way to get the "permission"? I'm just curious now to see what my OS has found that was lost and is hiding from me.

---

### Post by bacil on 2009-07-22
lost+found is special filesystem folder you can gain privileges by using sudo

```
sudo ls -la /lost+found
```

---

### Post by AndyCee on 2009-07-22
"lost+found" is owned by Root. I forget what it's for, but if you want to look inside using nautilus, type alt+f2 and type:

```
gksudo nautilus
```

and navigate to the directory.

EDIT: Just looked it up and now I remember. If your computer shuts down badly, Ubuntu (and other *nix's) run a file-system check (fsck). Any bad or corrupted files will go in this folder, in case they can be recovered.

---

### Post by 289531.EXE on 2009-07-22
in doing this action, will i  in any way damage my OS? Is this code temporary or does it permanently grant me access? Should I be looking in there?

---

### Post by 289531.EXE on 2009-07-22
Thanks but that seemed to be  pointless. apparently theres nothing inside. strange, why would an empty folder be under lock and key?

---

### Post by The Cog on 2009-07-22
sudo (or gksu/gksudo for GUI apps) run the given command with root's id and privileges. It is temporary, and harmless unless you make a mistake - the command has the full rights to trash the system.

Read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by XCan on 2009-07-22
> **289531.EXE said:**
> Thanks but that seemed to be  pointless. apparently theres nothing inside. strange, why would an empty folder be under lock and key?

If it wasn't, every user would have the chance to see other users' files in case of caught corrupt files. It being empty for you at this time, is only good. :)

---

