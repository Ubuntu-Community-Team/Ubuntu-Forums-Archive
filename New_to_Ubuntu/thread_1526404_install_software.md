---
title: "install software"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by arawa on 2010-07-08
i have dowloaded flock browser n save in the folder , n now how iam going to installit.
(flock-2.6.1.en-US.linux-i686.tar.bz2),thanks..

---

### Post by wingman358 on 2010-07-08
first use bunzip2 like so:

```

#  bunzip2 flock-2.6.1.en-US.linux-i686.tar.bz2

```that will leave you with a file flock-2.6.1.en-US.linux-i686.tar which you can extract further:


```

#  tar xvf flock-2.6.1.en-US.linux-i686.tar

```where** x** means e**X**tract, **v** means **V**erbose (print information), and **f** means use **F**ile ...

the second command will extract the contents of the archive and place them into a directory of the same name

when you get to this point try:

```

# cd flock-2.6.1.en-US.linux-i686
# sudo ./configure
# sudo make
# sudo make install

```

---

### Post by arawa on 2010-07-08
thanksyou my friend..i think i gat it.thanks so much..

---

