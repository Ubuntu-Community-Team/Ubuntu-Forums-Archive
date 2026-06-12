---
title: "Is there a way to remember what you have compiled using make?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-01-10
When installing using make I tend to forget what I have installed.

Is there a way I could get the pc to remember.

I don't have enough disk space to keep all the install files.

Is there a way I could get Synaptic to do that or even something else?

Thanks

---

### Post by unutbu on 2009-01-10
Perhaps use checkinstall:

```

sudo apt-get install checkinstall

```
Then, instead of using "make install" to install files,
you run this:
```

sudo checkinstall -D --fstrans=no make install
```
The -D flag tells checkinstall to create a .deb. You then install the .deb:
```

sudo dpkg -i packagename.deb
```
The nice thing about this is, the deb remembers what files were installed, and it gives you an easy way to uninstall it:
```

sudo dpkg -r packagename
```

---

### Post by pluckypigeon on 2009-01-10
> **unutbu said:**
> Perhaps use checkinstall:

```

sudo apt-get install checkinstall

```
Then, instead of using "make install" to install files,
you run this:
```

sudo checkinstall -D --fstrans=no make install
```
The -D flag tells checkinstall to create a .deb. You then install the .deb:
```

sudo dpkg -i packagename.deb
```
The nice thing about this is, the deb remembers what files were installed, and it gives you an easy way to uninstall it:
```

sudo dpkg -r packagename
```

Hey thanks for that.

I am an obessive when it comes to computer indexing and stuff.

---

