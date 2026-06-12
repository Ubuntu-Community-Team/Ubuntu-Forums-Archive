---
title: "Installing Bash 3.2"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by billcurtis14 on 2009-06-18
I want to install Bash 3.2 for a class. I'm using 3.2 because it's the version my professor is using. I have downloaded bash-3.2.tar.gz.sig and bash-3.2.tar.gz. Where do I go from here?

---

### Post by SOULRiDER on 2009-06-18
[http://packages.ubuntu.com/jaunty/bash](http://packages.ubuntu.com/jaunty/bash)
Apparently we have 3.5 in the repos, so thats what you should have.

To install what you have downloaded you will need to compile it.

---

### Post by billcurtis14 on 2009-06-18
You can delete this now if you want. If I knew how, I would.

---

### Post by monkey56657 on 2009-06-18
Hello. 

$ tar -xvzf bash-3.2.tar.gz
$ cd bash-3.2
$ ./compile
$ make
$ make install

^ This is the basic steps to compile this version of bash so fingers crossed the basic steps are enough in this case :)

Jonathan.

---

### Post by niteshifter on 2009-06-18
Hi,

In all likelyhood you already have bash 3.2, to see what version you have in a terminal type:
```
bash --version
```

Jaunty is not bash 3.5. There is no bash 3.5. See [ftp://ftp.gnu.org/gnu/bash/](ftp://ftp.gnu.org/gnu/bash/) (the 'home' of bash).

Jaunty is 3.2-5ubuntu1. The new bash is 4.0

---

