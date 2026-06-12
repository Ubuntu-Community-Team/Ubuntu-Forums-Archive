---
title: "What do I do with this JAR file I downloaded from sourceforge?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Spacestationmax on 2010-08-11
What do I do with this JAR file I downloaded from sourceforge?

---

### Post by surfer on 2010-08-11
if you have java installed (and you are sure that the program does not do anything harmful):

open a shell and call

```
java -jar yourfile.jar
```

---

### Post by Spacestationmax on 2010-08-11
max@EeePC901:~/Desktop/maxjar$ java -jar BluePad.jar
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
max@EeePC901:~/Desktop/maxjar$ 

Hmmmm which one of those do I want???

---

### Post by surfer on 2010-08-11
i'd suggest

```

$ sudo apt-get install openjdk-6-jre

```

---

### Post by Spacestationmax on 2010-08-11
max@EeePC901:~/Desktop/maxjar$ sudo apt-get install openjdk-6-jre
[sudo] password for max: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b14-1.4.1-0ubuntu7) but it is not going to be installed
E: Broken packages
max@EeePC901:~/Desktop/maxjar$ 

Hmm?

---

### Post by surfer on 2010-08-11
ups, my mistake:

```

$ sudo apt-get install openjdk-6-jre openjdk-6-jre-headless

```

should apt-get complain about more missing dependencies, just add them to the line.

---

### Post by Spacestationmax on 2010-08-11
max@EeePC901:~/Desktop/maxjar$ sudo apt-get install openjdk-6-jre-headless
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: tzdata-java but it is not going to be installed
E: Broken packages
max@EeePC901:~/Desktop/maxjar$ sudo apt-get install tzdata-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2009f-0ubuntu1) but 2009l-0ubuntu0.9.04 is to be installed
E: Broken packages
max@EeePC901:~/Desktop/maxjar$ sudo apt-get install 2009l-0ubuntu0.9.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2009l-0ubuntu0.9.04
max@EeePC901:~/Desktop/maxjar$ A

I really have no idea whats going on in this wacky linux world?

---

### Post by surfer on 2010-08-11
did you open synaptic and try to install that way? is usually easier than apt-get.

---

### Post by Spacestationmax on 2010-08-11
Was I supposed to do this?

sudo apt-get install openjdk-6-jre openjdk-6-jre-headless tzdata-java 2009l-0ubuntu0.9.04

---

### Post by Spacestationmax on 2010-08-11
> **surfer said:**
> did you open synaptic and try to install that way? is usually easier than apt-get.

I know how get to synaptic, search for openjdk-6-jre but when I mark it for install and apply It doesn't work

Could not mark all packages for install or upgrade
openjdk-6-jre:
 Depends: openjdk-6-jre-headless but it is not going to be installed

---

### Post by TNT1 on 2010-08-11
> **surfer said:**
> if you have java installed (and you are sure that the program does not do anything harmful):

open a shell and call

```
java -jar yourfile.jar
```


Can't you just right click on it and open with (whatever jave runtime you use)?

---

### Post by Spacestationmax on 2010-08-11
> **TNT1 said:**
> Can't you just right click on it and open with (whatever jave runtime you use)?

Nope .. It asks me what app to use and i dont see anything that looks like java

---

