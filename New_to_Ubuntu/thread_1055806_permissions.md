---
title: "permissions"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by mhh91 on 2009-01-31
how can i set permissions for the whole drive?


every time i do it on nautilus,it doesn't change,even though i tell it to apply the changes to the included folders


thanks for any help :)

---

### Post by gjoellee on 2009-01-31
I recommend that the permissions are as they are by default. Changing permissions in folder as ie: /usr will be a HUGE security flop.

 You can however use terminal:
```
gksu nautilus
``` and you have the root permissions, it is not recommended to do that unless you abselutely have to! It is dengarous and[COLOR=Red] doing a little mistake (just deleting the wrong folder) may harm your system!

[COLOR=Black] You can use chmod commands.
 Eaxmple:
```
sudo chmod 755 /path/to/folder
```

you must however know what the different values does!
[/COLOR][/COLOR]

---

### Post by mhh91 on 2009-01-31
i won't delete anything,i just want to access my music collection :D


EDIT:i still have the same problem,nautilus doesn't change the permissions of the included files

---

### Post by Elfy on 2009-01-31
Is it on a seperate drive? What is the path to it?

---

### Post by Cresho on 2009-01-31
very easy!

just follow the directions i posted for this guy.  Just look for my name in the various posts.  He is a happy dude now.

[http://ubuntuforums.org/showthread.php?t=1050615](http://ubuntuforums.org/showthread.php?t=1050615)

---

### Post by mister_pink on 2009-01-31
Is it a windows drive? Ie fat or ntfs? If so, it won't allow changing permissions, you have to set them in fstab. I'll give you some help on that if you say its the case.

---

### Post by mhh91 on 2009-01-31
> **mister_pink said:**
> Is it a windows drive? Ie fat or ntfs? If so, it won't allow changing permissions, you have to set them in fstab. I'll give you some help on that if you say its the case.

no,it's "ext3"

---

### Post by Elfy on 2009-01-31
I've used chown and chmod to deal with that, change user to your user name

sudo chown user.user /path/to/folder

then 

sudo chmod 770 /path/to/folder

would give user and user's group read,write and exec rights with nothing for others

Check this page out on chmod - there's a little box to fiddle with the numbers to show how it changes

---

