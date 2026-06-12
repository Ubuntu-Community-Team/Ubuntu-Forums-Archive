---
title: "Access Denied! want to load GIMP brushes"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by glennlad on 2009-01-22
[CENTER]Im trying to load some brushes into GIMP, but it keeps telling me that access is denied. Whys that? I am admin after all, and how do i get around this please? many thanks in advacne[/CENTER]

---

### Post by ET! on 2009-01-22
even if your are logged in as the admin certain actions require you to key in your password...try it in terminal with the prefix sudo (super user privilege)

---

### Post by glennlad on 2009-01-22
> **ET! said:**
> even if your are logged in as the admin certain actions require you to key in your password...try it in terminal with the prefix sudo (super user privilege)

It didnt ask me for a password :S

and how do i do the super user privlege please? 
Im new to linux

---

### Post by taurus on 2009-01-22
Are you trying to install some addons to gimp?  Can you give an exact example before you get that error message about permission?

---

### Post by glennlad on 2009-01-22
> **taurus said:**
> Are you trying to install some addons to gimp?  Can you give an exact example before you get that error message about permission?

[CENTER]No not plug-ins. Im trying to load brushes...I go into file system> usr> share> gimp> 2.0> brushes and move my brushes from the desktop into that folder. Then it tells me access denied.[/CENTER]

---

### Post by taurus on 2009-01-22
You need root privilege if you want to move or write something outside your $HOME directory.  And yes, you are the only user on your machine but it doesn't mean you are root.  You are just a user who happens to have root privilege.

From a terminal, run nautilus with root privilege and what would allow you to move/copy whatever you want to whichever directory you intend to.  Just be real careful with it because you could trash your system if you move or delete the wrong system files.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by glennlad on 2009-01-22
[CENTER]solved thanks guys i used "gksudo nautilus"[/CENTER]

---

### Post by glennlad on 2009-01-22
> **taurus said:**
> You need root privilege if you want to move or write something outside your $HOME directory.  And yes, you are the only user on your machine but it doesn't mean you are root.  You are just a user who happens to have root privilege.

From a terminal, run nautilus with root privilege and what would allow you to move/copy whatever you want to whichever directory you intend to.  Just be real careful with it because you could trash your system if you move or delete the wrong system files.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


[CENTER][SIZE="3"]Thank you =)[/SIZE][/CENTER]

---

