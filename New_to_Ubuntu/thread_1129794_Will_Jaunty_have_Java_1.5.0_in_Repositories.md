---
title: "Will Jaunty have Java 1.5.0 in Repositories"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by mikodo on 2009-04-19
Hello Everyone,

I would like to run JSword. Presently, the only way to use this Bible program in Linux is to have a version of Sun's Java (JDK 1.4 or higher) that will run it; not the gcj version of Java that is included in the Hardy distro that I use.The page from this link: [http://www.crosswire.org/jsword/linuxjava.html](http://www.crosswire.org/jsword/linuxjava.html)  explains how to obtain and install Java for Linux, which presumably will run JSword. As a newbie I am not comfortable attempting this work-up; Secondly for now, I would prefer to stick to repositories provided by Ubuntu. 

Does anybody know if Jaunty or the next version is going to have the needed Java JDK 1.4 or higher (ie.1.5) in their repositories? I plan to stick with Hardy until I have become comfortable with Linux, but would consider Jaunty if I could have a good Bible program like JSword easily from it's repositories of newer Java releases.

(I hope I didn't write a lot of gobily-goop, that makes no sense to anyone). 

Thank you

---

### Post by pspsampsp on 2009-04-19
there is sun-java6-jre/jdk and sun-java5-jre/jdk in 8.10 (intrepid ibex) and 9.04 (jaunty jackalope) i think if you enable the multiverse repositories it should be available in 8.04. To enable them click system -> administration -> software sources and the option should be there.

---

### Post by mikodo on 2009-04-19
Thank you for your response. What should I do once I am in Software sources?

---

### Post by Sef on 2009-04-19
> What should I do once I am in Software sources?

Easy to install java:

Applications > Add/Remove > Show: 'All Applications Available' > Search: Sun Java > click on the box next to what java you want > appy changes > apply > close.

---

### Post by mikodo on 2009-04-19
Thank you; 

 OpenJDK Java  Runtime
OpenJDK Java runtime, using Hotspot JIT 
Full Java runtime environment - needed for executing Java GUI and Webstart programs. Using Hotspot JIT.
The packages are built using the IcedTea build support and patches from the IcedTea project.

This application is provided by the Ubuntu community.

Does the last line mean that this is supported by Ubuntu and I will receive updates when ubuntu becomes aware of fixes?

mikodo

---

### Post by freak42 on 2009-04-19
Yes, the OpenJDK Version of Java is an open source version, therefore security problems can be expected to be fixed quite fast and automatically updated by your ubuntu updater.

by the way, after installing another version of java you might have to tell ubuntu which java to use as default, here is a little tutorial that helps you do that [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) .
(To see what version is currently default use "java -version" on a command line)

hth

---

### Post by mikodo on 2009-04-19
Thank you everyone,

I will read all the posts and links carefully. In my past life with MS, Sun did not always issue fixes in a timely manner, which left me wary of them. Now with Ubuntu, and from what I have already read from you, it should be safe to use the scripting now.

Best regards,

Mikodo

---

