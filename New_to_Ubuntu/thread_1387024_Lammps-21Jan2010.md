---
title: "Lammps-21Jan2010"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by dcasimir on 2010-01-21
I was previously using the lammps-8Dec09 version, then just recently downloaded the latest 21Jan2010 version.

I'm completely new to linux/ubuntu, and after some help from this thread 

[http://ubuntuforums.org/showthread.php?t=1038282&page=2](http://ubuntuforums.org/showthread.php?t=1038282&page=2)

I was able to get the 8Dec09 version up and running. However before I could start getting used to and learning lammps this newer version came out and again I am completely lost as to how to build this later version.

I would like to just get this latest version going since there are many bug fixes in it.

Can anyone help please?

v/r,

---

### Post by Yoshis88 on 2010-01-25
Try looking at my guide,

[http://ubuntuforums.org/showthread.php?t=1390490](http://ubuntuforums.org/showthread.php?t=1390490)

If you were able to get one build of LAMMPS under your belt, you probably have all the prerequisite packages installed and can start from step 3.

---

### Post by dcasimir on 2010-07-09
I followed your instructions for the 4Jul10 version of lammps, and dowloaded one the makefiles you provided, and it worked.

However I'm now having trouble with xmovie.
After going to the xmovie directory and typing "make" to make xmovie i get the following error.





administrator@ubuntu:~/lammps-4Jul10/tools/xmovie$ make
gcc -c -O2 -finline-functions -g -DMISSINGDEFS -D_POSIX_SOURCE -DUSEPRIVATE -DINCL_FLOAT -Wimplicit -Wunused -Wmissing-prototypes  xmovie.c
xmovie.c:12:28: error: X11/StringDefs.h: No such file or directory
xmovie.c:14:27: error: X11/Intrinsic.h: No such file or directory
xmovie.c:15:26: error: X11/Xaw/Form.h: No such file or directory
xmovie.c:16:31: error: X11/Xaw/Cardinals.h: No such file or directory
In file included from xmovie.c:18:
xmovie.h:65: error: expected specifier-qualifier-list before ‘Bool’
xmovie.h:98: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘TopLevel’
xmovie.h:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CreateScene’
xmovie.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CreateControl’
xmovie.h:105: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ReadProc’
xmovie.h:118: error: expected ‘)’ before ‘*’ token
xmovie.h:122: error: expected ‘)’ before ‘w’
xmovie.h:125: error: expected ‘)’ before ‘w’
xmovie.h:132: error: expected ‘)’ before ‘*’ token
xmovie.h:133: error: expected ‘)’ before ‘*’ token
xmovie.h:134: error: expected ‘)’ before ‘bg’
In file included from xmovie.c:19:
resource.h:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FallbackResources’
xmovie.c:34: warning: excess elements in struct initializer
xmovie.c:34: warning: (near initialization for ‘Common’)
xmovie.c:35: warning: excess elements in struct initializer
xmovie.c:35: warning: (near initialization for ‘Common’)
xmovie.c:36: error: ‘FALSE’ undeclared here (not in a function)
xmovie.c:36: warning: excess elements in struct initializer
xmovie.c:36: warning: (near initialization for ‘Common’)
xmovie.c:37: warning: excess elements in struct initializer
xmovie.c:37: warning: (near initialization for ‘Common’)
xmovie.c:38: warning: excess elements in struct initializer
xmovie.c:38: warning: (near initialization for ‘Common’)
xmovie.c:39: warning: excess elements in struct initializer
xmovie.c:39: warning: (near initialization for ‘Common’)
xmovie.c:40: warning: excess elements in struct initializer
xmovie.c:40: warning: (near initialization for ‘Common’)
xmovie.c:41: warning: excess elements in struct initializer
xmovie.c:41: warning: (near initialization for ‘Common’)
xmovie.c:42: warning: excess elements in struct initializer
xmovie.c:42: warning: (near initialization for ‘Common’)
xmovie.c:43: warning: excess elements in struct initializer
xmovie.c:43: warning: (near initialization for ‘Common’)
xmovie.c:44: warning: excess elements in struct initializer
xmovie.c:44: warning: (near initialization for ‘Common’)
xmovie.c:45: warning: excess elements in struct initializer
xmovie.c:45: warning: (near initialization for ‘Common’)
xmovie.c:46: warning: excess elements in struct initializer
xmovie.c:46: warning: (near initialization for ‘Common’)
xmovie.c:47: warning: excess elements in struct initializer
xmovie.c:47: warning: (near initialization for ‘Common’)
xmovie.c:48: warning: excess elements in struct initializer
xmovie.c:48: warning: (near initialization for ‘Common’)
xmovie.c:49: warning: excess elements in struct initializer
xmovie.c:49: warning: (near initialization for ‘Common’)
xmovie.c:50: warning: excess elements in struct initializer
xmovie.c:50: warning: (near initialization for ‘Common’)
xmovie.c:51: warning: excess elements in struct initializer
xmovie.c:51: warning: (near initialization for ‘Common’)
xmovie.c:52: warning: excess elements in struct initializer
xmovie.c:52: warning: (near initialization for ‘Common’)
xmovie.c:53: warning: excess elements in struct initializer
xmovie.c:53: warning: (near initialization for ‘Common’)
xmovie.c:54: warning: excess elements in struct initializer
xmovie.c:54: warning: (near initialization for ‘Common’)
xmovie.c:55: warning: excess elements in struct initializer
xmovie.c:55: warning: (near initialization for ‘Common’)
xmovie.c:56: error: extra brace group at end of initializer
xmovie.c:56: error: (near initialization for ‘Common’)
xmovie.c:56: error: extra brace group at end of initializer
xmovie.c:56: error: (near initialization for ‘Common’)
xmovie.c:56: error: extra brace group at end of initializer
xmovie.c:56: error: (near initialization for ‘Common’)
xmovie.c:56: error: extra brace group at end of initializer
xmovie.c:56: error: (near initialization for ‘Common’)
xmovie.c:56: warning: excess elements in struct initializer
xmovie.c:56: warning: (near initialization for ‘Common’)
xmovie.c:57: warning: excess elements in struct initializer
xmovie.c:57: warning: (near initialization for ‘Common’)
xmovie.c:58: warning: excess elements in struct initializer
xmovie.c:58: warning: (near initialization for ‘Common’)
xmovie.c:59: warning: excess elements in struct initializer
xmovie.c:59: warning: (near initialization for ‘Common’)
xmovie.c:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘TopLevel’
xmovie.c:69: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘options’
xmovie.c:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘resources’
xmovie.c:138: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘actions’
xmovie.c: In function ‘main’:
xmovie.c:145: error: ‘XtAppContext’ undeclared (first use in this function)
xmovie.c:145: error: (Each undeclared identifier is reported only once
xmovie.c:145: error: for each function it appears in.)
xmovie.c:145: error: expected ‘;’ before ‘AppContext’
xmovie.c:151: error: ‘TopLevel’ undeclared (first use in this function)
xmovie.c:151: warning: implicit declaration of function ‘XtAppInitialize’
xmovie.c:151: error: ‘AppContext’ undeclared (first use in this function)
xmovie.c:151: error: ‘options’ undeclared (first use in this function)
xmovie.c:152: warning: implicit declaration of function ‘XtNumber’
xmovie.c:153: error: ‘FallbackResources’ undeclared (first use in this function)
xmovie.c:153: error: ‘ZERO’ undeclared (first use in this function)
xmovie.c:155: warning: implicit declaration of function ‘XtVaGetApplicationResources’
xmovie.c:155: error: ‘XtPointer’ undeclared (first use in this function)
xmovie.c:156: error: ‘resources’ undeclared (first use in this function)
xmovie.c:160: warning: implicit declaration of function ‘XtAppAddActions’
xmovie.c:160: error: ‘actions’ undeclared (first use in this function)
xmovie.c:168: warning: implicit declaration of function ‘CreateScene’
xmovie.c:172: warning: implicit declaration of function ‘CreateControl’
xmovie.c:174: warning: implicit declaration of function ‘XtRealizeWidget’
xmovie.c:178: warning: implicit declaration of function ‘XtAppAddWorkProc’
xmovie.c:178: error: ‘ReadProc’ undeclared (first use in this function)
xmovie.c:181: error: ‘CommonData’ has no member named ‘init’
xmovie.c:185: warning: implicit declaration of function ‘XtAppMainLoop’
xmovie.c: In function ‘CheckResources’:
xmovie.c:261: error: ‘CommonData’ has no member named ‘version’
xmovie.c:263: error: ‘CommonData’ has no member named ‘natomcolors’
xmovie.c:263: error: ‘CommonData’ has no member named ‘natomcolors’
xmovie.c:264: error: ‘CommonData’ has no member named ‘natomcolors’
xmovie.c:266: error: ‘CommonData’ has no member named ‘nbondcolors’
xmovie.c:266: error: ‘CommonData’ has no member named ‘nbondcolors’
xmovie.c:267: error: ‘CommonData’ has no member named ‘nbondcolors’
xmovie.c:269: error: ‘CommonData’ has no member named ‘opaque’
xmovie.c:269: error: ‘CommonData’ has no member named ‘hollow’
xmovie.c:269: error: ‘TRUE’ undeclared (first use in this function)
xmovie.c:271: error: ‘CommonData’ has no member named ‘atoms_visible’
xmovie.c:272: error: ‘Bool’ undeclared (first use in this function)
xmovie.c:272: error: expected expression before ‘)’ token
xmovie.c:274: error: ‘CommonData’ has no member named ‘diameter’
xmovie.c:275: error: ‘Dimension’ undeclared (first use in this function)
xmovie.c:275: error: expected expression before ‘)’ token
xmovie.c:277: error: ‘CommonData’ has no member named ‘bonds_visible’
xmovie.c:278: error: expected expression before ‘)’ token
make: *** [xmovie.o] Error 1

---

