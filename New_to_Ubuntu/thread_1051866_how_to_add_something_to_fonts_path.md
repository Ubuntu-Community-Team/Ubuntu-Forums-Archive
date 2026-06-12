---
title: "how to add something to fonts path"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by abraxas334 on 2009-01-27
how do i add something to my font path?
I am trying to run mathematica remotely, but my fonts aren't displayed properly, so I have been trying to follow what this website has suggested.
[http://reference.wolfram.com/mathematica/tutorial/FontsOnUnixAndLinux.html]("http://reference.wolfram.com/mathematica/tutorial/FontsOnUnixAndLinux.html")
I have copied the fonts directory to my local machine. However when i use the following command:
```



xset fp+ /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Fonts/Type1; xset fp rehash


```
i get the following message:
```

xset:  bad font path element (#422), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax

```
the directory exists and i have read and write permission.
Any thoughts? Help will be greatly appreciated.

---

### Post by albinootje on 2009-01-27
> **abraxas334 said:**
> how do i add something to my font path?


It should be as easy as putting the fonts in the ~/.fonts/ directory, and then logging out of the desktop, and log in again.

---

