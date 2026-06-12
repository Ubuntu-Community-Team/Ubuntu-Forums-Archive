---
title: "How to install java 1.5 on unbuntu 11.04?"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by TERW_DAN on 2011-09-07
I'm currently setting up a developmentmachine for developing for an Android device, which requires Java 1.5 to be installed. Currently only java 1.6 is installed, but I cannot seem to be able to install version 1.5. 
 
When I try to use apt-get, it says the package has no installation candidate, and in the software manager, there is no mention of version 1.5 at all. 
 
When I try to find an installer on the web, I only find Windowsbased installers, so that isn't going to help me. 
 
Does anyone know where to get an installer or something to get java1.5 working on Ubuntu 11.04?

---

### Post by Nickjpost on 2011-09-07
I don't use Java but perhaps this site can bring you towards your goal: [http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html](http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html)

---

### Post by Paqman on 2011-09-07
Java 1.5 hasn't been in the repositories since Hardy. Since the Hardy repos are still open for servers you could try installing it [manually]("http://packages.ubuntu.com/hardy-updates/sun-java5-jre"). You might need to sort some dependencies, such as [this]("http://packages.ubuntu.com/hardy-updates/sun-java5-bin") file. After that run:
```
sudo update-alternatives --config java
```
in a terminal to switch to it.

Don't know for sure if this will work, I've never tried it.

---

### Post by TERW_DAN on 2011-09-07
running update-alternatives --config java gives me an error there is nothing to config, since only java 1.6 is installed. 
 
Does anyone have Java 1.5 running on 11.04? Otherwise I'll have to find me an old ubuntu 8 or something to see if it works there.

---

### Post by Azdour on 2011-09-07
Hi,

Its been a long time since I had to use an old version of Java so the following is from memory only.

If you need an older version of Java you are going to need to install it without the help of the synaptic package manager:

[LIST=1]
[*]Download the '.bin' version of v1.5 (v5) from: [http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html](http://www.oracle.com/technetwork/java/javase/downloads/index-jdk5-jsp-142662.html)
[*] Go to [http://www.oracle.com/technetwork/java/javase/install-139487.html](http://www.oracle.com/technetwork/java/javase/install-139487.html) and click on the link for the relevant install instructions link
[/LIST]

Follow the install instructions and use:
```
sudo update-alternatives --config java
```
To switch from 1.6 to 1.5

---

### Post by TERW_DAN on 2011-09-08
I followed the installation instructions and it seems to copy/extract files to a directory, but when I try to run sudo update-alternatives -- config java, it says there is only one alternative in link groud java. 
 
How do I manage these link groups? I am used using installers like in Windows, that actually install something, this only seems to copy things.

---

### Post by Azdour on 2011-09-08
Hi,

I think because you installed it yourself without the help of dkpg or synaptic package manager you will now need to tell Ubuntu about this version of Java. You'll need to know where the jdk1.5 is installed in order to alter the path set out in the guide below:

[http://daily-hacking.blogspot.com/2010/04/add-java-runtime-to-ubuntu-using-update.html](http://daily-hacking.blogspot.com/2010/04/add-java-runtime-to-ubuntu-using-update.html)

---

### Post by Paqman on 2011-09-08
> **TERW_DAN said:**
> running update-alternatives --config java gives me an error there is nothing to config, since only java 1.6 is installed. 

Did you download and install the .deb packages from the pages I linked to? The download link is at the bottom left. You'll need both.

---

### Post by servventer on 2011-09-08
After following the Oracle instructions ([http://www.oracle.com/technetwork/java/javase/install-linux-138610.html](http://www.oracle.com/technetwork/java/javase/install-linux-138610.html)) run this command in terminal:

sudo update-alternatives --install /usr/bin/java java /opt/java/jre1.5.0_22/bin/java 100

make sure the "opt/java/jre1.5.0_22/bin/java" points to the directory where you installed the .bin

do a #java -version to confirm

---

### Post by eostang on 2012-04-09
I followed [servventer]("http://ubuntuforums.org/member.php?u=1433437") instruction. It works for me. Thank you!

---

### Post by sammiev on 2012-04-09
I suspect with that java version you will be hacked rather sooner than later. Why not update to the current version?

---

