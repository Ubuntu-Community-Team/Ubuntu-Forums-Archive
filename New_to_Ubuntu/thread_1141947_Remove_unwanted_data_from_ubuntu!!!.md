---
title: "Remove unwanted data from ubuntu!!!"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by alok.phonexsia on 2009-04-28
How to remove unwanted data from my ubuntu so that i an free some space there, i have deleted all the other files only the system files dont know which one is important or which one is not important...
please help
thank you very much

---

### Post by taurus on 2009-04-28
How much space do you have for Ubuntu?

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

### Post by unutbu on 2009-04-28
Here is a nice guide on how to find disk hogs and free up disk space: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by MontelEdwards on 2009-04-28
> **taurus said:**
> How much space do you have for Ubuntu?

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Now what exactly dose this do?
 Is it like the Janitor program?

---

### Post by taurus on 2009-04-28
> **monteledwards said:**
> Now what exactly dose this do?
 Is it like the Janitor program?

```

       clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

```

---

### Post by MontelEdwards on 2009-04-28
> **taurus said:**
> ```

       clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

```
hmmm,
thanks! that will really come in handy!
oh, and I use bleachbit too it is like CCleaner for Windows.
```
sudo apt-get install bleachbit
```

---

### Post by oldos2er on 2009-04-28
Install localepurge.

---

