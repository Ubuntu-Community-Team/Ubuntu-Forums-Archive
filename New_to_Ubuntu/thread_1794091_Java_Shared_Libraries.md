---
title: "Java Shared Libraries"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by driebel on 2011-06-30
I'm looking to construct and interface so that one program (the Aladin image server) can be controlled by a scripting language (IDL).  Fortunately, all the hard work has been done for me and I have a (mostly) ready to use suite of software to handle it.  The only rub is that the developers of this package have used IDL's JAVA bridge, and I know absolutely nothing about JAVA.  The setup is rather straight forward (from the README):

> 
Before being able to use the API, you need to properly configure the IDL Java Bridge :

* create a new file $HOME/.idljavabrc with the following line :

      JVM Classpath = $CLASSPATH:$HOME/jar/Aladin.jar

      This property will tell IDL where to find needed Java classes

* create an environment variable called IDLJAVAB_LIB_LOCATION and pointing the JVM shared library to be used. For instance, your .tcshrc file may have the following lines : 

      setenv JAVA_HOME /usr/java/jdk1.5.0_04
      setenv IDLJAVAB_LIB_LOCATION $JAVA_HOME/jre/lib/i386/client


Easy enough until those last steps.  I'm not sure where to find my JVM shared library.  It's not under /usr/java, there's no such directory.  I have found /usr/lib/jvm which contains

java-1.5.0-gcj-4.4
.java-6-openjdk.jinfo
.java-6-sun.jinfo
java-1.6.0-openjdk
java-6-sun
java-gcj
java-1.5.0-gcj
java-6-openjdk
java-6-sun-1.6.0.24
java-gcj-4.4

I've followed a few of these through ./jre/lib/amd64/ but haven't yet found one containing a "client."
I'm running Lucid on a 64-bit machine (using a 32-bit version of IDL 7.0, if that helps).  Does anyone know what my best local equivalent to /usr/java/jdk1.5.0_04/jre/lib/i386/client is?  Also, if you could explain what some of those 10 java-X.X links are, and if I really need 10 of them, I'd appreciate it.

Cheers,
Dave

---

### Post by jtarin on 2011-06-30
> * create an environment variable called IDLJAVAB_LIB_LOCATION and pointing the JVM shared library to be used. For instance, your .tcshrc file may have the following lines :

setenv JAVA_HOME /usr/java/jdk1.5.0_04
setenv IDLJAVAB_LIB_LOCATION $JAVA_HOME/jre/lib/i386/client First...unless your using the shell tcsh...your environment variables will be set in .bashrc in your /home/username directory.

---

