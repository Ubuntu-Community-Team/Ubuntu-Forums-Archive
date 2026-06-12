---
title: "Need to determine where an application installs itself"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by NewJack on 2010-09-06
I am looking to find an application/utility that will monitor where I install applciations and show me where it's remnants end up.  There is a program like this for Windows called RegShot.  It lets you take a snapshot of your system before and after installing an application and then reports what changes were made to the system (Registry entries, folder & file locations).  

Is there something like this for Linux?  I have tried searching Google with no luck.  Maybe I am using bad search terms.  

Any help would be greatly appreciated.  

Thanks!
Joe

---

### Post by t0p on 2010-09-06
**which** will tell you where a particular app is stored.  For instance, this command (in a terminal):

```
which gedit
```you get the feedback:
```

t0p@deimos:~$ which gedit
/usr/bin/gedit

```It's not exactly what you're looking for, but it's a helpful tool nevertheless.  The terminal command

```

dpkg --get-selections > file

```

will generate a list of installed programs, in a file called 'file'.  You could then run 

```

which <program-name>

```

for every program on the list, and you'll learn where everything is located.  A bit torturous and long-winded though...

---

### Post by Nythain on 2010-09-06
synaptic will show you what files a program installs and where it installs them to

---

### Post by gauravj on 2010-09-07
In synaptic, right click on installed package and select Properties.
It will have a tab for files installed.

While uninstalling applications, use sudo apt-get purge app-name,
to clean system of config files along with application files.

This will save you from trouble of remnant files.

---

### Post by NewJack on 2010-09-07
gauravj - Thanks for that info.  Exactly what I am looking for!!!  Cheers.

Thanks to all who responded!

Joe

---

