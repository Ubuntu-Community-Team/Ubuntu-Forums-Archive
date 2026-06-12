---
title: "Can someone walk me through..."
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-10
[http://www.linuxquestions.org/questions/linux-newbie-8/imlib2-dependency-for-pypanel-759152/](http://www.linuxquestions.org/questions/linux-newbie-8/imlib2-dependency-for-pypanel-759152/)

This here (above)? I want to install Pypanel, but it keeps telling me that I need Imlib2.

I don't know where the files are, I don't know how to symlink, so I can't do either workaround until someone tells me what to do.

---

### Post by sliketymo on 2010-01-10
> **Psumi said:**
> [http://www.linuxquestions.org/questions/linux-newbie-8/imlib2-dependency-for-pypanel-759152/](http://www.linuxquestions.org/questions/linux-newbie-8/imlib2-dependency-for-pypanel-759152/)

This here (above)? I want to install Pypanel, but it keeps telling me that I need Imlib2.

I don't know where the files are, I don't know how to symlink, so I can't do either workaround until someone tells me what to do.

sudo apt-get install Imlib2

---

### Post by Psumi on 2010-01-10
> **sliketymo said:**
> sudo apt-get install Imlib2

No package by that name, I already tried that.

---

### Post by sandyd on 2010-01-10
> **Psumi said:**
> No package by that name, I already tried that.
libimlib2

---

### Post by Psumi on 2010-01-10
> **carlee said:**
> libimlib2

I already have that, but pypanel still says I need Imlib2.

As the thread I linked states, setup.py for PyPanel points to an invalid file/location, but, I do not know what to correct it to.

---

### Post by sandyd on 2010-01-10
/usr/lib/imlib2
assuming its looking for the libs folder.

---

### Post by Psumi on 2010-01-10
So what do I put in these spots?

```
# Full paths to imlib2-config and freetype-config, adjust as needed -
configs = ["/usr/bin/freetype-config", "/usr/bin/imlib2-config"]

# Adjust or add any additional include directories here -
idirs   = ["/usr/X11R6/include"]

# Add any additional library directories here -
ldirs   = []

# Add any additional compile options here -
cargs   = ["-Wall"]

# Full path to libImlib2 shared library
imlib2  = "/usr/lib/libimlib2.so.1"
```

Changing the last line to what you mentioned doesn't work at all.

---

### Post by sandyd on 2010-01-10
> **Psumi said:**
> So what do I put in these spots?

```
# Full paths to imlib2-config and freetype-config, adjust as needed -
configs = ["/usr/bin/freetype-config", "/usr/bin/imlib2-config"]

# Adjust or add any additional include directories here -
idirs   = ["/usr/X11R6/include"]

# Add any additional library directories here -
ldirs   = []

# Add any additional compile options here -
cargs   = ["-Wall"]

# Full path to libImlib2 shared library
imlib2  = "/usr/lib/libimlib2.so.1"
```Changing the last line to what you mentioned doesn't work at all.
ooh. just forgot
linux is case sensative. which is why i couldn't find the files that the package installed until i looked in synaptic
```

/usr/lib/libImlib2.so.1

```

---

### Post by Psumi on 2010-01-10
Still says I need the imlib2 library though, sadly. :( I give up, I'm going to try lxpanel -_-

---

