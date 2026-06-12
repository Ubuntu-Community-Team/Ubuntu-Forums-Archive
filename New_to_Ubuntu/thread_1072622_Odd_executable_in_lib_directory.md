---
title: "Odd executable in /lib directory"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-17
Anyone know what this file is or what preocess it it related to ?

**[SIZE="3"]klibc-zUXi_KjK5ZQAIyc8jlwme9T6a4U.so[/SIZE]**



It's located in my /lib folder as an executable "so" file.


If I was still in Windows I would think my computer was infected with a virus with a name like that :(

---

### Post by sisco311 on 2009-02-17
don't worry. it's in the libklibc package.
[http://packages.ubuntu.com/pt-br/intrepid/i386/libklibc/filelist]("http://packages.ubuntu.com/pt-br/intrepid/i386/libklibc/filelist")

---

### Post by neu2buntu on 2009-02-17
checked "klibc" properties in synaptic and it is one of the installed files .see screenshot so no need to worry...lol

---

### Post by sisco311 on 2009-02-17
to find which package a file belongs to:
```
sudo apt-file update
apt-file search /path/to/the/file
```

---

### Post by mistypotato on 2009-02-17
:p

whew...back in the days of Windoze, a file with a name like that was probably a death file

---

