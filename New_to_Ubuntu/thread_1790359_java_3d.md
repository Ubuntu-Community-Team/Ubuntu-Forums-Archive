---
title: "java 3d"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by &lt;(-.-)&gt; on 2011-06-24
I'm trying to install java 3d.  I installed libjava3d-java, libjava3d-jni through synaptic, downloaded the java 3d, and tried to move the jar files to  /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/ext but the java-6-sun-1.6.0.15 folder does not exist. do i just need to create it or do i need to install something.

---

### Post by jtarin on 2011-06-25
> **<(-.-)> said:**
> I'm trying to install java 3d.  I installed libjava3d-java, libjava3d-jni through synaptic, downloaded the java 3d, and tried to move the jar files to  /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/ext but the java-6-sun-1.6.0.15 folder does not exist. do i just need to create it or do i need to install something.Open Synaptic Package Manager an search for Sun Java and install.

---

### Post by &lt;(-.-)&gt; on 2011-06-25
there are several sun java packages. which ones do i install?

---

### Post by Perfect Storm on 2011-06-25
> **<(-.-)> said:**
> there are several sun java packages. which ones do i install?

libjava3d-java

If you haven't already install sun java:

sun-java6-bin 
sun-java6-fonts
sun-java6-jre
sun-java6-plugin

---

### Post by &lt;(-.-)&gt; on 2011-06-25
none of the sun-java6 packages are in synaptic. is there a repository that i need to add?

---

### Post by Perfect Storm on 2011-06-25
You have to enable 'Canonical Partner' in your sourcelist first.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=195947&stc=1&d=1309024333[/IMG]

---

### Post by jtarin on 2011-06-25
A guy's gotta sleep sometime! :p Glad you got help.

---

