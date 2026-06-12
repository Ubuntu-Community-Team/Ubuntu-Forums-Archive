---
title: "How do I know if opengl is installed on my ubuntu"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by anayisse on 2009-02-21
Dear helpers

If I can visualize videos properly, doest it mean that I have OPENGL installed in my linux, I'm using ubuntu 8.04 LTS ?

If not ! how can I know, because I need to have OPENGL installed on my computer before installing some softwares. 

what are the libraries I need to have OPENGL installed

Thank you very much

---

### Post by sandyd on 2009-02-21
```

glxinfo

```

does that help?

---

### Post by anayisse on 2009-02-21
Hi carlee,

Thank you very much, I used glxinfo and it seems that OPENGL is already installed but why I got those errors when I'm trying to install some software :

/usr/bin/ld: cannot find -lXmu
.........
include/G4OpenGLXViewer.hh:43:29: error: X11/Xmu/StdCmap.h: No such file or directory
Making dependency for file src/G4OpenGLStoredXmViewer.cc ...
........
g++ -shared -Wl,-soname,libGX11.so -m32 -O2 -o lib/libGX11.so x11/src/GX11Gui.o x11/src/Rotated.o x11/src/TGX11.o x11/src/gifdecode.o x11/src/gifencode.o x11/src/gifquantize.o x11/src/G__X11.o -lXpm -lXext -lX11 -lXft
/usr/bin/ld: cannot find -lXft
collect2: ld returned 1 exit status
make: *** [lib/libGX11.so] Error 1
.....

perhaphs some libraries are missing, what do you think please ?

Thanks again

---

### Post by Mitch9654 on 2009-02-21
try going to synaptic (system/administration/synaptic package manager, click on the search tab and type in openGL

Hope it works!


mitch9654

---

### Post by Mercury_Alpha on 2009-02-21
Are you trying to build something from source code? If so, it looks like you need to do a

```

sudo apt-get build-dep <package name>

```

...which will give you a list of all the libraries you need to build that package.

Otherwise, I'd strongly recommend searching in Synaptic for your package, instead of trying to build it. Building makes it more difficult to remove the app.

---

### Post by 3rdalbum on 2009-02-21
If you are compiling software from source, you need development libraries too. The Linux implementation of OpenGL is called Mesa, so you need the packages whose names contain the word "mesa" and have "-dev" at the end of them.

You seem to be new to Linux, so maybe you should stick to the Synaptic Package Manager for the time being rather than compile software?

---

### Post by anayisse on 2009-02-21
Thanks every one for your help! I have a question please 

I checked and found lot of librairies, I would like to install just the good ones,
according to the error message above it seems like libXmu is missing ... i found in Synaptic libXmu et libXmu-dev

what is the difference between lib...   and lib..-dev  for example libXmu et libXmu-dev ? which one should I install ?

---

### Post by anayisse on 2009-02-21
thank you 3rdalbum

so I understand that I have to install all the packages whose names contain the word "mesa" and have "-dev" at the end of them.  and please what about packages whose names contain the word "mesa" only ?

---

### Post by jacksaff on 2009-02-21
Generally you won't choose to install libraries. You install the software you want and the underlying system works out what libraries you need and gets them for you. 

If you are trying to compile software then you will need the -dev .debs of whatever software you need. These contain files that are needed to compile software but which aren't necessary just to run it. Including them in the main package would make it unnecessarily large.

Find out what dependencies your to-be-compiled app needs and pick those development packages in synaptic.

---

### Post by anayisse on 2009-02-21
for example according to this error message what libraries should I install please :

/usr/bin/ld: cannot find -lXmu
.........
include/G4OpenGLXViewer.hh:43:29: error: X11/Xmu/StdCmap.h: No such file or directory
Making dependency for file src/G4OpenGLStoredXmViewer.cc ...
........
g++ -shared -Wl,-soname,libGX11.so -m32 -O2 -o lib/libGX11.so x11/src/GX11Gui.o x11/src/Rotated.o x11/src/TGX11.o x11/src/gifdecode.o x11/src/gifencode.o x11/src/gifquantize.o x11/src/G__X11.o -lXpm -lXext -lX11 -lXft
/usr/bin/ld: cannot find -lXft
collect2: ld returned 1 exit status
make: *** [lib/libGX11.so] Error 1
.....

---

### Post by Mercury_Alpha on 2009-02-21
> **anayisse said:**
> for example according to this error message what libraries should I install please :

/usr/bin/ld: cannot find -lXmu
.........
include/G4OpenGLXViewer.hh:43:29: error: X11/Xmu/StdCmap.h: No such file or directory
Making dependency for file src/G4OpenGLStoredXmViewer.cc ...
........
g++ -shared -Wl,-soname,libGX11.so -m32 -O2 -o lib/libGX11.so x11/src/GX11Gui.o x11/src/Rotated.o x11/src/TGX11.o x11/src/gifdecode.o x11/src/gifencode.o x11/src/gifquantize.o x11/src/G__X11.o -lXpm -lXext -lX11 -lXft
/usr/bin/ld: cannot find -lXft
collect2: ld returned 1 exit status
make: *** [lib/libGX11.so] Error 1
.....

Did you try that terminal command I gave?

---

### Post by teosbpl on 2012-04-04
Installing  xorg-dev fixes this problem. Just in case if anybody were still interested.

---

