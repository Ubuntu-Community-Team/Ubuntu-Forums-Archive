---
title: "Java"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Tmoney1309 on 2009-01-25
I installed Java on my computer (Ubuntu 8.04) and im not sure if it is working or not. I tried to test it at java.com, but it isnt working. Does anybody know how to find out if it is working?

---

### Post by taurus on 2009-01-25
How did you install it?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by cardinals_fan on 2009-01-25
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by minsf on 2009-01-25
also interesting is the output of
```
sudo dpkg -l | grep java
```

---

### Post by Tmoney1309 on 2009-01-25
I typed what you said and this is what appeared-

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

---

### Post by igknighted on 2009-01-25
If you type "about:plugins" in firefox, does it list a java plugin?

---

### Post by Tmoney1309 on 2009-01-25
ii  java-common                                0.28ubuntu3                       Base of all Java packages
ii  libaccess-bridge-java                      1.22.0-0ubuntu5                   Java Access Bridge for GNOME
ii  sun-java6-bin                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jre                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar

---

### Post by igknighted on 2009-01-25
> **Tmoney1309 said:**
> ii  java-common                                0.28ubuntu3                       Base of all Java packages
ii  libaccess-bridge-java                      1.22.0-0ubuntu5                   Java Access Bridge for GNOME
ii  sun-java6-bin                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jre                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar

Ahh, forget my last post... type (in the terminal) 'sudo apt-get install sun-java6-plugin'

---

### Post by Tmoney1309 on 2009-01-25
no, there is no plug in for Java

---

### Post by Tmoney1309 on 2009-01-25
alright, I typed that in the terminal and now it says-

Setting up sun-java6-plugin (6-07-3ubuntu2) ...

---

### Post by Tmoney1309 on 2009-01-25
Its not doing anything though

---

### Post by igknighted on 2009-01-25
> **Tmoney1309 said:**
> Its not doing anything though

Did you restart firefox?

---

### Post by Tmoney1309 on 2009-01-25
My java still isnt working, do you know how to enable it? also do you know how to install and open frostwire?

---

### Post by igknighted on 2009-01-25
> **Tmoney1309 said:**
> My java still isnt working, do you know how to enable it? also do you know how to install and open frostwire?

Frostwire should work fine for you (you have have installed, you just don't have the firefox web plugin working).

Are you running 64bit?  There is no 64bit browser plugin, unless you use the pre-release version.

---

### Post by minsf on 2009-01-26
as the previous post suggests, there is no support for x64.
we can still guide you through installation of java5 in this case, or of the latest release of java6.
so please let us know if you are running 32 or 64 bit.
also please post the current output of
```
sudo dpkg -l | grep java
```
(we need to verify that the sun-java6-plugin package was installed successfully)

---

### Post by minsf on 2009-01-26
you seem to have another thread on the same issue:
[http://ubuntuforums.org/showthread.php?t=1050606](http://ubuntuforums.org/showthread.php?t=1050606)
please keep track of you threads, rather than starting new threads
cheers :)

---

