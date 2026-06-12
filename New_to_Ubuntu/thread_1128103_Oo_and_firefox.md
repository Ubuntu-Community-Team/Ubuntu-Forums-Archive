---
title: "Oo and firefox"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by DKCorey on 2009-04-17
I'm trying to get used to ubuntu and wondered why I can't upgrade open office or firefox to the latest version?

Thanks!
DC

---

### Post by por100pre1 on 2009-04-17
Every Ubuntu release uses the last stable version of those programs at the time of its release with all subsequent *security* patches. Which version of **Ubuntu** are you using?

---

### Post by lolol i r linux noob on 2009-04-17
are u using intrepid.

because firefox is already the latest version.

if u want open office 3 do this:

open a terminal and type

```
sudo gedit /etc/apt/sources.list
```

Then add the following lines to the bottom of the file:

```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
save and exit.

Then open terminal again and type

```
sudo apt-get update && sudo apt-get dist-upgrade
```

open office 3 is installed.

---

### Post by freesitebuilder on 2009-04-17
Ubuntu 9.04 releases on 23 April, and that includes OO3 I think.

---

### Post by lolol i r linux noob on 2009-04-17
to freesitebuilder:

yes ur right.

---

