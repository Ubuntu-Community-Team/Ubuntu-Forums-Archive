---
title: "Where is Sun JDK ?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by perito on 2010-04-30
Just updated to the 10.04 Ubuntu, everything seems cool.
But as I am trying to install sun-jdk6 as usual i can't find it. I did sudo apt-cache search jdk and its no where to be found ... there is a new 'default' jdk .. is that it?

Also when I browse youtube videos it tell me I need to install plug-ins but when I search it says 'no plug-ins found'

I'm using the main server in synaptic manager...

any help?

---

### Post by philinux on 2010-04-30
Sun java has been deprecated. Openjdk is now the default, i.e installing ubuntu-restricted-extras with recommends will install the icedtea plugin. Openjdk has been certified by Java SE Test Compatibility Kit (TCK) and is compatible with the Java(TM) SE 6 platform on the amd64 (x86_64) and i386 (ix86) architectures. However sun-java should be in the partner repo.

Activate partner in software sources.

---

### Post by perito on 2010-04-30
> **philinux said:**
> Sun java has been deprecated. Openjdk is now the default, i.e installing ubuntu-restricted-extras with recommends will install the icedtea plugin. Openjdk has been certified by Java SE Test Compatibility Kit (TCK) and is compatible with the Java(TM) SE 6 platform on the amd64 (x86_64) and i386 (ix86) architectures. However sun-java should be in the partner repo.

Activate partner in software sources.

thanks a lot, found it.
Programs like Frost wire and Eclipse do not work with Openjdk (or at least didn't use to work several months ago).

---

