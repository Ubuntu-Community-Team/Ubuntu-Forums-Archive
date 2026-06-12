---
title: "does ubuntu open exe files?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by mrcactu5 on 2009-02-16
I went to download a program and it was only available as .exe  Does that mean it's exclusively for windows?

---

### Post by TJCIB on 2009-02-16
What program is it?

.exe is a Windows executable file.

Someone may be able to point you to the right place to download the proper file.

Or you could always try the program using WINE.

---

### Post by avtolle on 2009-02-16
> **mrcactu5 said:**
> I went to download a program and it was only available as .exe  Does that mean it's exclusively for windows?
Yes, although it may run in WINE; it will not, however, run natively in Linux. You might do a Google search on the name of the program and Wine, to see if there is anything out there concerning running the program under Wine.

Alternatively, do a search to see if there is either a Linux version of the program, or an analogous program in Linux.

---

### Post by mrcactu5 on 2009-02-16
I have Wubi, so I will just use Windows XP for this one.  thanks

---

### Post by Bölvaður on 2009-02-16
To make it simple: **you are unable to open .exe files**. Just like you are unable to open them on a mac or bds.. or solaris...


To make it complicated: yes you are. But depending on how and how well the program was made you may not be able to run it.

To find out if you will be able to run it through WINE go to [http://www.winehq.org/]("http://www.winehq.org/") and use the search to see how other's are doing getting that program to work.

To install it go to Applications &#8594; Add/Remove and look for WINE. Then tick the box next to it and apply.

Now all you have to do is right click on the file and select "open with WINE"


but you can also get newer versions of wine and tweak things a lot. But I think starting from simple and then having you advancing towards doing and accomplishing what ever you want, step by step.

---

### Post by mrbiggbrain on 2009-02-16
linux doesnt attmept to guess if a file is exeuctible by its ending so a file can be an .exe, .png, or .jpg, or even .exe and be given executble rights. soy ou can compile a program and give it a .txt ending and run it as ./whatever.txt and it will run, unlike windows.

---

### Post by dragos240 on 2009-02-16
Yes, an exe is for windows, it might run in wine, unless it needs a .NET frameworks thing, because those don't work. Linux packages are:
deb, rpm, yum, and some are non-compiled in folders. Anyways, exe's are windows executables made for windows, also, you can get most linux packages from the synaptic package manager on root or an account that can use sudo.

---

