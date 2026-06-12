---
title: "Help needed understanding java packages"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by searchfgold6789 on 2010-10-30
Hi, I'm a little bit confused about the way java packages work. I have the following java-related packages installed on my PC.
icedtea-6-jre-plugin
icedtea-6-cacao
openjdk-6-jre
openjdk-6-headless
openjdk-6-jre-lib
Which ones do I need? IcedTea says it is a replacement or openJDK, so could I just uninstall the heavy openjdk? I always run Java GUI's like jEdit.
Thanks,
 - search

---

### Post by gandaran on 2010-10-30
you need all of then if you want to keep the icedtea plugin for web browsers, (the plugin depends on openjdk-java packages) what I would recommend is get rid of all openjdk-java or just the icedtea plugin if you have any application that depends on openjdk and install sun-java instead!
to get sun-java you have to enable the archive.canonical partner repository in software sources and update the software package list next, then you can find sun-java in ubuntu software center or synaptic and install the the sun-java6-plugin.

---

