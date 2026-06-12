---
title: "Aptitude command that lists available updates without installing"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by eli_12345 on 2010-08-20
Hi,
i'm looking for aa apt-command that lists all available updates in the console without installing them...
cheers,
eli

---

### Post by Bachstelze on 2010-08-20
I don't know about Aptitude but you can use the -s flag of apt-get:

```
sudo apt-get -s upgrade
```

---

### Post by oldos2er on 2010-08-20
Using aptitude or apt-get? In aptitude, press Ctrl-t then u to update the package list, then Enter to show the list of upgradeable packages.

---

### Post by eli_12345 on 2010-08-21
Thanks for the quick repies :)
@Bachstelze: sudo apt-get -s upgrade seems to install the packages, but i need to just have a look at the available packages

What i'm looking for is a command that can be integrated in a batch-script and that shows all the packages which are available for an upgrade in the console...
It doesn't matter if it is an aptitude or apt-get command or something else, but it should show the content that the Ubuntu upgrade manager shows when it is started.

---

