---
title: "What is the default shell in ubuntu distribution and how to assing it to a new user?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by legolas_w on 2010-02-05
Hi
Thank you for reading my post.

Does you know what is a good shell to assign to a user when we are creating a user using useradd command? I want the shell to have all capabilities of the default ubuntu shell like using TAB for auto-complete and other things. 


Thanks.

---

### Post by audiomick on 2010-02-05
As far as I know, the default shell in Ubuntu is bash.

I do not believe that you have to assign a shell to a new user. When the new user opens a terminal, he will get the same shell that the first user gets.

---

### Post by bluefrog on 2010-02-05
bash is default
adduser or the GUI add/remove user
useradd will give sh as default

---

### Post by audiomick on 2010-02-05
> **bluefrog said:**
> bash is default
adduser or the GUI add/remove user
[COLOR=Red]useradd will give sh as default[/COLOR]
not bash? any idea why not?

---

### Post by bluefrog on 2010-02-05
cause you are not supposed to use useradd. if you do you are supposed to know what you do. why is the sky blue?

adduser is what you want to use.

---

### Post by Bachstelze on 2010-02-05
> **audiomick said:**
> not bash? any idea why not?

Why would it? Assigning a POSIX-compliant shell seems like a good thing to me.

---

### Post by legolas_w on 2010-02-05
Hi,

what is the difference between adduser and useradd except for the assignment of the default shell?

thanks

---

### Post by Bachstelze on 2010-02-05
HOw about you try and find out? ;)

In a nutshell, useradd is non-interactive: you type the command, and it creates the users based on the prameters you give it, without asking further questions. adduser, on the other hand, is interactive: it will prompt you for information you don't supply on the command like (the user's login shell, among others).

---

### Post by audiomick on 2010-02-05
From 
```
man adduser
```
```
DESCRIPTION
       adduser  and  addgroup  add users and groups to the system according to
       command    line    options    and    configuration    information    in
       /etc/adduser.conf.   They  are  friendlier  front ends to the low level
       tools like useradd, groupadd and usermod programs, by default  choosing
       Debian  policy conformant UID and GID values, creating a home directory
       with skeletal configuration, running a custom script,  and  other  fea&#8208;
       tures.  adduser and addgroup can be run in one of five modes:

```

from
```
man useradd
```
```
DESCRIPTION
       useradd is a low level utility for adding users. On Debian,
       administrators should usually use adduser(8) instead.

       When invoked without the -D option, the useradd command creates a new
       user account using the values specified on the command line plus the
       default values from the system. Depending on command line options, the
       useradd command will update system files and may also create the new
       user´s home directory and copy initial files.

       By default, a group will also be created for the new user (see -g, -N,
       -U, and USERGROUPS_ENAB).

```

---

