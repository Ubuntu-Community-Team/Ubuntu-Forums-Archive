---
title: "installing jdk"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by abhishek_n on 2009-01-04
guys how do i install jdk to compile java codes????
when i try to install it says must be root .
when i try 'sudo -i' it still does not work ??
also wat is the default password if use 'su' command

---

### Post by fooman on 2009-01-04
you could use synaptic to install (system > administration > synaptic package manager).  just search synaptic for "sun-java6-jdk"

or in a terminal:

```
sudo apt-get install sun-java6-jdk
```

---

### Post by sadaruwan12 on 2009-01-04
> **fooman said:**
> you could use synaptic to install (system > administration > synaptic package manager).  just search synaptic for "sun-java6-jdk"

or in a terminal:

```
sudo apt-get install sun-java6-jdk
```
You can do it using the command line or just got System -> Administration -> Synaptic Package Manager and search sun-java6-jdk other wise you can use the open source version for Sun Java openJDK search for openjdk-6-jdk when you finds it click on that package then from the pop up click on "Mark for installation". Now click on apply on top tool bar then from the dialog click on apply again and this will install all the components needed including dependencies if needed. If asked give your password that you use to log in to you Ubuntu OS after completing this you're ready to go close the SPM and start using Java. \\:D/

---

