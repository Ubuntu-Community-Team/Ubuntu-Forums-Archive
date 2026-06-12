---
title: "beginners question about permissions?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by casmok on 2009-03-09
One of the things I dont quite understand is Permissions. Well I sort of do (emphasis on sort of here!) Theres a tutorial on Psychocats but that comes more from the command line perspective. Here's what I cant figure out and want to do:

In the /home/"user name"/examples directory there are a pile of example files that I'd like to delete. I cant delete them as they are root permission and if I go to properties it wont let me change the permissions as "I'm not the owner" 

So how do I change the permissions? I'd like to know how to do this by both the command line AND on the GUI if possible. 

Many thanks
Mike

---

### Post by LowSky on 2009-03-09
there is no way to do it from the GUI, sorry at leat not in Ubuntu (you canot log in with Root)
from a gnome terminal
```
gksu nautilus
```
it will open the file manager with root access... what ever you delete will be gone forever, be careful

---

### Post by taurus on 2009-03-09
In this case, change the ownership of those files from root to your login name would allow you to do whatever you want with those files, deleting them if you wish.

```
cd ~/examples
sudo chown *username* *
```
Replace *username* with your login name.

Or delete them with root privilege.

```
cd ~/examples
sudo rm *
```

---

### Post by kanikilu on 2009-03-09
If those example files accidentally got owned by root, the easiest way to deal with it in a GUI is to start nautilus with gksudo. Ironically, this has to be done with the commandline. Press ALT+F2 or go to Applications > Accessories > Terminal and type: ```
gksudo nautilus
``` enter your password when asked, and a file manager window owned by root should show up. Now just browse to /home/username and you can delete those example files.

Alternatively, you can do it all from the commandline. Open a terminal and you should be in your home directory. Now you can use ```
sudo chown username exampleFile
``` to change the ownership of *exampleFile* to your account. Then use **rm** to remove the files.

For more information ```
man rm
man chown
man chgrp
man chmod
```

---

### Post by vanadium on 2009-03-09
"/home/"user name"/examples" is a symbolic link pointing to a common system directory where you do not have permissions. If you want to "customize" this directory:

1) rename "examples" to "examples_old"
2) Create a new directory "examples"
3) Copy all files from "examples_old" to "examples"
4) Delete "examples_old" (you are only deleting the link)
5) Change "examples" to your heart's content.

---

### Post by protargol on 2009-03-09
To change the permissions on the files you can use the 'chmod' command.

There are several ways to use that command to change permissions for the owner, group, and others.

One example is:
```
chmod 644 *file*
```

This will give the owner read and write permissions, while the group and others will only have read-only permission.

If you are not the owner, you'll have to add *sudo* to the beginning in order to overcome that.

But taurus is correct in pointing out that you could just change ownership to remove them.

---

### Post by casmok on 2009-03-09
> **taurus said:**
> In this case, change the ownership of those files from root to your login name would allow you to do whatever you want with those files, deleting them if you wish.

```
cd ~/examples
sudo chown *username* *
```
Replace *username* with your login name.

Or delete them with root privilege.

```
cd ~/examples
sudo rm *
```

OK thanks everyone. Lots to digest here..I do appreciate your advice/comments!

But when I enter what taurus said into terminal I get this. Why?

"mbdb@M2000:~$ cd ~/examples
bash: cd: /home/mbdb/examples: No such file or directory
mbdb@M2000:~$

---

### Post by casmok on 2009-03-09
> **LowSky said:**
> there is no way to do it from the GUI, sorry at leat not in Ubuntu (you canot log in with Root)
from a gnome terminal
```
gksu nautilus
```
it will open the file manager with root access... what ever you delete will be gone forever, be careful

OK that worked pretty slick. Yes Ill be very careful but I dont think I need things like boring music clips or "fables" ;)

Thanks

---

### Post by protargol on 2009-03-09
> **casmok said:**
> 
But when I enter what taurus said into terminal I get this. Why?

"mbdb@M2000:~$ cd ~/examples
bash: cd: /home/mbdb/examples: No such file or directory
mbdb@M2000:~$

You get that because the directory "/home/mbdb/examples" does not exist.  The "~" just defines your home directory.  Wherever your examples folder is is what you need to *cd* into.

I'm guessing that your mistake is a case-sensitivity one.  Remember, case matters in linux.  *Examples* is not the same as *examples*

Try this:
```
cd ~/Examples
```

Should work this time

---

### Post by taurus on 2009-03-09
> **casmok said:**
> OK thanks everyone. Lots to digest here..I do appreciate your advice/comments!

But when I enter what taurus said into terminal I get this. Why?

"mbdb@M2000:~$ cd ~/examples
bash: cd: /home/mbdb/examples: No such file or directory
mbdb@M2000:~$

Where is that directory?

```
ls -la ~
```

---

### Post by The Cog on 2009-03-09
As a general rule, I don't think you should go taking ownership of files outside your home directory. If they're outside your home directory then they really shouldn't be owned by you. Instead, adopt root priviledges with sudo or gksu to get the power you need and leave the ownership alone.

---

