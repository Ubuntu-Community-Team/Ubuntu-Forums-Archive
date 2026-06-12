---
title: "android : error while make"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by ssprabu on 2011-05-19
]As i try to build android file system while making java it shows the error,

 *** [out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes.dex] Error 1

---

### Post by ssprabu on 2011-05-19
how to resolve this ..........
when i try to make java1.5 in ubundu................
UNEXPECTED TOP-LEVEL EXCEPTION:
java.util.zip.ZipException: error in opening zip file
    at java.util.zip.ZipFile.open(Native Method)
    at java.util.zip.ZipFile.<init>(ZipFile.java:203)
    at java.util.zip.ZipFile.<init>(ZipFile.java:234)
    at com.android.dx.cf.direct.ClassPathOpener.processArchive(ClassPathOpener.java:205)
    at com.android.dx.cf.direct.ClassPathOpener.processOne(ClassPathOpener.java:130)
    at com.android.dx.cf.direct.ClassPathOpener.process(ClassPathOpener.java:108)
    at com.android.dx.command.dexer.Main.processOne(Main.java:247)
    at com.android.dx.command.dexer.Main.processAllFiles(Main.java:183)
    at com.android.dx.command.dexer.Main.run(Main.java:139)
    at com.android.dx.command.dexer.Main.main(Main.java:120)
    at com.android.dx.command.Main.main(Main.java:89)
1 error; aborting
make: *** [out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes.dex] Error 1

---

### Post by freak42 on 2011-05-19
by asking in the right group:

for instance try here: 
[http://groups.google.com/group/android-developers/browse_thread/thread/6960bfd92a5952db?pli=1](http://groups.google.com/group/android-developers/browse_thread/thread/6960bfd92a5952db?pli=1)

---

### Post by howefield on 2011-05-19
Threads merged.

---

