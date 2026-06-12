---
title: "Java 3D Installation"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by ashwat on 2009-03-24
How do I go about changing or setting the paths for the Java 3d installation? I am a noob at Ubuntu and Java programming, but another program that I need to work on needs Java 3D and as luck would have it, this is urgent.

I downloaded the zip file and extracted the contents into 

home/username/j3d/lib
the ext and i386 folders are in the same

I now need to set the classpath to this path.

---

### Post by ashwat on 2009-03-25
bump

---

### Post by Flimm on 2010-01-25
This worked for me:

```
sudo aptitude install libjava3d-java
sudo cp /usr/share/java/j3d*.jar /usr/lib/jvm/java-6-sun/jre/lib/ext/
```

---

### Post by crobeles on 2010-03-29
Doesn't work for me. When trying to run an example, I get: 

Exception in thread "main" java.lang.UnsatisfiedLinkError: no j3dcore-ogl in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1709)
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1028)
    at javax.media.j3d.NativePipeline$1.run(NativePipeline.java:231)
    at java.security.AccessController.doPrivileged(Native Method)
    at javax.media.j3d.NativePipeline.loadLibrary(NativePipeline.java:200)
    at javax.media.j3d.NativePipeline.loadLibraries(NativePipeline.java:157)
    at javax.media.j3d.MasterControl.loadLibraries(MasterControl.java:987)
    at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUniverse.java:299)
    at javax.media.j3d.Canvas3D.<clinit>(Canvas3D.java:3881)
    at HelloJava3Dd.<init>(HelloJava3Dd.java:94)
    at HelloJava3Dd.main(HelloJava3Dd.java:115)


This is after installing java3d as per the above post. Any ideas? I am new to all of this and seem unable to figure it out.

---

### Post by derrekito on 2010-06-19
BUMP!!

I also receive the "no j3dcore-ogl" error.

---

### Post by lkjoel on 2010-06-19
> **Flimm said:**
> This worked for me:

```
sudo aptitude install libjava3d-java
sudo cp /usr/share/java/j3d*.jar /usr/lib/jvm/java-6-sun/jre/lib/ext/
```
I like 
```
sudo apt-get install libjava3d-java
sudo cp /usr/share/java/j3d*.jar  /usr/lib/jvm/java-6-sun/jre/lib/ext/
``` better.

---

### Post by Miguel on 2010-08-03
For reference, the file **libj3dcore-ogl.so** is located in the package libjava3d-jni. It is still possible for java to complain about vecmath, a jar contained in the original libjava3d-java that you previously installed. So if you need any of this in order to get java3d, perform the following:
```

sudo aptitude install libjava3d-jni
sudo cp /usr/lib/jni/libj3dcore-ogl.so /usr/lib/jvm/java-6-sun/jre/lib/i386/
sudo cp /usr/share/java/vecmath-*.jar /usr/lib/jvm/java-6-sun/jre/lib/ext/

```

If you are using a 64 bit system (as is my case) you should substitute "i386" with "amd64" in the last command. There are, however, a few more things you should know. First of all, this works with both openjdk and sun's java. At least crystall0graph does. Second, when java is updated, chances are you'll have to put all these libraries again.

---

### Post by protivakid on 2010-10-30
> **lkjoel said:**
> I like 
```
sudo apt-get install libjava3d-java
sudo cp /usr/share/java/j3d*.jar  /usr/lib/jvm/java-6-sun/jre/lib/ext/
``` better.
Worked for me!

---

### Post by protivakid on 2010-10-30
> **Miguel said:**
> For reference, the file **libj3dcore-ogl.so** is located in the package libjava3d-jni. It is still possible for java to complain about vecmath, a jar contained in the original libjava3d-java that you previously installed. So if you need any of this in order to get java3d, perform the following:
```

sudo aptitude install libjava3d-jni
sudo cp /usr/lib/jni/libj3dcore-ogl.so /usr/lib/jvm/java-6-sun/jre/lib/i386/
sudo cp /usr/share/java/vecmath-*.jar /usr/lib/jvm/java-6-sun/jre/lib/ext/

```If you are using a 64 bit system (as is my case) you should substitute "i386" with "amd64" in the last command. There are, however, a few more things you should know. First of all, this works with both openjdk and sun's java. At least crystall0graph does. Second, when java is updated, chances are you'll have to put all these libraries again.

Also needed to get java3d working in Ubuntu 10.04.1 w/ Eclipse

---

