---
title: "Getting Sun JRE for Firefox"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by zer010 on 2010-08-13
I had this working once before, but the simple steps I used aren't working. Right now I have Sun installed as evidenced by: ~$ java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)

When i check "about: plugins" in FF, I see that it is still using IcedTea. How do I change it to use Sun?

---

### Post by Miljet on 2010-08-13
Easiest way is to use Synaptic Package Manager to remove Icedtea plugin.

---

### Post by wojox on 2010-08-13
Did you install Java through the repositories or from their site?

---

### Post by jcolyn on 2010-08-13
First you will need to remove java from your system then do not use package management to download Java6. Use the terminal because you have to agree to the term of agreement.

In the terminal ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by zer010 on 2010-08-14
Ok, I didn't remove Java, I used ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```  to install Sun Java. I will try using Synaptic to remove ALL of Java, then reinstall via terminal...

---

### Post by Norm24 on 2010-08-14
Remove Iced Tea,Open jdk.Sun Java plugin is in the repos.

---

### Post by wojox on 2010-08-14
> **Norm24 said:**
> Remove Iced Tea,Open jdk.Sun Java plugin is in the repos.

After you enable it in Software Sources > Other Software > Partner

---

### Post by philinux on 2010-08-14
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Update Alternatives.

```
sudo update-alternatives --config java
```

---

### Post by zer010 on 2010-08-14
I forgot about "update-alternatives". lol  Either way, I went to Synaptic and removed both Sun and IcedTea, then went into the terminal and installed Sun Java. Now everything's running smooth again! Thanks everyone!

---

