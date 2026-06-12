---
title: "Problem reinstalling Zsnes after upgrade to Jaunty"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by floatingpoint on 2009-04-29
I had problems with Zsnes crashing after upgrading to 9.04, so I uninstalled it in teminal

```
 $ sudo apt-get remove zsnes 
```

Then I restarted. 

I went to terminal, and...  

```
kevin@kevin-desktop:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate
kevin@kevin-desktop:~$ 

```

Went to Add/Remove, it won't let me check it to install.
Went to Synaptic, and when I mark it for installation I get
> zsnes:

Package zsnes has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


I went to software sources and checked some stuff in Third Party, then tried again, but I'm just getting the same problems.

Any help appreciated!

---

### Post by floatingpoint on 2009-04-29
no one has any ideas?

---

### Post by Redundant Username on 2009-04-29
I guess they haven't made a version for Jaunty yet. I don't even see it in my package manager.
Maybe try running the windows version in W.I.N.E. ?

---

### Post by mkoehler on 2009-04-29
It appears as though there is only a zsnes package available for i386 computers at this time - [http://packages.ubuntu.com/jaunty/zsnes](http://packages.ubuntu.com/jaunty/zsnes).  If you have an i386 computer, you should check to make sure that you have the universe repository enabled, or you could download it directly from the link above.  Hope this helps :)

---

### Post by floatingpoint on 2009-04-30
That's weird, in Intrepid I got it with apt-get, and it's still in my repositories just now. It said it was gonna remove zsnes after the upgrade, and I asked it not to. Will the i386 version run on my amd64?

---

