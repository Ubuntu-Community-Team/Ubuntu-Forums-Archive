---
title: "Update problem"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by ashley123 on 2011-02-27
I'm sorry if I'm violating the rules of the forum, I'm new here.
I upgraded Karmik Koala to Lucid Lynx. Now I need to install several softwares. seeing several threads here, i tried to update the os. but it fails everytime, saying 
failed to fetch package...
please somebody help me, it's urgent...

Thanks.

---

### Post by emoguitarist06 on 2011-02-27
> **ashley123 said:**
> I'm sorry if I'm violating the rules of the forum, I'm new here.
I upgraded Karmik Koala to Lucid Lynx. Now I need to install several softwares. seeing several threads here, i tried to update the os. but it fails everytime, saying 
failed to fetch package...
please somebody help me, it's urgent...

Thanks.

What software are you trying to install?
How are you trying to install? Via terminal using "sudo apt-get install [package-name]"??

Be a little more specific and post your error messages

---

### Post by Ben Page on 2011-02-27
Welcome to the forums!

When you say "upgraded", do you mean you deleted the old OS and installed the new one from scratch or that you have upgraded via the updater? Can you post full output of the error?

---

### Post by ashley123 on 2011-02-27
I upgraded OS by using update manager. It worked at that time. now i need to install openjdk and eclipse. Foloowing messages appear while installing openjdk:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java icedtea-6-jre-cacao java-common libaccess-bridge-java
  libaccess-bridge-java-jni libice-dev libpthread-stubs0 libpthread-stubs0-dev
  libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxt-dev
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra
  tzdata tzdata-java x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  xtrans-dev
Suggested packages:
  default-jre equivs openjdk-6-demo openjdk-6-source visualvm icedtea6-plugin
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts
The following NEW packages will be installed:
  ca-certificates-java icedtea-6-jre-cacao java-common libaccess-bridge-java
  libaccess-bridge-java-jni libice-dev libpthread-stubs0 libpthread-stubs0-dev
  libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxt-dev
  openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  ttf-dejavu-extra tzdata-java x11proto-core-dev x11proto-input-dev
  x11proto-kb-dev xtrans-dev
The following packages will be upgraded:
  tzdata
1 upgraded, 24 newly installed, 0 to remove and 17 not upgraded.
Need to get 8,893kB/54.1MB of archives.
After this operation, 144MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main x11proto-core-dev 7.0.16-1
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libice-dev 2:1.0.6-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libxau-dev 1:1.0.5-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libxdmcp-dev 1:1.0.3-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main x11proto-input-dev 2.0-2
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main x11proto-kb-dev 1.0.4-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main xtrans-dev 1.2.5-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libpthread-stubs0 0.3-2
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libpthread-stubs0-dev 0.3-2
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libxcb1-dev 1.5-2
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libx11-dev 2:1.3.2-1ubuntu3
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-proposed/main tzdata 2011b-0ubuntu0.10.04
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-proposed/main tzdata-java 2011b-0ubuntu0.10.04
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main ca-certificates-java 20100406ubuntu1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libaccess-bridge-java-jni 1.26.2-3
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libaccess-bridge-java 1.26.2-3
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libsm-dev 2:1.1.1-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libxt-dev 1:1.0.7-1
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main ttf-dejavu-extra 2.30-2
  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-core/x11proto-core-dev_7.0.16-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-core/x11proto-core-dev_7.0.16-1_all.deb)  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libi/libice/libice-dev_1.0.6-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libi/libice/libice-dev_1.0.6-1_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxau/libxau-dev_1.0.5-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxau/libxau-dev_1.0.5-1_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxdmcp/libxdmcp-dev_1.0.3-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxdmcp/libxdmcp-dev_1.0.3-1_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_2.0-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_2.0-2_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-kb/x11proto-kb-dev_1.0.4-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-kb/x11proto-kb-dev_1.0.4-1_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xtrans/xtrans-dev_1.2.5-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xtrans/xtrans-dev_1.2.5-1_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0_0.3-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0_0.3-2_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.3-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.3-2_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.5-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.5-2_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.3.2-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.3.2-1ubuntu3_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011b-0ubuntu0.10.04_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011b-0ubuntu0.10.04_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011b-0ubuntu0.10.04_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011b-0ubuntu0.10.04_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100406ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100406ubuntu1_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/java-access-bridge/libaccess-bridge-java-jni_1.26.2-3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/java-access-bridge/libaccess-bridge-java-jni_1.26.2-3_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/java-access-bridge/libaccess-bridge-java_1.26.2-3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/java-access-bridge/libaccess-bridge-java_1.26.2-3_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.1.1-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.1.1-1_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.7-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.7-1_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.30-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.30-2_all.deb)  Unable to connect to in.archive.ubuntu.com:http:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by emoguitarist06 on 2011-02-27
> **ashley123 said:**
> 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Did you try that?
You should try running
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist upgrade
sudo apt-get install -f
```

---

### Post by Ben Page on 2011-02-27
From this it looks like apt is working OK. The repository you are trying to reach is unavailable, I can't reach it either.
I see you are in "in." - India/Indonesia? Try to switch your repositories in synaptic to main Ubuntu server. Open Synaptic, in settings menu click Repositories and then change Download from: to Main Server. Update  apt and try again.

---

### Post by ashley123 on 2011-02-27
Yes, I tried apt-get update. It didn't work for many times. But, somehow, it did finally. And all of a sudden, installation of openjdk was successful... :)

Can you tell me why it failed earlier?

Thanks for the help... :)

---

### Post by Ben Page on 2011-02-27
> **ashley123 said:**
> 
Can you tell me why it failed earlier?


The repository is back online

---

### Post by ashley123 on 2011-02-27
> **Ben Page said:**
> The repository is back online

Ok, Sir. Thanks a lot...

---

