---
title: "HELP! Need an easy photo editor ASAP"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by kyootcarmy on 2010-12-13
Can someone please suggest a good and easy not to mention VERY user friendly photo editor for Ubuntu 10.10. I have Gimp, but its too fussy. (YES I'M A NOOB),

I want some similar to Picasa. The Picasa I've downloaded and installed doesn't seem to work. :( It installs and even appears under the Applications menu, logo and all, but when I click on it, nothing happens. So please help.

---

### Post by sandyd on 2010-12-13
> **kyootcarmy said:**
> Can someone please suggest a good and easy not to mention VERY user friendly photo editor for Ubuntu 10.10. I have Gimp, but its too fussy. (YES I'M A NOOB),

I want some similar to Picasa. The Picasa I've downloaded and installed doesn't seem to work. :( It installs and even appears under the Applications menu, logo and all, but when I click on it, nothing happens. So please help.
you mean you downloaded the deb from [http://picasa.google.com/linux/](http://picasa.google.com/linux/) ?

---

### Post by kyootcarmy on 2010-12-13
Yes I did all of that

---

### Post by the.phantom on 2010-12-13
i use   showfoto

easy to use and in the ubuntu software center

i found gimp a bit hard too

---

### Post by sandyd on 2010-12-13
go to Applications -> Accessories -> Terminal
type in 
```

picasa
```and hit enter.
post the output.

It should be working, because it even works in gentoo, after --force all.....

---

### Post by nerdy_kid on 2010-12-13
gwenview is a nice app, find it in the software center or type this in a terminal:
```

sudo apt-get install gwenview

```

---

### Post by kyootcarmy on 2010-12-13
> **sandyd said:**
> go to Applications -> Accessories -> Terminal
type in 
```

picasa
```and hit enter.
post the output.

It should be working, because it even works in gentoo, after --force all.....

I removed it last night, but I am downloading it as we speak. Will try starting it again.
Thanks in advance :)

---

### Post by kyootcarmy on 2010-12-13
Heres the output:

/usr/bin/picasa: line 139: 20060 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175: 20163 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

---

### Post by sandyd on 2010-12-13
> **kyootcarmy said:**
> Heres the output:

/usr/bin/picasa: line 139: 20060 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175: 20163 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
Use Picassa 3, even though it says beta.

Thats a bug in picassa 2 (its never been fixed..)

---

### Post by kyootcarmy on 2010-12-13
Clearly shows how noob I really am. LOL
Going to try it again then... :)

---

### Post by Bluebuddy on 2010-12-13
Try using Photoshop Express it's web browser-based photo editor. 
[http://www.photoshop.com/tools](http://www.photoshop.com/tools)

---

### Post by kyootcarmy on 2010-12-13
> **sandyd said:**
> Use Picassa 3, even though it says beta.

Thats a bug in picassa 2 (its never been fixed..)


:biggrin: Thanks so much! It worked. I'm editing yipeeeee!


[Mods please lock]

---

