---
title: "Android file system-error on make"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by ssprabu on 2011-05-19
hi,
   when i tried to 'make' the java 1.5 in android, i got this error..pleaze  solve it.. 



UNEXPECTED TOP-LEVEL EXCEPTION:
java.util.zip.ZipException: error in opening zip file
    at java.util.zip.ZipFile.open(Native Method)
    at java.util.zip.ZipFile.<init>(ZipFile.java:203)
    at java.util.zip.ZipFile.<init>(ZipFile.java:234)
    at com.android.dx.cf.direct.ClassPathOpener.processArchive(ClassPathOpener.java:205)
    at com.android.dx.cf.direct.ClassPathOpener.processOne(ClassPathOpener.java:130)
    at com.android.dx.cf.direct.ClassPathOpener.process(ClassPathOpener.java:10
    at com.android.dx.command.dexer.Main.processOne(Main.java:247)
    at com.android.dx.command.dexer.Main.processAllFiles(Main.java:183)
    at com.android.dx.command.dexer.Main.run(Main.java:139)
    at com.android.dx.command.dexer.Main.main(Main.java:120)
    at com.android.dx.command.Main.main(Main.java:89)
1 error; aborting
make: *** [out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes.dex] Error 1

---

