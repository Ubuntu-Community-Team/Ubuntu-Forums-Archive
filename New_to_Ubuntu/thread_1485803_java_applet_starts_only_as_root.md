---
title: "java applet starts only as root"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by jobrea on 2010-05-17
Due to known openjdk problems I installed the sun-java6-plugin in Ubuntu Lucid Lynx 10.04, after a complete deinstallation of openjdk and icedtea packages. Matlab and OpenOffice run, java -version produces the expected output and the about: plugins lists the sun java plugin.

However, any java applet only starts when I run the browser as root. The solution in [http://ubuntuforums.org/showthread.php?t=1475842](http://ubuntuforums.org/showthread.php?t=1475842) didn't work for me. Any suggestions?


$java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

about: plugins
Java(TM) Plug-in 1.6.0_20
File: libnpjp2.so
....

---

