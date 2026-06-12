---
title: "Package Installer Freezes, 8.1"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by remotecontrolled on 2009-01-11
I'm trying to use the Package Installer that's (I'm assuming) built into Intrepid Ibex, under the Applications menu > Add/Remove Programs.  I can view programs that are available, as well as those installed, but trying to install *anything* results in a freeze at either the "downloading package" or the "installing software" popup.  I can force quit, or I can kill the processes, but other than that its the only way for it to stop.  

I'm running Ubuntu on a Macbook revision 2,1.  I have updated everything to the latest versions, and still have problems... what am I doing wrong?  

Thanks in advance.

---

### Post by Shhnap on 2009-01-11
Have you tried to use a different pacakge manager to install stuff? It's worth a try...

---

### Post by Xiong Chiamiov on 2009-01-11
Try updating or installing something via the command-line interface to it, so we can see what's happening (or not):
```

sudo apt-get update && sudo apt-get safe-upgrade
sudo apt-get install [package name]

```

---

