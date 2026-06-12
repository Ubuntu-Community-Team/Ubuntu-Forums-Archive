---
title: "how to get java version jre-6u13-linux-x64.bin working"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2009-06-11
I need to access a certain Government website called Service Canada for income tax purposes. The site says I have an "older" version of java installed and provides me with a link that leads to this version of java "jre-6u13-linux-x64.bin" (I think the most recent version is jre-6u14-linux-x64.bin)?

Anyhow, when I ran the command java -version it tells me that I have the following version:

brian@brian-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
brian@brian-laptop:~$ 

What is confusing to me is that there are seemingly 2 javas on my computer, the openJDK version which seems to be the default that the Government website says is outdated and a "sun java 6 webstart located under "internet" in the GUI. I noted that clicking on the sun java 6 webstart produced no response. 

Also when I clicked on "system" then "preferences" then "Sun java 6 plugin control panel" in Gnome and then clicked "Java" it tells me that I have "product name" jre, version: 1.6.0_13 in "location" usr/lib/jvm java-6-sun-1.6.0.13/jre" and that it is "enabled."

My question is: Is version "java-6-sun-1.6.0.13/jre" the same application as "jre-6u13-linux-x64.bin that the Government site requires?"

If it is, how do I set it as default either temporarily or permanently so that the Government website that requires this version (or a later version) recognizes I have java and allows me to log in?

---

### Post by asmoore82 on 2009-06-11
there are multiple java's in the Repos for debian and *buntu systems.
if you have more than one installed, you can switch between them
by using the Debian "Alternatives" System.

The commandline tool to make changes is `update-alternatives` and is always available.
There is a graphical tool "galternatives" in the Repos: ```
sudo apt-get install galternatives
```
It shows up in the menu under "Applications -> System Tools" for me, or you can simply: ```
gksudo galternatives
```

You need to go to all the java entries, especially the javaplugin ones,
and set them to sun's "official" java ... I believe the ones that
really control Firefox's plugin are the xulrunner-*-javaplugin.so ones.

Firefox will have to be restarted to notice the change.

---

### Post by Brian_Newbie on 2009-06-11
Thanks a bunch asmoore82. I installed the galternatives in terminal, then in the GUI opened it, selected the sun java radio button which de-selected the openJDK, restarted firefox and now I am able to log into the Government website. 

Thanks again!!

p.s. Isn't there a "thank-you" icon and "solved thread" icon that I can use in thanking posters?

---

### Post by asmoore82 on 2009-06-13
:guitar: Excellent!

I myself keep the ancient sun-java-5 selected because it works the best with yahoo games :oops:

---

