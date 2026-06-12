---
title: "Updating With Subversion (svn)"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by spikoley on 2010-06-25
I am new to Subversion and I cannot figure out how to update a package.  Does anybody have a general guide to update with Subversion?

---

### Post by nothingspecial on 2010-06-25
Change directory to the source code you downloaded with subversion 

```
cd *directory*
```

Then ```
svn up
```

From there it depends on the build instructions for the source you want to compile.

Usually
```

make clean
make
sudo make install
```

But not always. There should be instructions in the original source you downloaded or on the web page.

---

### Post by spikoley on 2010-06-25
Thanks, that helped out.

---

