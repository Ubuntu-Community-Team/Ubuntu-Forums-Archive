---
title: "Java not working..."
date: 2010-04-17
forum: New to Ubuntu
---

### Post by camn on 2010-04-17
Anything I can do to make it work? Hopefully my last noobish question >_<

---

### Post by unixisfreedom on 2010-04-19
I have Ubuntu 9.1 (Karmic) and as far as I know a JVM (necessary to run Java apps) doesn't come with Karmic.  I had to install myself...  There was two Debian packages (.DEBs) I had to install before Java worked for me.  Unforunately they depend on each other so installing them was tricky for me (though could be easier for you because you can use the 'apt' tool and I couldn't-- long story)...  But the upshot is you don't "instantly get" Java with Ubuntu and must install.  If you have problems installing, I or someone else on here will probably know what you need to and hopefully share :-)

---

### Post by EddieInGeeksClothing on 2010-04-19
> **camn said:**
> Anything I can do to make it work? Hopefully my last noobish question >_<

What exactly is not working? If you open a terminal and type 

> java -version

It will tell you if there is a default JVM installed, and what version it is.

There a quite a few different JVMs that you can install on Linux. If you don't need a pure Sun Java JVM then there others that you can install through the Software repositories.

I also believe that OpenJDK is installed by default on Ubuntu.

I will check when I get home in a couple of hours, and if it's not I'll give you a list of opens you can installed through the Synaptic Package Manager

---

