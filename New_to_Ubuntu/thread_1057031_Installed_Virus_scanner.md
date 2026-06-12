---
title: "Installed Virus scanner"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by halovivek on 2009-02-01
HI 
i have installed virus scanner in ubuntu. while i try to check the update. it says it can be done only using root. 
i could not go further. could you please help me
thanks

---

### Post by cardinals_fan on 2009-02-01
Why did you install a virus scanner?

Anyway, you should run it with *sudo* in the terminal.  Example: open terminal (Accessories -> Terminal) and enter ```
sudo insertcommandhere
```

That will give the scanner root privileges.  Note that you should only do this with software you trust, since it could easily hose your machine.

EDIT: If it is a graphical app, use *gksudo* instead.

---

### Post by HermanAB on 2009-02-01
Hmm, updating it is pointless, since there aren't any Linux viruses to scan for...

Relax and enjoy your new Linux system!

Cheers,

Herman

---

### Post by perlluver on 2009-02-01
I would recommend reading this: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812), all about security on Linux and Ubuntu.

---

### Post by kansasnoob on 2009-02-02
I'd like to know what virus scan was installed.

There are legitimate virus scanners like clamav.

---

### Post by jrusso2 on 2009-02-02
> **halovivek said:**
> HI 
i have installed virus scanner in ubuntu. while i try to check the update. it says it can be done only using root. 
i could not go further. could you please help me
thanks

Make your user part of the antivirus group. Most of them make a group. Like avg makes one called AVG.

---

### Post by mhh91 on 2009-02-02
> **HermanAB said:**
> Hmm, updating it is pointless, since there aren't any Linux viruses to scan for...

Relax and enjoy your new Linux system!

Cheers,

Herman

it checks for windows viruses,btw :D

---

### Post by Neural oD on 2009-02-02
Probably the only reason to have a virus scanner on Ubuntu - is to make sure that files you pass on to Windoz do not carry something that could hurt their os!

---

### Post by halovivek on 2009-02-02
Hi
i have installed antivirus to check windows partition as well to the files. Nothing more. I know well about the security for ubuntu.

---

