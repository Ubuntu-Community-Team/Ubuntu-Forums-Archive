---
title: "help installing .rpm package"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-08-08
okay i installed alien what would be the exact entry in the terminal to install this file

testdisk-6.11.3-1.i386.rpm

to convert it to deb file and then install or to install directly
tks

---

### Post by bilalakhtar on 2010-08-08
Just type
```
sudo alien --to-deb <DEBFILENAMEHERE>
```

This will give you a deb which you can install by double-clicking it.

Have fun with alien!

---

### Post by CharlesA on 2010-08-08
Isn't testdisk located in the repos?

---

### Post by Perfect Storm on 2010-08-08
Usually you can use the command **man** (which means manual) to get how to use the command.

eg.
```
man alien
```

press [q] to exit.

Note: It's not recommendable to use .rpm files in a Debian based linux structure especially if it's libraries or system files. Better if you can find a .deb

> Isn't testdisk located in the repos?

It is. 
```
sudo apt-get install testdisk
```

---

### Post by Perfect Storm on 2010-08-08
> **Artificial Intelligence said:**
> Usually you can use the command **man** (which means manual) to get how to use the command.

eg.
```
man alien
```

press [q] to exit.

Note: It's not recommendable to use .rpm files in a Debian based linux structure especially if it's libraries or system files. Better if you can find a .deb

> Isn't testdisk located in the repos?

It is. 
```
sudo apt-get install testdisk
```

---

### Post by rburkartjo on 2010-08-08
tks all just trying to work with alien. tks art about the heads up of it being in the repos

---

