---
title: "Problem with installation of Java Platform, Enterprise Edition 6 SDK (with JDK)"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by sreeandg on 2011-06-02
Hi,
I am trying to install Java Platform, Enterprise Edition 6 SDK (with JDK 6 U25) on Ubuntu 11.04(natty). On running the .sh file for installation, I get the following error:
****************************************************
 ./java_ee_sdk-6u2-jdk-linux-x64-ml.sh
Could not locate a suitable jar utility.
Please ensure that you have Java 6 or newer installed on your system and accessible in your PATH or by setting JAVA_HOME
****************************************************
Why is it asking for an installed Java 6 when I am trying to install it? Please advice.
Thanks in advance!
SG

---

### Post by jamesidw on 2011-06-02
This may sound dumb, but why not try using Synaptic or the Software Center to install from the official repositories instead?
A manual installation is always going to be much trickier. You have to put it in the right folder and you can't always know if all it's dependencies are satisfied. [your's seems to expect you to already have the jre installed]

---

