---
title: "Platinum Arts Sandbox"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by leinad177 on 2010-03-13
**EDIT: as it turns out, i cannot install anything from playdeb...is it me or the site?**

how do i install this?
[http://sandboxgamemaker.com/download-sandbox.html](http://sandboxgamemaker.com/download-sandbox.html)

when i click on the link it takes me here
[http://www.playdeb.net/software/Sandbox%20Game%20Maker]("http://www.playdeb.net/software/Sandbox%20Game%20Maker")

then it says this when i click to install it

> Could not find package 'sandboxgamemaker'.

---

### Post by leinad177 on 2010-03-13
bump

---

### Post by Tikkyca on 2010-03-13
You can find installation on this website.
[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)

---

### Post by mechro on 2010-03-13
[http://packages.debian.org/unstable/games/sandboxgamemaker](http://packages.debian.org/unstable/games/sandboxgamemaker)

---

### Post by leinad177 on 2010-03-13
> **mechro said:**
> [http://packages.debian.org/unstable/games/sandboxgamemaker](http://packages.debian.org/unstable/games/sandboxgamemaker)

> 
Error: Dependency is not satisfiable: libenet0debian1


thats what comes up when i try to install the .deb

---

### Post by sandyd on 2010-03-13
download and install
[http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb")

```

sudo apt-get update
sudo apt-get install playdeb
```

or (reccomended)
```

wget -c http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb
sudo dpkg -i getdeb-repository*.deb
sudo apt-get update
sudo apt-get install playdeb
```

---

### Post by leinad177 on 2010-03-13
> **carlee said:**
> download and install
[http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb]("http://archive.getdeb.net/install_deb/playdeb_0.3-1%7Egetdeb1_all.deb")

```

sudo apt-get update
sudo apt-get install playdeb
```or (reccomended)
```

wget -c http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb
sudo dpkg -i getdeb-repository*.deb
sudo apt-get update
sudo apt-get install playdeb
```


i followed all those steps, then at the end i got this

> daniel@daniel-desktop:~$ sudo apt-get install playdeb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package playdeb


EDIT: lmfao, i forgot to do the very first step

---

### Post by sandyd on 2010-03-13
> **leinad177 said:**
> i followed all those steps, then at the end i got this



EDIT: lmfao, i forgot to do the very first step
eh, thought getdeb had the playdeb packages inside it too.
try the first steps...

---

### Post by mechro on 2010-03-13
> **leinad177 said:**
> thats what comes up when i try to install the .deb

The debian page gives you a list of dependencies for sandboxgamemaker. libenet0debian1 is listed as one of the dependencies so install that first.

---

### Post by leinad177 on 2010-03-13
thanks, it works now

---

