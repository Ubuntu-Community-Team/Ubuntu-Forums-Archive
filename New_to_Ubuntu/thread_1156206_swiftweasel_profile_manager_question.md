---
title: "swiftweasel profile manager question"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by northwestuntu on 2009-05-11
im using swiftweasel 3.10 and trying to restore a profile using the febe extension.  

the way i run swiftweasel is by extracting the archive in a directory and hitting swiftweasel to run.  i can't figure out how to get to profile manager so i can restore a profile.

thanks

---

### Post by kellemes on 2009-05-11
Probably something like..
```
swiftweasel -profilemanager
```

---

### Post by northwestuntu on 2009-05-11
yeah tried that one and say's command not found.  i also tried sw3 -profilemanger

also tried swiftweasel3 -profile manager.

:confused:

---

### Post by kellemes on 2009-05-11
> **northwestuntu said:**
> yeah tried that one and say's command not found.  i also tried sw3 -profilemanger

also tried swiftweasel3 -profile manager.

:confused:

Well, I'm not using Swiftweasel so can't do this myself..
But you can always check the command that's run when you select Swiftweasel from the menu.. So startup your menu-editor and find the Swiftweasel entry.
You can also enter "swift" from commandline and hit the TAB-key to see what comes up.

Edit: A google search came up with..
```
swiftweasel32 -profilemanager
```

---

### Post by northwestuntu on 2009-05-11
got the same response.  no command found.  

:confused:

---

### Post by northwestuntu on 2009-05-15
update!!

you need to have the full path to the folder in the terminal then add -profilemanager at the end and it works.

---

