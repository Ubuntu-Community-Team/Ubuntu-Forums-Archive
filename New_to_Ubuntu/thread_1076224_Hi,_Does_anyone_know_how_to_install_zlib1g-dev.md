---
title: "Hi, Does anyone know how to install zlib1g-dev?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by gaoxt1983 on 2009-02-21
gao@gao-desktop:~/libraries$ sudo apt-get install zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3.3.dfsg-12) but 1:1.2.3.3.dfsg-12ubuntu1 is to be installed
E: Broken packages




I don't know what's going on :(

---

### Post by zvacet on 2009-02-21
```
sudo apt-get -f install
```

or 

```
sudo dpkg --configure -a
```

---

### Post by gaoxt1983 on 2009-02-22
I'm sorry, but "sudo apt-get install -f zlib1g-dev" doesn't help. Please help me, I can't install libssl-dev because of that? Is there a solution?

---

### Post by brian_p on 2009-02-22
> **gaoxt1983 said:**
> 

The following packages have unmet dependencies:
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3.3.dfsg-12) but 1:1.2.3.3.dfsg-12ubuntu1 is to be installed
E: Broken packages

zlib1g (= 1:1.2.3.3.dfsg-12) is a package from the Debian archive. The apt database wants to install it because it is needed by zlib1g-dev.

1:1.2.3.3.dfsg-12ubuntu1 is a Ubuntu (Intrepid/Jaunty) package. This is all apt can find and it does not like it.

Examine your /etc/apt/sources.list.

---

