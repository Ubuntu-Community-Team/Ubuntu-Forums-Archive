---
title: "permission changes EASILY"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by adam2000 on 2011-08-11
Hi

My question is: how to change an .exe file's permission from read-only to executable in order to execute it? ( i have wine )
( I already tried chmod 755 and such and didn't work )

---

### Post by Paqman on 2011-08-11
Right click on the file > Properties > Permissions > Check "allow executing as a program"

---

### Post by dniMretsaM on 2011-08-11
Right click -> Properties -> Permissions -> Allow execution as a program (or something along those lines). Or chmod -x might do it.

---

### Post by papibe on 2011-08-11
Right click on icon, and select 'Open with Wine Windows Program Loader'.

Or in the command line:
```
$ wine yourprogram.exe
```
Hope it helps.

---

### Post by adam2000 on 2011-08-11
it dosent let me change it by the right click version

---

### Post by Iislsdum on 2011-08-11
Did you try sudo chmod 755?  Another thing you can try is the GUI (right click > Permissions > Allow running as executable, or something similar).  Lemme know how it goes!

---

### Post by Paqman on 2011-08-11
> **adam2000 said:**
> it dosent let me change it by the right click version

Who does it say the file is owned by? If it's not you then you'll need to use:
```
sudo chmod +x /path/to/file
```

---

### Post by ~!geek!~ on 2011-08-11
> **adam2000 said:**
> Hi

My question is: how to change an .exe file's permission from read-only to executable in order to execute it? ( i have wine )
( I already tried chmod 755 and such and didn't work )

Permission rules are same for all files in linux.
Use this link to learn about permissions in linux: 
[http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

---

### Post by CatKiller on 2011-08-12
> **adam2000 said:**
>  how to change an .exe file's permission from read-only to executable in order to execute it?

... It's on a cd, isn't it?

---

### Post by The Cog on 2011-08-12
I am guessing that CatKiller is right - you are trying to change file permissions on a CD. Yer can't do that. As someone else said, right-click the file and open with Wine windows program loader.

---

