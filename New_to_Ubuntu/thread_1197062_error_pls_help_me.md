---
title: "error pls help me"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by nnamdi on 2009-06-25
i have this error pls how do i resolve it

```


pradeep@pradeep-laptop:~/Desktop/vidalia-0.1.13$ sudo apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libqt4-dev: Depends: libpng12-0-dev
E: Broken packages
pradeep@pradeep-laptop:~/Desktop/vidalia-0.1.13$ 


```

---

### Post by Revolutionary101 on 2009-06-25
Type this into terminal

```
sudo apt-get install libpng12-0-dev
```

Then do this

```
sudo apt-get install libqt4-dev
```

Hope it helps

---

### Post by nnamdi on 2009-06-26
hey thanks for the responds but still did not work!!!

---

### Post by michy99 on 2009-06-26
Try this:```
sudo apt-get install libpng12-dev libqt4-dev
```

---

### Post by nnamdi on 2009-06-26
still same errors i get i hope i have to broken my ubuntu!!!!

---

### Post by Bucky Ball on 2009-06-26
Could you try opening Synaptic Package Manager and fixing broken packages. There is a sort of info line along the bottom right of the Synaptic interface that tells you the state of your packages, including broken ones.

You could also attempt installing it in Synaptics and seeing what result you get after fixing any broken packages.

* ps: Could you please use more descriptive titles in future. More people will bother to look at your post that way. Include any helpful information you can think of.  ;)

---

