---
title: "where is local package database?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by MichaelBurns on 2010-01-05
Does anyone know where is the local database that is supposedly created by running
```
sudo apt-get update
```
?
Is it a single file somewhere in the filesystem, or something more elusive?

---

### Post by diesch on 2010-01-05
Plain text files in */var/lib/apt/lists/*

---

### Post by MichaelBurns on 2010-01-05
Thanks, diesch.

What would happen if I deleted all of those files?  Could I then run
```
sudo apt-get update
```
replace them with fresh ones?

Does this command also update the database in /var/lib/dpkg/available and /var/lib/dpkg/status?

---

### Post by diesch on 2010-01-07
> **MichaelBurns said:**
> Thanks, diesch.

What would happen if I deleted all of those files?  Could I then run
```
sudo apt-get update
```replace them with fresh ones?


yes

> **MichaelBurns said:**
> 
Does this command also update the database in /var/lib/dpkg/available and /var/lib/dpkg/status?

No. /var/lib/dpkg/status is modified by dpkg if you change the state of a package, i.e. install it, remove it, mark it for some action, ...

/var/lib/dpkg/available "is mostly useless if you don't use dselect but an APT-based frontend: APT has its own system to keep track of available packages" as dpkg's manpage says.

---

### Post by firefly2442 on 2010-01-07
Just FYI or for anyone else that's reading this, the actual .deb packages you download are stored in:

```
/var/cache/apt/
```

Then head into the "archives" folder.

You can clean this out and remove the stored packages by running:

```
sudo apt-get clean
```

at the commandline.

---

