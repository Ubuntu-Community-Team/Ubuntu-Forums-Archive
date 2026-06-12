---
title: "Getting Vuze to Work"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by herrnaphta on 2009-12-02
I'm running Eeebuntu and am trying to get  Vuze to work.  When I try to run it through the command line, I get exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

Is there a quick fix for this?

---

### Post by endBc on 2009-12-02
You are missing the Java Runtime Environment.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by herrnaphta on 2009-12-02
i already have the newest version of java: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqt4-opengl libxine1-x librdf0 kdebase-runtime-data-common
  libqt4-test kdebase-runtime libxine1-misc-plugins kdelibs5 libxcb-xv0 phonon
  amarok-common kdemultimedia-kio-plugins kde-icons-oxygen libxine1-bin
  libexiv2-5 libkcddb4 librasqal1 libloudmouth1-0 libsoprano4 redland-utils
  kdebase-runtime-bin-kde4 libqt4-webkit kdelibs5-data libxcb-shape0
  libqt4-svg libstreamanalyzer0 libphonon4 linux-netbook phonon-backend-xine
  kdelibs-bin khelpcenter4 libpq5 libstreams0 exiv2 libxcb-shm0 soprano-daemon
  kdebase-runtime-data libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

still getting the same message when i try to run vuze

---

### Post by endBc on 2009-12-02
```
java -version && sudo update-java-alternatives -l
```

Please show us the Terminal output.

---

### Post by herrnaphta on 2009-12-02
```
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)
[sudo] password for herrnaphta: 
java-6-sun 63 /usr/lib/jvm/java-6-sun

```

---

### Post by endBc on 2009-12-02
Haven't used Vuze for a while now but could it be so that it really wants to run only on OpenJDK ?

```
sudo apt-get install openjdk-6-jre
```

---

### Post by herrnaphta on 2009-12-02
working now, thanks!

---

