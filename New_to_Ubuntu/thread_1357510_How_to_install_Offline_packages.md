---
title: "How to install Offline packages"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by harish4linux on 2009-12-17
I have collected all the packages from my friend through AptonCD

i have reloaded the packages to var/cache/apt/archives but i am able to install only some of the packages by double clicking the dependencies are missing i hope so

please help how to install the packages from the terminal completely along with the dependencies

please help thanks in advance...

---

### Post by northern lights on 2009-12-17
You'd have to have the .debs for the dependencies also.

No internet connection on that machine whatsoever?

---

### Post by harish4linux on 2009-12-17
> **northern lights said:**
> You'd have to have the .debs for the dependencies also.

No internet connection on that machine whatsoever?

Ya i do have all .debs for the dependencies also..
i dont have internet connection for the machine i want to install, please help me with the procedure how to install

---

### Post by northern lights on 2009-12-17
What exact error are you getting?

Can you try installing with *dpkg* directly so you might get better output?

```
sudo dpkg -i foo.deb
```

---

### Post by harish4linux on 2009-12-17
> **northern lights said:**
> What exact error are you getting?

Can you try installing with *dpkg* directly so you might get better output?

```
sudo dpkg -i foo.deb
```

This what the error i am getting when i use the command

> jack@jack-desktop:~$ sudo dpkg -i foo.deb
[sudo] password for jack: 
dpkg: error processing foo.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 foo.deb
jack@jack-desktop:~$

---

### Post by northern lights on 2009-12-17
I'm sorry, I suppose I should have given more in-depth explanations:

*foo* is a place holder name for the actual .deb package your trying to install. Also run it with the complete path to the file.

Maybe```
sudo dpkg -i /path/to/package.deb
```is more intuitive.

---

### Post by harish4linux on 2009-12-17
> **northern lights said:**
> I'm sorry, I suppose I should have given more in-depth explanations:

*foo* is a place holder name for the actual .deb package your trying to install. Also run it with the complete path to the file.

Maybe```
sudo dpkg -i /path/to/package.deb
```is more intuitive.

Ok ill try in my machine and let know...

hope so it will work...

---

### Post by LowSky on 2009-12-17
[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

---

