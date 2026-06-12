---
title: "FreeFontPath error when ssh forwarding X, entire desktop"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by gyzer on 2008-05-30
I am trying to ssh from my laptop into my desktop. I can ssh into the desktop just fine, but when I try to forward the entire X desktop after hitting CTRL+ALT+F1 OR F2 and input this command:
 
```
xinit -e ssh -XCT yourusername@your.host gnome-session -- :1
```
 
I get this error:
 
```
Waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/x11/misc"
refcount is 2, should be 1; fixing

```
 
Before I get the error the screen on the laptop flickers a few times.
 
The desktop is running Ubuntu 8.04 and the laptop is using Xubuntu 8.04 with IceWM, not XFCE. 
 
I have done allot of searching on this error and "FreeFontPath" and I really haven't been able to find anything that pertains to my problem.
 
I looked in the xorg.conf files of both computers and neither of them had any font references and I also looked for the "/usr/share/fonts/x11/misc" directory, and that directory doesn't exist on either computer.
 
So what is going on here? Am I missing some fonts or a directory or something?
I did also try this in XFCE and I got the same problem.
 
Also I did try running ssh with different combinations of the -X -C and -T options, and it still resulted in the same error message.
 
Any help would be greatly appreciated.

---

### Post by gyzer on 2008-06-02
anyone got any ideas?

---

