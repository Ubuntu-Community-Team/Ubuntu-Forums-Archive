---
title: "cp, not a directory"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by M!K3_$ on 2010-10-31
Hello,

I'm trying to write a script to be used in a crontab job, but i'm running into problems with the script

```
cp /home/minecraft/Kelowna Minecraft/level.dat /home/minecraft/backups/backup_`/bin/date +\%Y-\%m-\%d-\%H` >> /home/mike/minecraft/backups/backup.log 2>&1
```

(i know, its for minecraft)


I'm getting erros in my log saying
```
cp :target 'home/minecraft/backups/backup_2010-10-31-00.dat' is not a directory

```

well i know that.

i want to be able to copy from the existing level.dat file to the backup file. Not into a directory.

Suggestions?

---

### Post by spiky001 on 2010-10-31
should that be cd? Sorry missed you were copying my mistake

---

### Post by spiky001 on 2010-10-31
should Kelowna Minecraft be "Kelowna Minecraft" with the ""

---

### Post by M!K3_$ on 2010-10-31
wow i'm tired. what you said made me look more closely and i figured out the problem.

i was trying to backup
```
/home/minecraft/Kelowna Minecraft/level.dat
```
when i should have done
```
/home/mike/minecraft/Kelowna Minecraft/level.dat
```


*sigh*

---

