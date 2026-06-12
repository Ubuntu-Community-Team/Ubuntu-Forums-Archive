---
title: "Java linked with mozilla, still not working"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Mahngiel on 2010-01-05
Using a base Karmic with Studio's rt kernel.
1)Downloaded and installed jre-6u17
```

king@mahngiel:/usr/share/java$ ls jre*
[COLOR=Lime]jre-6u17-linux-i586.bin[/COLOR]
jre1.6.0_17:
bin        javaws  LICENSE  plugin  THIRDPARTYLICENSEREADME.txt
COPYRIGHT  lib     man      README  Welcome.html

```2)Java version check
```

java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)

```3)Created symbolic link
```
king@mahngiel:/usr/lib/mozilla/plugins$ ls -l
total 360
lrwxrwxrwx 1 root root     37 2010-01-01 14:06 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
[COLOR=DeepSkyBlue]lrwxrwxrwx 1 root root     71 2010-01-05 11:16 libjavaplugin_oji.so -> /usr/share/java/jre1.6.0_u17/plugin/i386/ns7-gcc29/libjavaplugin_oji.so[/COLOR]
-rw-r--r-- 1 root root   5456 2009-11-03 05:38 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root  96200 2009-11-11 04:09 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 104768 2009-11-11 04:09 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  71612 2009-11-11 04:09 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  75904 2009-11-11 04:09 libtotem-narrowspace-plugin.so

```4) Ensured Java was enabled, and restarted Mozilla.  Still no dice, and no appearance in plug-ins.  See attached.

--Thanks.

---

### Post by Mahngiel on 2010-01-05
solved: i guess it doesn't have to be so difficult as the directions given by sun.java.com. just go to the repository and search 'java-sun6-plugin'

---

