---
title: "Enabling Java plugins in firefox and google chrome"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by ItBala on 2011-05-29
I'm using google chrome and firefox (3.6.17) browsers in my kubuntu 10.10 machine ..in both the browsers i'm getting the below error when it tries to execute the java applet

Error: Please click here to download Java. If you already have Java, please restart your browser and try again.

I'm getting the same message even after installing Java ..

home@home:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

Not sure how to enable Java on my browsers ...
in firefox i'm not seeing Java plugins under tools -> addons -> plugins and i have no idea how to enable java pulgins in google chrome..

---

### Post by jtarin on 2011-05-29
[Here ya go!]("https://help.ubuntu.com/community/Java") I recommend Sun Java and removing the others......but you keep what you want....after all it's free software.....exception being Sun Java.

---

### Post by ItBala on 2011-05-29
Thank you very much your help...

Yes you are correct I had two versions of Java, openjdk and sunJava..

I have uninstall openjdk and now using SUN java alone.. but after installing sun-java6-plugin (browser plugin) ... both my browsers are indicating that this plugin is outdated and need to updated.. 

on clicking the update plugin .. i'm reaching Java download page [http://www.java.com/en/download/manual.jsp#lin](http://www.java.com/en/download/manual.jsp#lin) where i can see only java rpms for linux versions...no deb files available...

Please help me in updating the sun-java6-plugins

---

### Post by wildmanne39 on 2011-05-29
> **ItBala said:**
> Thank you very much your help...

Yes you are correct I had two versions of Java, openjdk and sunJava..

I have uninstall openjdk and now using SUN java alone.. but after installing sun-java6-plugin (browser plugin) ... both my browsers are indicating that this plugin is outdated and need to updated.. 

on clicking the update plugin .. i'm reaching Java download page [http://www.java.com/en/download/manual.jsp#lin](http://www.java.com/en/download/manual.jsp#lin) where i can see only java rpms for linux versions...no deb files available...

Please help me in updating the sun-java6-plugins
Hi, when you get it installed using firefox if you use noscript it will disable java on a lot sites until you tell it not to.

---

### Post by jtarin on 2011-05-29
> **ItBala said:**
> Thank you very much your help...

Yes you are correct I had two versions of Java, openjdk and sunJava..

I have uninstall openjdk and now using SUN java alone.. but after installing sun-java6-plugin (browser plugin) ... both my browsers are indicating that this plugin is outdated and need to updated.. 

on clicking the update plugin .. i'm reaching Java download page [http://www.java.com/en/download/manual.jsp#lin](http://www.java.com/en/download/manual.jsp#lin) where i can see only java rpms for linux versions...no deb files available...

Please help me in updating the sun-java6-pluginsIf you look at the page link I gave you it gives youthe link to update your Java....or you can just use Synaptic package manager to install. Make sure you have the partner repository enabled.

---

### Post by ItBala on 2011-05-29
I have removed all the java versions installed and did a clean install on sun java via synaptic manager and my browsers now detects the java plugins and running applets accordingly ...

Thankyou very much for your help on this.

---

### Post by jtarin on 2011-05-29
Good! Mark as solved to help others.

---

### Post by wog on 2011-05-29
I notice the Sun site lists the latest version as 6.25, while the latest in Synaptic is 6.24.

So how is it possible to update to the latest version?

---

### Post by jtarin on 2011-05-29
> **wog said:**
> I notice the Sun site lists the latest version as 6.25, while the latest in Synaptic is 6.24.

So how is it possible to update to the latest version?6.24 is the most recent .deb package available in the repository. If you don't want to wait for it to up date you can go [here]("http://www.java.com/en/download/help/linux_install.xml#download") and follow the instructions for installing the "Linux self extracting binary file" or use the "alien" package in the repositories to convert the "Linux RPM package" to a ".deb" file and install that way. However unless you have some overpowering need to have that version I would stay with the one from the repositories. It works fine with all my Java apps. If you have Sun Java already there should be a Java update application in your menu. You might try that. Can't guarantee any of these outside of the repository will work as intended. If you feel confident and knowledgeable enough to know what your doing you can use any method, but keep track of installation directories.

---

### Post by lordadi on 2011-05-29
This should help, you can follow the instructions in my post #6 and #7 :)
[http://ubuntuforums.org/showthread.php?t=1769916](http://ubuntuforums.org/showthread.php?t=1769916)

---

### Post by wog on 2011-05-30
The line:
```
sudo apt-get update
```

After adding the ppa produces this line (amongst others):

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jtarin on 2011-05-30
That's because there is no Natty.......back up on the url
[http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/)
Use Maverick (which is.24 and not .25) or follow instructions in my previous post.

---

### Post by wog on 2011-05-30
Do you know how much time it takes before these things get updated in the repositories? I was pretty sure 1.6.25 came out before 11.04 did.

---

### Post by jtarin on 2011-05-31
> **wog said:**
> Do you know how much time it takes before these things get updated in the repositories? I was pretty sure 1.6.25 came out before 11.04 did.
Ha!!!! I think 1.6 came out before Ubuntu.:P

---

### Post by tx99h4 on 2012-03-25
Hello :p

```
sudo apt-get install icedtea6-plugin

```

---

### Post by d4m1r on 2012-03-25
> **jtarin said:**
> [Here ya go!]("https://help.ubuntu.com/community/Java") I recommend Sun Java and removing the others......but you keep what you want....after all it's free software.....exception being Sun Java.

x2. While I prefer open source, IcedTea and OpenJDK have been really flaky for me with Ubuntu 11.10 and Firefox 11. I eventually uninstalled them all and installed the official Java repo's.

---

