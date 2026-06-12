---
title: "Java - Installed but can't use 'javac'?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-05-05
I am trying to get Java installed so I can program with it. I already installed both the JRE and JDK into my ~/home folder so I have easy access to it. The only thing I can't seem to do is compile. I followed a tut to make a simple Hello, World! program, but when it comes to compile it, when I go to the Terminal and run javac HelloWorld.java, it doesn't work. It instead displays"

```

unknownfear@ubuntu:~/java$ javac HelloWorld.java
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>
unknownfear@ubuntu:~/java$ 

```

Any help with this? Better yet, if it makes a difference, I will delete both JRE and JDK directories from my Home folder and, maybe someone can tell me step-by-step how to install it properly to make Java programs?

---

### Post by doas777 on 2010-05-05
> **UnknownFear said:**
> I already installed both the JRE and JDK into my ~/home folder..."


well that is likely the issue. 
try removing them and then install the openjdk from the repos via synaptic, 
or enable the partner repos and use these instructions to install the sun jre/sdk: [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

---

### Post by peculiar penguin on 2010-05-05
You need to specify the full path to the compiler binary (I really doubt it's lying around in  ~/java, if you manually installed it there look for subdirectories called bin or similar), or add the directory it's in to your path so the system can find it automatically.

Generally, as doas777 mentioned, try the stuff from the repositories first (which should take care of things like this automatically) instead of manually downloading stuff and shoehorning it into the system.

---

### Post by UnknownFear on 2010-05-05
> **doas777 said:**
> well that is likely the issue. 
try removing them and then install the openjdk from the repos via synaptic

That worked like a charm :) Thanks!!

---

