---
title: "piping a text file to apt"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by meer on 2010-02-25
I hope this hasn't been posted before. Here's what I'm trying to do:

I have a text file - myfile - with the results of an aptitude search.

```
p   libqcad0-dev                                                           - professional CAD system -- development headers and static libraries             
p   qcad                                                                   - professional CAD system                                                         
p   qcad-data                                                              - professional CAD system -- shared files                                         
p   qcad-doc                                                               - professional CAD system -- documentation   
```How do I pipe this to an apt command?  This is what I had in mind, but it obviously didn't work.

```
sudo apt-get install < myfile
```Thanks for any help in advance.

---

### Post by Tibuda on 2010-02-25
you should cut only the package names first. something like this:
```
cut -d' ' -f4 myfile | xargs sudo apt-get install
```
play with cut before

---

