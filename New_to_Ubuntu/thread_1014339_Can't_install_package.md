---
title: "Can't install package"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by dtommy79 on 2008-12-17
Hi,

When I try to download and install a package using the synaptic p.m. I get this error:

```
W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/t/ttf-wqy-zenhei/ttf-wqy-zenhei_0.6.26-2ubuntu1_all.deb
  Could not connect to hu.archive.ubuntu.com:80 (195.228.240.55), connection timed out


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/universe/c/cacao-oj6/cacao-oj6-jre-lib_6b12-0ubuntu5_i386.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b12-0ubuntu6_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2008h-2ubuntu1_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/r/rhino/rhino_1.7R1-1ubuntu3_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b12-0ubuntu6_i386.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/j/java-access-bridge/libaccess-bridge-java_1.24.0-0ubuntu2_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu3_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b12-0ubuntu6_i386.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20080712ubuntu3_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/universe/c/cacao-oj6/cacao-oj6-jre-headless_6b12-0ubuntu5_i386.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/universe/c/cacao-oj6/cacao-oj6-jre_6b12-0ubuntu5_i386.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/universe/b/bluefish/bluefish_1.0.7-5_i386.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/universe/j/jedit/jedit_4.3~pre13.dfsg-0ubuntu3_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/t/ttf-indic-fonts/ttf-bengali-fonts_0.5.4ubuntu2_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/t/ttf-indic-fonts/ttf-kannada-fonts_0.5.4ubuntu2_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/t/ttf-indic-fonts/ttf-oriya-fonts_0.5.4ubuntu2_all.deb
  Unable to connect to hu.archive.ubuntu.com http:


W: Failed to fetch http://hu.archive.ubuntu.com/ubuntu/pool/main/t/ttf-indic-fonts/ttf-telugu-fonts_0.5.4ubuntu2_all.deb
  Unable to connect to hu.archive.ubuntu.com http:

```

---

### Post by halitech on 2008-12-17
2 questions, what version of Ubuntu and are you online with this system? (dumb question but had to ask)

edit: actually it looks like that server is down at the moment so maybe try another mirror and it should work.

---

### Post by donkyhotay on 2008-12-17
Might need to change what repository server you connect to but more information will help give us accurate information.

---

### Post by zvacet on 2008-12-18
Probably server is down.Switch to main server in **system<admin>software sources.**

---

