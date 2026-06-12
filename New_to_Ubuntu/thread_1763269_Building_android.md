---
title: "Building android:"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by ssprabu on 2011-05-20
hi  new to this field..............
while building android file system/////
in 32 bit Ubuntu with Java 1.6
after make command 

after few lines of execution it stops with

target Dex:core 

how to resolve this...............?

---

### Post by Sub101 on 2011-05-20
Can you add some background to what you are doing.

---

### Post by wep940 on 2011-05-20
(1) Quit opening a new thread for this same issue

(2) If nobody responds, don't just post again or bump your thread.  This is an all-volunteer forum and the forum rules dictate waiting 24 hours before bumping your thread.

---

### Post by ssprabu on 2011-05-20
hey thank  
i m new to this ............
i m trying to work on panda board so building android flat-form,
i followed all the steps given in pandaboard.org and i downloaded sun Java jdk 1.6.22 
after make clean 
and make command i m getting the following errors   

install: out/host/linux-x86/lib/libneo_util.so 
 Install: out/host/linux-x86/lib/libneo_cs.so 
 Install: out/host/linux-x86/lib/libneo_cgi.so 
 Install: out/host/linux-x86/lib/libclearsilver-jni.so 
 target Java: core (out/target/common/obj/JAVA_LIBRARIES/ 
 core_intermediates/classes) 
 Note: Some input files use or override a deprecated API. 
 Note: Recompile with -Xlint:deprecation for details. 
 Note: Some input files use unchecked or unsafe operations. 
 Note: Recompile with -Xlint:unchecked for details. 
 host Java: dx (out/host/common/obj/JAVA_LIBRARIES/dx_intermediates/ 
 classes) 
 Note: Some input files use unchecked or unsafe operations. 
 Note: Recompile with -Xlint:unchecked for details. 
 Install: out/host/linux-x86/framework/dx.jar 
 Copy: dx (out/host/linux-x86/obj/EXECUTABLES/dx_intermediates/dx) 
 Install: out/host/linux-x86/bin/dx 
 target Dex: core

---

### Post by ssprabu on 2011-05-20
hey thank  
i m new to this ............
i m trying to work on panda board so building android flat-form,
i followed all the steps given in pandaboard.org and i downloaded sun Java jdk 1.6.22 
after make clean 
and make command i m getting the following errors   

install: out/host/linux-x86/lib/libneo_util.so 
 Install: out/host/linux-x86/lib/libneo_cs.so 
 Install: out/host/linux-x86/lib/libneo_cgi.so 
 Install: out/host/linux-x86/lib/libclearsilver-jni.so 
 target Java: core (out/target/common/obj/JAVA_LIBRARIES/ 
 core_intermediates/classes) 
 Note: Some input files use or override a deprecated API. 
 Note: Recompile with -Xlint:deprecation for details. 
 Note: Some input files use unchecked or unsafe operations. 
 Note: Recompile with -Xlint:unchecked for details. 
 host Java: dx (out/host/common/obj/JAVA_LIBRARIES/dx_intermediates/ 
 classes) 
 Note: Some input files use unchecked or unsafe operations. 
 Note: Recompile with -Xlint:unchecked for details. 
 Install: out/host/linux-x86/framework/dx.jar 
 Copy: dx (out/host/linux-x86/obj/EXECUTABLES/dx_intermediates/dx) 
 Install: out/host/linux-x86/bin/dx 
 target Dex: core

---

### Post by philinux on 2011-05-20
@ssprabu,

I've deleted your duplicate Thread. Cheers.

---

### Post by mikechant on 2011-05-20
None of those messages look like fatal errors, they just look like warnings. Are you sure that the 'make' has actually failed?

---

