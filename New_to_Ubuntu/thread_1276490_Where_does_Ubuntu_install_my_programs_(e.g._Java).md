---
title: "Where does Ubuntu install my programs? (e.g. Java)"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by gemm on 2009-09-27
Hello,

I cannot understand where Ubuntu installs my programs. For example, in the Synaptic Package Manager I have  written java. I have marked sun-java6-jdk and install it. Now when I type in my console "which java", I get /usr/java/bin. But as I can see it, in /usr/bin there are only executables. Where is the folder of java6-jdk? Because what if I want to install java5-jdk now and use it instead of java6-jdk. The executable is just "java" and doesn't specify whether it is java5 or java6. 

In my profile file, I have added this:

export JAVA_HOME=/usr/bin

I am not sure whether it was necessary. But anyway, this is just "java" and I don not know how to understand which version of Java I am using. From the Sunaptic Package Manager I ca see that java6-jdk is installed, because it is marked as green, however, I do not understand where, and I do not understand whether I am actually using java6. What if before installing java6-jdk there was some other java isntalled, and I am still using the old Java. How can I check all these thing? Thanks a lot in advance.

---

### Post by mapes12 on 2009-09-27
[http://amitech.50webs.com/installing/index.php.html#where_did_it_go](http://amitech.50webs.com/installing/index.php.html#where_did_it_go)

---

### Post by oldos2er on 2009-09-27
** java -version** entered into a terminal should show you just that. **dpkg -L <package name>** , e.g. **dpkg -L sun-java6-jre** will show you the location where each file in a particular package has been installed. You can also see this in Synaptic, click Status (lower left), Installed, right-click on an installed package and choose Properties, Installed Files.

---

