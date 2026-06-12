---
title: "Javac"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by brenan on 2009-01-07
I'm trying to compile a java file using javac, but whenever I do, it gives me this error: The program 'javac' can be found in the following packages:
 * gcj-4.2
 * jikes-sun
 * jikes-sablevm
 * kaffe
 * jikes-classpath
 * java-gcj-compat-dev
 * ecj
 * gcj-4.3
 * cacao-oj6-jdk
 * openjdk-6-jdk
 * jikes-kaffe
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found


But the output of the command 'java -version' shows me this:
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

Any ideas?

---

### Post by Tim Sharitt on 2009-01-08
You've only got the java runtime installed, which is only for running compiled java programs. The java compiler is separate. I would say that you either need sun-java6-sdk or gcj-4.3, depending on what you need it for. If your application is going to be used across other platforms, I would suggest the sun jdk for compatability reasons.

---

