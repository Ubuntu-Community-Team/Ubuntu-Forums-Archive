---
title: "Tarballs"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by l3gacy on 2009-05-27
I need help installing python 3.0.1 from the tarball that you download. I have never done this before and it would help tremendously if you could be as simple as possible.

---

### Post by amingv on 2009-05-27
Well, if you really want it as simple as possible then forget the tarball (which most likely would be source code for you to compile), open a terminal and do (if you're using jaunty):

```
sudo aptitude install python3.0
```

Run it by typing "python3.0" at the terminal or by using "#!/usr/bin/python3.0" as the shebang.

If not, decompress the file and look for a textfile named "INSTALL" or "README", install the dependencies listed and follow the instructions there.

---

### Post by Drate on 2009-05-27
Assuming the tarball you refer to is a tar.gz:

mv file.tar.gz ~
tar -xzvf file.tar.gz
cd file
sudo ./configure
sudo make && sudo make install


That's the usual method.  You unpack it, change directory to the new directory that should have been created, run a configure script if one is present (not always there), and then do the make, make install.

If it is not a .gz, but just a .tar, then take the "z" out of the above tar command.

---

### Post by l3gacy on 2009-05-28
Thank you amingv! The command worked!

---

