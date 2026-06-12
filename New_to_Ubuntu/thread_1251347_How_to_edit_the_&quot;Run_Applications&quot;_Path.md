---
title: "How to edit the &quot;Run Applications&quot; Path"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by mman426 on 2009-08-27
Hi, I was just wondering if anyone could tell me how to edit the path that "Run Application" checks for apps. I installed a program that it can't seem to find and I wanted to manually add it. Thanks

---

### Post by LowSky on 2009-08-27
you can add applications to the menu, note not all applications will automatically, especally programs that ar enot installed form the repos.

right click on the applications menu and click on edit, and you can go from there

---

### Post by mman426 on 2009-08-27
Hi, thank you for your help, but I am not trying to add it to the menu, I just want it do be launchable from "Run Applications" (Alt+F2) without having to type the full path to where it is. The funny thing is that this program added itself to the applications menu under accessories but does not show up under edit menu.

---

### Post by g.a. on 2009-12-20
same problem here
g.

---

### Post by akoskm on 2009-12-20
Add these lines to the end of your ~/.bashrc file:
```

PATH=/<execDirectory>:$PATH
export PATH

```,
where **execDirectory** represents the full patch to the executable's diretory.
If your executable file is in ~/bin the modify:
```

PATH=~/bin:$PATH
export PATH

```.

---

### Post by leef on 2009-12-20
You might try adding the directory that contains the executable to your users PATH variable by editing ~/.bashrc

find a line similar to this;

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/lee/src/android-sdk-linux/tools"

```

and add your new path, similar to how I've added "/home/lee/src/android-sdk-linux/tools".

Edit: akoskm beat me to it :).

---

### Post by g.a. on 2009-12-21
the .bashrc file should be used when you open a new shell and not for the "Run Application" command right?

I have modified the PATH in the .profile file and logged out & in and it worked.

thanks,
g.

---

### Post by akoskm on 2009-12-21
> **g.a. said:**
> the .bashrc file should be used when you open a new shell and not for the "Run Application" command right?

I have modified the PATH in the .profile file and logged out & in and it worked.

thanks,
g.

Doesn't matter how are you exporting that patch... It'll be added to the end (or beginning, depending on the syntax) of the $PATH environment variable with .bashrc and .profile too.

---

