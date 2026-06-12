---
title: "Programs not launching in Wine"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Unforgiver on 2011-02-08
I already posted this over at the Wine forums, but I'm hoping that maybe someone here might be able to help....

Hello all, 
 
First and foremost I'm fairly new to Linux (ubuntu 10.10 to be specific)  and I'm having issues getting the application functional in Wine.  I've  tried going through the documentation, copying the DLL files to the  system32 folder, tried different OS emulation and it still does the  exact same thing.  I launch the program, sits on a window that says  "opening prepware.exe", and then closes.  No error message or anything  helpful. 
 
I can't find anything in the AppDB on this program and I'm not sure what else I can try.  Can anyone help? 
 
Thanks in advance  [IMG]http://forum.winehq.org/images/smiles/icon_biggrin.gif[/IMG]

---

### Post by PunkLV on 2011-02-08
Name of the program you tried to launch would help. 

In case you can't provide it: at least tell about what does it do, bcause I'm pretty sure there is an analog for Linux.

And for debugging (sort of) try launching it from terminal, you will see exactly where wine crashes and what it lacks for your program to run:
```
wine /path/to/.exe
```

---

