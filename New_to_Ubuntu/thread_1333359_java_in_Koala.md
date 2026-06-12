---
title: "java in Koala"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by zhanglini on 2009-11-21
I am a bit confused by all the Java packages (when I was googling around), there seem to be many of them.

I only need Java to open some applets, local or in Firefox.  I am not programming anything.  To serve my MINIMAL need, which package is right for me?  and where do I get it?

Thanks

---

### Post by Jon Monreal on 2009-11-21
> **zhanglini said:**
> I am a bit confused by all the Java packages (when I was googling around), there seem to be many of them.

I only need Java to open some applets, local or in Firefox.  I am not programming anything.  To serve my MINIMAL need, which package is right for me?  and where do I get it?

Thanks

In Synaptic, you should have sun-java6-bin, sun-java6-jre, and sun-java6-plugin (for viewing web applets). It's sun-java6-jdk that is the Java Development Kit.

---

### Post by zhanglini on 2009-11-23
> **Jon Monreal said:**
> In Synaptic, you should have sun-java6-bin, sun-java6-jre, and sun-java6-plugin (for viewing web applets). It's sun-java6-jdk that is the Java Development Kit.

Thanks Jon, that is exactly what I need!

---

### Post by Pjotr123 on 2009-11-23
That version is insecure and won't be updated. I advise strongly, to install the latest JRE update 17, which is secure, *by hand*. 

Here you can find a how-to: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Axos on 2009-11-23
> **Pjotr123 said:**
> Here you can find a how-to: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
Wow, that how-to explains where the 64-bit plug-in is! Why does Sun's site say there is no plug-in for 64-bit Linux? I need to correct a post I made a few days ago. Thanks!

Here's a quote from Sun's site:

"For Java Plug-in and Java Web Start on 64-bit Linux systems, support is not offered at this time. "

[http://java.sun.com/javase/6/webnotes/install/system-configurations.html#deployment-footnotes](http://java.sun.com/javase/6/webnotes/install/system-configurations.html#deployment-footnotes)

---

