---
title: "make errors making me gaga"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by hugstari on 2009-07-19
Good day all

I am trying to compile Exult from the cvs and i keep getting errors during the make process. The latest ones look like this:

collect2: ld returned 1 exit status
make[2]: *** [exult] Error 1
make[2]: Leaving directory `/home/hugstari/Desktop/exult'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hugstari/Desktop/exult'
make: *** [all] Error 2

Well that's only part of the make output. I have no idea where i can find the entire log, its pretty long and the terminal doesn't display it all.
 These issues have been nagging me for a while and i would very much like to put them behind me. So if there is anybody out there willing to help a linux noob like myself i would be eternally great full.

Thanks in advanced :)

---

### Post by yeats on 2009-07-19
Did you do a ./configure step before this?  That output (wrap in CODE tags) would be more helpful probably.

---

### Post by hugstari on 2009-07-19
Yes i ran ./configure and before that i ran ./autogen.sh

I will try to do that code thing. This should be a little more of the make output

```
xdrag.o: In function `Get_window_coords':
/home/hugstari/Desktop/exult/xdrag.cc:51: undefined reference to `XQueryTree'
/home/hugstari/Desktop/exult/xdrag.cc:53: undefined reference to `XFree'
/home/hugstari/Desktop/exult/xdrag.cc:59: undefined reference to `XGetWindowAttributes'
xdrag.o: In function `Xdnd':
/home/hugstari/Desktop/exult/xdrag.cc:88: undefined reference to `XInternAtom'
/home/hugstari/Desktop/exult/xdrag.cc:89: undefined reference to `XInternAtom'
/home/hugstari/Desktop/exult/xdrag.cc:90: undefined reference to `XInternAtom'
/home/hugstari/Desktop/exult/xdrag.cc:91: undefined reference to `XInternAtom'
/home/hugstari/Desktop/exult/xdrag.cc:93: undefined reference to `XInternAtom'
xdrag.o:/home/hugstari/Desktop/exult/xdrag.cc:94: more undefined references to `XInternAtom' follow
xdrag.o: In function `Xdnd::select_msg(XSelectionEvent&)':
/home/hugstari/Desktop/exult/xdrag.cc:258: undefined reference to `XGetAtomName'
/home/hugstari/Desktop/exult/xdrag.cc:275: undefined reference to `XGetWindowProperty'
/home/hugstari/Desktop/exult/xdrag.cc:307: undefined reference to `XFree'
xdrag.o: In function `Xdnd::client_msg(XClientMessageEvent&)':
/home/hugstari/Desktop/exult/xdrag.cc:132: undefined reference to `XGetAtomName'
/home/hugstari/Desktop/exult/xdrag.cc:190: undefined reference to `XSendEvent'
/home/hugstari/Desktop/exult/xdrag.cc:154: undefined reference to `XGetWindowProperty'
/home/hugstari/Desktop/exult/xdrag.cc:200: undefined reference to `XConvertSelection'
xdrag.o: In function `Xdnd':
/home/hugstari/Desktop/exult/xdrag.cc:108: undefined reference to `XChangeProperty'
/home/hugstari/Desktop/exult/xdrag.cc:108: undefined reference to `XChangeProperty'
collect2: ld returned 1 exit status
make[2]: *** [exult] Error 1
make[2]: Leaving directory `/home/hugstari/Desktop/exult'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hugstari/Desktop/exult'
make: *** [all] Error 2

```

---

### Post by hugstari on 2009-07-19
Hello everyone

Does nobody have a idea what my problem might be. Maybe it isn't a problem at all?

Anyways any help would be great :)

---

### Post by yeats on 2009-07-20
> Hello everyone

Does nobody have a idea what my problem might be. Maybe it isn't a problem at all?

Anyways any help would be great 

There's not enough information to go on here.  It looks like the problem lies with ld:

```
collect2: ld returned 1 exit status
```

but that's not enough information to troubleshoot.  You can add debugging information to make by adding a -d flag to it:

```
make -d
```

Perhaps that will give you more clues to go on.

---

### Post by hugstari on 2009-07-21
make -d gave me this

```
collect2: ld returned 1 exit status
Reaping losing child 0x082b1bb8 PID 5108 
make[2]: *** [exult] Error 1
Removing child 0x082b1bb8 PID 5108 from chain.
make[2]: Leaving directory `/home/hugstari/Desktop/exult'
Reaping losing child 0x09414588 PID 4983 
make[1]: *** [all-recursive] Error 1
Removing child 0x09414588 PID 4983 from chain.
make[1]: Leaving directory `/home/hugstari/Desktop/exult'
Reaping losing child 0x0879dc50 PID 4982 
make: *** [all] Error 2
Removing child 0x0879dc50 PID 4982 from chain.

```

---

### Post by Mark Phelps on 2009-07-22
You're getting errors from the object loader because it can't resolve the code references to some XWindows routines.  This means, most probably, that you are missing one or more XWindows development libraries or runtime libraries.  

Don't know which ones, but you'll need to Google on the XWindows calls to find out which libraries are needed.

---

