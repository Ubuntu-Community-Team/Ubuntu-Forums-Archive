---
title: "How to open .jnlp files in 64-bit ubuntu?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by ItecKid on 2008-12-10
Hello,

I am running 64-bit Ubuntu 8.10.  Is there any way to open .jnlp files?  Presently, when I click on the file, nothing happens.

Thank you.

---

### Post by Dedoimedo on 2008-12-10
Try through Firefox.
Dedoimedo

---

### Post by ItecKid on 2008-12-10
Hello,

If I try to open the file in firefox, I get:

/home/obriem5/Desktop/rpischeduler.jnlp could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.

However, it is saved to my desktop already.  From that path, choosing to open with firefox redirects me to the website where I downloaded it, with the option to open or save to disk.

---

### Post by Michael.Godawski on 2008-12-10
I would right-click some JNLP file, select "Open With", and select open with sun java 6 web start.

---

### Post by ItecKid on 2008-12-10
If I try doing that, it does absolutely nothing...

---

### Post by Ddeath on 2010-02-13
Try install libnetx-java package... :-) Maybe it help you

---

### Post by ronmaroria on 2011-07-25
Had exactly the same problem. Be sure you have nothing but the latest sun java 6 web start. In firefox preferences, select to open .jnlp files using sun java 6 web start. If you have openjdk installed, completely remove that. anyway, that is worked for me, if somebody did something else, they can share.

---

### Post by kaldor on 2011-07-25
> **ronmaroria said:**
> Had exactly the same problem. Be sure you have nothing but the latest sun java 6 web start. In firefox preferences, select to open .jnlp files using sun java 6 web start. If you have openjdk installed, completely remove that. anyway, that is worked for me, if somebody did something else, they can share.

For future reference to anyone reading this:

OpenJDK is a future replacement for Java. Currently, Ubuntu and Mac OS X use this instead of the official Oracle Java. Some things do not work entirely yet and may cause problems, but it does get closer with every release. If this is the case for you, simply replace OpenJDK with Java.


On Ubuntu, you will likely want to use Oracle Java instead of OpenJDK. You can do this by enabling the Partner Repository in the Ubuntu Software Centre's Software Sources menu. Do a search for Java and install sun-java6-jre and all should be well.

Once you download and save a .jnlp file, right-click on it and select Preferences and then the Open With tab. Select Java instead of OpenJDK. All should be well.

***Note that you do not need to totally remove OpenJDK. You can have both installed at once with no problems. Some people report having better performance on Minecraft using OpenJDK instead of Java, for example. So if you don't mind taking up some extra space, there's no problem if you do not remove it.*

---

### Post by narr on 2012-09-21
Again for future reference:
If you want to try the open implementation, you can install the package icedtea-netx (I tried it on Ubutu 12.04 and 12.10). You can then try to open the jnlp file with the command `javaws`

---

