---
title: "Uninstalling libtcl/libtk"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by kcmccorm on 2009-09-03
when I want to run the program ds9, I get this error:

ds9: error while loading shared libraries: libtcl8.5.so.0: cannot open shared object file: No such file or directory

I'm not sure this is the right thing to do, but I was going to uninstall my existing tcl/tk and install libtcl8.5.  However, I'm embarrassed to admit that I don't know how to uninstall it.  When I type:

sudo apt-get uninstall libtcl8.4.so

I get back:

E: Invalid operation uninstall


I read somewhere that the "uninstall" function only works if it is listed in the configuration file (or something like that....I don't really know what I'm talking about).  So how do I uninstall if it's not listed?

---

### Post by perce on 2009-09-03
The command to uninstall is:

```
sudo apt-get remove
```

and the command to know everything about apt-get is:

```
 man apt-get 
```

---

