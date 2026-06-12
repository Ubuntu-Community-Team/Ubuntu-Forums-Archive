---
title: "Programs not installing due to java error"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by DavidG24 on 2009-06-09
G'day everyone,

I am extremely new to Ubuntu (and Linux in general) so please be kind and detailed in your solutions.

I must have installed the Javadoc 5, 6 libraries incorrectly as I am constantly unable to install applications using the Synaptic Package Manager which crashes due to this for.

For example, I tried to install sun-java6-plugin (and this is just an example its happened with numerous other applications) using the Synaptic Package Manager and got the following message,

 Setting up sun-java6-doc (6-20-0ubuntu2) ...

This package is an installer package, it does not actually contain the JDK documentation. You will need to go download one of the following archives
jdk-6-doc.zip jdk-6-doc-ja.zip
(choose the no-update version if this is the first installation).
Please visit
[http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)
now and download. The file should be owned by root.root and be copied to /tmp.
[Press RETURN to try again, 'no' + RETURN to abort]

after a few RETURNS it kept given the same error message so I enter 'no' and it breaks the installation.

I tried to follow the instructions given, with no luck.

Is there an easy way to correct this?

Again please be detailed as I'm a complete NOOB to linux.

Thanks in advance,

David

ps - I'm running Ubuntu 8.10

---

### Post by blackxored on 2009-06-09
sun-java*-doc is not a real package, it's an installer one. It will download the javadoc from Sun and extract it to /tmp. If you're download failed (weird since uses wget -c) then It won't install. Try removing the docs and the installing the JRE sun-java6-jre or the JDK sun-java6-jdk or try openjdk. Hope it helps.

---

### Post by reeseslover531 on 2009-06-09
I think there is some sort of issue with downloading the java docs on ubuntu, just go to that website and download the documentation and put it in your /tmp folder and make sure root owns it. To do this type:
```
sudo chown root:root /tmp/nameofDoc.zip
``` and put the correct filename in, and then try and reinstall.  That should work.

---

### Post by DavidG24 on 2009-06-09
hey everyone,

Thanks for your responses, I found what is probably an inefficient way of solving the problem...but it worked.

As per instructed, I went into the Synaptic Package Manager, un-installed every java item I could see, and then re-installed them. Now everything is working well.

Probably a laughable solution, but for the time being I'm happy

Thanks again for the responses,

David

---

