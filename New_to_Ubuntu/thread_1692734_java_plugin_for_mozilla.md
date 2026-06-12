---
title: "java plugin for mozilla"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-02-21
How to install java plugin in mozilla? How to install java plugin in google chrome? I have got jre already.

---

### Post by YesWeCan on 2011-02-21
If you have installed the Oracle/Sun JRE, see [http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

---

### Post by Frogs Hair on 2011-02-21
See if this is the same plug-in. [http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

---

### Post by RobikShrestha on 2011-02-21
thanks it works. but can i get the same plugin for google chrome too?

---

### Post by gandaran on 2011-02-22
> **RobikShrestha said:**
> thanks it works. but can i get the same plugin for google chrome too?
all you need is install the java plugin from ubuntu software center or synaptic package manager, this plugin works on every browser including google chrome.
installing java from the oracle website is a mistake when you have everything in ubuntu package manager system.
there are two java plugins, one is for the openjdk-java packages and is called the [COLOR="Red"]icedtea-plugin[/COLOR], install this one if you want to use openjdk-java but some people say openjdk-java doesn't work very well on some websites.
to install sun-java instead you will have to enable the archive.canonical partner repository in software sources and update the software package list then you can find the [COLOR="Red"]sun-java6-plugin[/COLOR] ready for install in package manager.

---

### Post by YesWeCan on 2011-02-22
Hang on.
It depends what the OP wants. If the OP wants the official Oracle/Sun Java then they certainly do not want OpenJava/IcedTea on their system.

The official Sun Java is not the same as OpenJava.

Personally, I always use the official Java. Why not?
I don't know what the point is of OpenJava other than avoiding licensing issues.

---

### Post by Old_Man_Unix on 2011-02-22
> **YesWeCan said:**
>  
Personally, I always use the official Java. Why not?
I don't know what the point is of OpenJava other than avoiding licensing issues.

The point is that SunJava is not open source. If that doesn't bother you, go ahead and use it.  If it does bother you, use the open source equivalent.   BTW,  it does perform a lot better than you imply. 

The great thing about Linux is that you have a choice.

---

### Post by gandaran on 2011-02-22
> **YesWeCan said:**
> Hang on.
It depends what the OP wants. If the OP wants the official Oracle/Sun Java then they certainly do not want OpenJava/IcedTea on their system.

The official Sun Java is not the same as OpenJava.

Personally, I always use the official Java. Why not?
I don't know what the point is of OpenJava other than avoiding licensing issues.
the point is if the OP wants sun-java and if he can easily install the same sun-java package which includes a plugin that works in every browser from package manager why download from oracle website?

---

### Post by YesWeCan on 2011-02-22
> **Old_Man_Unix said:**
> The point is that SunJava is not open source. If that doesn't bother you, go ahead and use it.  If it does bother you, use the open source equivalent.   BTW,  it does perform a lot better than you imply. 

The great thing about Linux is that you have a choice.
Why would not using an open source version of an application bother me? Why would it bother anyone?

I am all in favour of community software projects whose intention is to bring free access to the people of proprietary applications.

In the case of Java I just don't see the point. I can see a licensing point but that doesn't affect you unless you are going to commercialize something. And if you were going to commercialise I doubt you would risk using OpenJava.

Sun Java is of excellent quality, always up to date and already completely free.

Please help me understand why anyone would prefer OpenJava.

It would be like Microsoft offering free Office for linux (we can dream) and then someone deciding to create an open source version to mimmick it.

---

### Post by ratcheer on 2011-02-22
> **YesWeCan said:**
> 

Sun Java is of excellent quality, always up to date and already completely free.

Please help me understand why anyone would prefer OpenJava.



No, it is free as in beer but not free as in speech. That distinction certainly does matter to most proponents of FOSS. In fact, the free speech aspect is much more important to FOSS than being free in the sense of money.

Tim

---

