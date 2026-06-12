---
title: "auto load slideshow from removeable"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-09-14
Hi,
I have a show that auto loads from a special folder that holds the required show file.
Is it possible to do the same thing using a USB memory  stick?
I have a stick which identifies as TOSHIBA on the Desktop when plugged in.
Is it possible to address the stick using commands (from Terminal or Startup )? 
I've tried a few things, but always seem to end up with "directory doesn't exist"!

kenmac2

---

### Post by nhasian on 2009-09-14
when your removable drive is plugged in, you should be able to see it in the /media folder.  you can access it from there.

```
ls /media
```

---

### Post by kenmac2 on 2009-09-14
Yes, I can see the TOSHIBA in the media folder.
However, the response I get when I went to the media folder ( cd /media) and did "cd /TOSHIBA" it says "No such file or directory" !

kenmac2

---

### Post by nhasian on 2009-09-14
> **kenmac2 said:**
>  did "cd /TOSHIBA" it says "No such file or directory"

yes, that makes sense.  it should be:

```
cd /media/TOSHIBA
```

assuming toshiba is in all caps that is.  you can also use [tab] to autocomplete the filename.

---

### Post by kenmac2 on 2009-09-14
OK, I can see where I went wrong with the CD actions.
I forgot to include the shortcut  period (.) when stepping down directory levels.
```
cd /media
cd ./TOSHIBA
```Anyway, that was a side issue.
I'm still looking at why I can't get the program to open at startup from the USB stick.

kenmac

---

### Post by kenmac2 on 2009-09-14
When I apply the same commands (in Terminal) as used in Startup, it responds with:
> javaldx: Could not find a Java Runtime Environment! 
Please ensure that the package openoffice.org-java-common is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xmland a screen message says "/media/TOSHIBA/..... does not exist"
I had a look in Synaptic and couldn't see "openoffice.org-java-common", but there is a "java-common".
Anyway, there is no problem when the file is accessed from an internal folder under the /home directory. 

Usually the " does not exist..." message occurs with a misspelling, incorrect case or  path statement, but I can't fault it.
I'm going to put this aside for a couple of days then come back for a fresh look at it.


kenmac2

---

