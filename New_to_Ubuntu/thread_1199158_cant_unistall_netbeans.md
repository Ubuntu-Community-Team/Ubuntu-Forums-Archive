---
title: "cant unistall netbeans"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-28
i started learning java on my own and i needed an development kit
after some google i ended in netbeans
so i installed it but because some reasons i wanted to unistall it and install again
when i tried to reinstall it i noticed that it didnt download again the files...it just seemed to install 
..but that means when i unistalled the files/packages instead of being deleted they remained of the computer

some help to understand whats going on?
b

---

### Post by WRDN on 2009-06-28
You uninstalled the software, and when you went to reinstall it, Ubuntu found the debian package (.deb), in /var/cache/apt/archives, so it didn't download the file again.
You can manually remove the files in this cache, or just the command:

```
sudo apt-get clean
```

This will remove all the downloaded debian packages.

Note: Do not delete the partial folder at /var/cache/apt/archives/partial

---

### Post by heyyy on 2009-06-29
> **WRDN said:**
> You uninstalled the software, and when you went to reinstall it, Ubuntu found the debian package (.deb), in /var/cache/apt/archives, so it didn't download the file again.
You can manually remove the files in this cache, or just the command:

```
sudo apt-get clean
```

This will remove all the downloaded debian packages.

Note: Do not delete the partial folder at /var/cache/apt/archives/partial
thanks
should i type this?

> sudo apt-get clean netbeans

---

### Post by WRDN on 2009-06-29
No, apt-get clean is used to remove the downloaded debian packages (which hold the files to be installed), not programs themselves, so either run

```
sudo apt-get clean
```

Or, manually remove the debian packages

```
sudo rm [filename].deb
```

A quick way to remove downloaded packages related to NetBeans (though not guaranteed):

```
sudo rm *netbeans*
```

The above 2 commands must be run from within the archives directory.

---

