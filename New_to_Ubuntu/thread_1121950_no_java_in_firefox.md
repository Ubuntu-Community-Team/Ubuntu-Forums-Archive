---
title: "no java in firefox"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by rveska on 2009-04-10
Hi.
I've just tried to install kubuntu. I've used ubuntu for about one and a half years, but some of my bodies told me kubuntu/KDE was better; so I figured it was a great project for my holiday. But now java isn't running in firefox. I've installed sun-java in the package manager, but firefox says that I need to install the plugin, but when I try, it says that I need to do manually.
Does anyone know what to do?

   - Skannrup

---

### Post by SuperSonic4 on 2009-04-10
Did you try ```
sudo apt-get install sun-java6-plugin
```

---

### Post by gandaran on 2009-04-10
> **Skannrup said:**
> Hi.
I've just tried to install kubuntu. I've used ubuntu for about one and a half years, but some of my bodies told me kubuntu/KDE was better; so I figured it was a great project for my holiday. But now java isn't running in firefox. I've installed sun-java in the package manager, but firefox says that I need to install the plugin, but when I try, it says that I need to do manually.
Does anyone know what to do?

   - Skannrup
install the sun-java6-plugin!

---

### Post by ubudog on 2009-04-10
I think there is a java applet thing that you can get as some kind of add on for firefox.  I tried it in 8.10 and it didn't work.  It works in 8.04.  Sorry I don't really remember much else.

---

### Post by SuperSonic4 on 2009-04-10
If the repos fail you can try installing it manually by following the guide at [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

### Post by rveska on 2009-04-10
No good. I already have java installed, it just doesn't seem to registrer with firefox.

---

### Post by freeman2000 on 2009-04-12
I was also having the same problem.  I had installed Java for Jaunty with all the extras/plugins/dependencies/etc thru Synaptics, but still had problems with Firefox.  So in Firefox, I clicked on Tools --> AddOns --> Get AddOns.  In the search box I typed Java.  A list came back, and I installed the latest version - Java Console 6.0.2 which solved my problem.  Good luck.

---

### Post by rveska on 2009-04-13
Hi,
I have solved my problem with the latest version of java from sun; and a little help from about:plugins.

   - Skannrup

---

