---
title: "installing multiple eclipse on ubuntu"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by replikanxxl on 2010-03-01
is there a way to have both ganymede and galileo on the system at the same time ? cause some of plugins i use doesnt work on galileo , and some doesnt work on ganymede

thank you

---

### Post by derrick81787 on 2010-03-01
> **replikanxxl said:**
> is there a way to have both ganymede and galileo on the system at the same time ? cause some of plugins i use doesnt work on galileo , and some doesnt work on ganymede

thank you

Yeah.  If you're using Ubuntu 9.10, you can install Ganymede by running the command

```
sudo apt-get install eclipse
```

If you're using an earlier version of Ubuntu, that will install Galileo.  To get the second version, you just go to Eclipse's website and download the version for your OS and architecture.  They are pre-compiled, so you just have to unzip the zip file and then run the included binary.

After they are both installed, you can just run the one you want at any given time.  I actually downloaded Ganymede from Eclipse's website and ran it back when Ubuntu only had Galileo.  Everything worked fine.  You will have to create your own menu entry for it, though (if you want one), but that's not really a big deal.

- Derrick

---

