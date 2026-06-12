---
title: "[SOLVED] Setting up Awesome3.0"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Maverick1712 on 2008-12-14
Hi All,

I am trying to setup Awesome3.0 using this guide :

[http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-git-Ubuntu-Intrepid](http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-git-Ubuntu-Intrepid)

the problem I am experiencing is with step 6. I create the .xinitrc with the suggested contents and run the link command to .Xsession. problem is, I didn't have a .Xsession file, so I created one. Sice the link was there, I figured it would just read from the .xinitrc file. The problem is when i just to "run Xclient script", I get an error almost immediately saying that my session lasted less than 10 seconds. Any help would be appreciated regaring this issue.

Cheers,
Adam

---

### Post by dantrevino on 2008-12-14
Delete the .Xsession file and create the link as in the instructions.  The command basically tells anyone looking for .Xsession to go to .xinitrc.  No need to 'create' the .Xsession.

---

### Post by Maverick1712 on 2008-12-14
Hi

Stumbled across a new problem. Just trying to start the awesome from the terminal generates this:

```
adam@thor:~$ awesome
awesome: error while loading shared libraries: libxcb-keysyms.so.0: cannot open shared object file: No such file or directory
```

I can't seem to figure out where this package should have come from and can't seem to find anything about this on the forums. Any help is appreciated.

Cheers,
Adam

---

### Post by Maverick1712 on 2008-12-14
Consider this solved. Found the package and Awesome now runs fine.

Thanks
Adam

---

### Post by Unr3a1r00t on 2009-01-28
I am getting this same error... where did you find the package?

---

