---
title: "Can't AssaultCube to work"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Cpt.Jack on 2009-02-16
Now I am a self confessed Ubuntu Noob just onto 8.10 after being on 8.04 for a short period but I tries "sudo apt-get install assaultcube" to get it it didn't work so I thought fair enough it's not in my repository so I downloaded it off the link on the site but now it is just a bundle of files and I have no idea how to make it work. I wouldn't mind that much but I see this problem arising in the future so it would be nice to sort out now.

---

### Post by jpeddicord on 2009-02-16
Whoops, somehow your thread got moved to the forum archives. I've moved it back to the active section of the forums; sorry for the inconvenience.

---

### Post by Ptero-4 on 2009-02-16
Does it contain files ending in .c, .cpp, .h and files called Makefile?
If it does then you got the game´s source code. To install it you would need to type first:
```

sudo aptitude install build-essential autoconf automake autogen gawk libtool intltool bison flex byacc

```
to get a development kit (you´ll need it). Then in the game´s directory type:
```

./configure --help | less

```
if it lists a screenful of options then you can either post them and someone here will likelly know which ones are recomended to set. Or just use this basic ones:
```

./configure --prefix=/usr --disable-debug

```
which are usually good enough, unless the program contains large amount of modules and options in which case leaving the defaults might give you a crippled installation.

---

### Post by thegreenblob on 2009-02-16
The package from assault cubes site is a tar.bz2 file, but once extracted there is a binary file. You can run it by double clicking on assaultcube.sh and then click run.

Or if you prefer you can install the deb package from here: [http://www.getdeb.net/app/AssaultCube](http://www.getdeb.net/app/AssaultCube)

---

