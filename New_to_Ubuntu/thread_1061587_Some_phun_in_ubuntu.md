---
title: "Some phun in ubuntu?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-05
I am trying to run the game [Phun](http://www.phunland.com/wiki/Home) under ubuntu 64bit and I installed all the libaries it said it wanted and it even loaded once or twice for me, but now I get this error when trying to load it: ```
./phun.bin: error while loading shared libraries: libboost_filesystem.so: cannot open shared object file: No such file or directory
```

Any ideas what happened to cause or if maybe there is a .deb of phun for ubuntu to install this easier?

~Jeff

---

### Post by hyper_ch on 2009-02-06
just a guess: it can't ind that file

solution: find out what package contains that file

(1) install apt-fil
```

sudo apt-get install apt-file

```

(2) update apt-file
```

sudo apt-file update

```

(3) search apt-file for a file
```

apt-file search FILENAME

```

(4) install the according package.

---

