---
title: "Force Emnty Trash {FIX}"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by JohnsShadow on 2009-02-10
hey guys earlyer this week i was haveing problems getting a file to delete from the trash
together with a friend we investigated the problem and solved it

now be shure to COPY THE ENTIRE CODE if you miss one letter you could delete the whole system 

          COPY ENTIRE CODE OR DIE

```
rm -rf /home/<username>/.local/share/Trash/*
```

now <username> refers to the name of your user
for me its

```
rm -rf /home/jsx/.local/share/Trash/*
```

and now we have a special segment called "understanding the code your copying and pasteing"

```
"rm" stands for remove but it usually pretains to a single file
```

```
"rmdir" will remove the directory of where you target it but only an empty directory
```

```
"rm -rf" will delete all the files and folders in the directory you target with "*" NOTE: if you type in rm -rfinto your home directory you will delete all the files in your home directory
```

special thanks to 
JohnsShadow (me)
Austus
Realn0whereman

---

### Post by Elfy on 2009-02-10
Good job, so you are aware - instead of /home/user you can use ~/ as a shortcut so that

rm -rf ~/.local/share/Trash/*

works for anyone :)

There is a comprehensive howto here for other disk full issues including trash

[http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by JohnsShadow on 2009-02-10
> **forestpixie said:**
> Good job, so you are aware - instead of /home/user you can use ~/ as a shortcut so that

rm -rf ~/.local/share/Trash/*

works for anyone :)

There is a comprehensive howto here for other disk full issues including trash

[http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

i did not know that but thank you :D

---

