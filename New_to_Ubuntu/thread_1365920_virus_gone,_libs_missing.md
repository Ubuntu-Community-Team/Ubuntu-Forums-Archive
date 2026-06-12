---
title: "virus gone, libs missing"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Daniel1994 on 2009-12-27
Okay, so today all of a sudden my computer started automatically restarting, freezing, and other nasty things. I ran KlamAV and found out I had infected files, but it froze before I could remove them. So I booted from a Live CD, installed KlamAV and deleted all the broken files. 

I think I got rid of the virus, but now I am experiencing a lot of side-effects. Nautilus won't show my desktop icons, my clock dissapeared, KlamAV won't scan, the login screen is weird(allthough it still works), and probably a lot more I haven't discovered yet.

I think the programs is missing some shared libs or something, but I don't know how to reinstall them. 

Any ideas?

---

### Post by 3rdalbum on 2009-12-27
> **Daniel1994 said:**
> Okay, so today all of a sudden my computer started automatically restarting, freezing, and other nasty things. I ran KlamAV and found out I had infected files, but it froze before I could remove them. So I booted from a Live CD, installed KlamAV and deleted all the broken files. 

I think I got rid of the virus, but now I am experiencing a lot of side-effects. Nautilus won't show my desktop icons, my clock dissapeared, KlamAV won't scan, the login screen is weird(allthough it still works), and probably a lot more I haven't discovered yet.

I think the programs is missing some shared libs or something, but I don't know how to reinstall them. 

Any ideas?

I must admit I doubt that you had a virus. Probably more like a false alarm. As far as I know there are no Linux viruses at the moment, and viruses don't tend to cause crashes even on Windows.

Freezing, rebooting and odd behaviour usually points to hard disk or memory problems. When you start up, run the Memtest program from the GRUB menu. Run it overnight. If it shows errors, remove some of your RAM and try again. Isolate which RAM sticks are causing problems and get them replaced under warranty, or simply bin them.

Life's too short for bad memory.

---

### Post by sandyd on 2009-12-27
> **3rdalbum said:**
> <snip>

**Life's too short for bad memory.**
^    ^
nice one:lolflag:

---

### Post by Daniel1994 on 2009-12-27
Thanks for your reply. I'll do that :)

But right now my biggest problem is my missing libs.
I can't run OpenOffice, Firefox, Nautilus or even see what the time is before i fix it.

For example:

Output of KlamAV:
```
daniel@daniel-laptop:~$ klamav
klamav: error while loading shared libraries: libkio.so.4: cannot open shared object file: No such file or directory

```

Output of Nautilus:
```
daniel@daniel-laptop:~$ nautilus
nautilus: error while loading shared libraries: libexempi.so.3: cannot open shared object file: No such file or directory

```

Is there a command or something that can fix this?

---

### Post by jrusso2 on 2009-12-27
Did you and Klamav delete those?

---

### Post by Daniel1994 on 2009-12-27
yeah...

It seemed like a good idea then, but when I think about it, it seems like I overreacted a bit.

---

### Post by aljoriz on 2009-12-27
try to do a FRESH INSTALLATION.  

Always remember that klamav should be use to scan usb flash disk and not the ubuntu hdd.  I learned that the hard way, even if the virus enters the ubutnu system its useless but klam is helpful to shut your friends up accusing you being the source of the virus.

---

### Post by Daniel1994 on 2009-12-27
I hoped I would be able to fix it without reinstalling, but I guess it is the easiest way. Thanks for all your help, I'll reinstall tomorrow.:popcorn:

---

