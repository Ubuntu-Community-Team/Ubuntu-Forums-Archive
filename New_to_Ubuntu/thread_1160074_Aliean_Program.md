---
title: "Aliean Program"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-15
Ok,  so i found some programs for linux that are not for ubuntu.  so i looked online and saw some commands that i can use to install aliean to run those programs.  however when i type those commands into terminal i get a error message saying aliean is a invalid command.  can someone help.  ive tried everything i could find online.  i will show you what i get if you tell me where to look.  thank you

---

### Post by Dougie187 on 2009-05-15
I'm not sure, but I believe you mean alien?

Aside from that, you might try posting the commands you are trying to run, and their associated error messages.

---

### Post by bruno9779 on 2009-05-15
first install Alien:

```
sudo apt-get install alien
```

then alien the .rpm :
```

sudo alien package.rpm
```

Alien doesn't give an 100% implementation of some packages, so it is better to use the .deb version when available, and sometimes is only possible to compile from source.

more info here

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

---

