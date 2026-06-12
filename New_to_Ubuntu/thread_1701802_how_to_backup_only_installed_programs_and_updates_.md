---
title: "how to backup only installed programs and updates in ubuntu 10.10"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by anjexe on 2011-03-06
how to backup only installed programs and updates in ubuntu 10.10
i dont want to back up any setting or driver
i am confused please help me in clear way

---

### Post by mrhhug on 2011-03-07
software needs to be recompiled to work properly on a different system. i would recommend that you note all the installed packages and reinstall them on your new system.

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

the only issue i could see with this method would be unattainable software source or non booting systems.

let us know if you have either of these situations and we'll offer our best efforts

---

### Post by wizard10000 on 2011-03-07
If you're not changing architecture (32-bit to 64-bit or vice versa) you can just back up /var/cache/apt/archives, restore it to the new machine and run

```
sudo apt-get update
```

That'll get all the applications migrated so you don't have to *download* them but it won't install them for you.

Better yet, try this -

```
dpkg --get-selections > installed-programs.log
```

That will dump a list of your currently installed applications to a text file.  You can then move the file to the new machine and do 

```
sudo dpkg --set-selections < installed-programs.log
```

then do

```
sudo apt-get dselect-upgrade
```

to install the packages.

Hope this helps -

---

### Post by anjexe on 2011-03-07
> **wizard10000 said:**
> If you're not changing architecture (32-bit to 64-bit or vice versa) you can just back up /var/cache/apt/archives, restore it to the new machine and run

```
sudo apt-get update
```That'll get all the applications migrated so you don't have to *download* them but it won't install them for you.

Better yet, try this -

```
dpkg --get-selections > installed-programs.log
```That will dump a list of your currently installed applications to a text file.  You can then move the file to the new machine and do 

```
sudo dpkg --set-selections < installed-programs.log
```then do

```
sudo apt-get dselect-upgrade
```to install the packages.

Hope this helps -

do i have to download any pachage in this way?


ia have a pc whit 32 bit ubuntu and AMD cpu
now i want to migrte to my new asus n43jf laptop whit corei3 CPU but also 32 bitubuntu (the same version)

---

### Post by wizard10000 on 2011-03-07
> **anjexe said:**
> do i have to download any pachage in this way?


ia have a pc whit 32 bit ubuntu and AMD cpu
now i want to migrte to my new asus n43jf laptop whit corei3 CPU but also 32 bitubuntu (the same version)

No, if you use --set-selections above and put the text file on the new laptop then use --get selections from the new laptop it'll intall all the packages automatically.  It will have to download all the packages, though.

---

### Post by anjexe on 2011-03-07
tnx
actully i installs all updates some programs left 
i think it is easar to dl them too
then make a compelet backup
so whats the best whay to have a complet back up?

---

