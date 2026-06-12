---
title: "java install on 8.04 LTS desktop"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by bitdoger on 2009-07-27
i need clear and simple instructions for installing the latest
and greatest JAVA onto my 8.04 LTS desktop ubuntu...so that
my stock brokerage software can run...thanx david rose

---

### Post by credobyte on 2009-07-27
Terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by Clorow on 2009-07-27
Here you go: [install]("apt:sun-java6-jre,sun-java6-bin")

---

### Post by bitdoger on 2009-07-27
after i do this apt-get install is there anything i need to do
so that the brokerage software written in i think JAVA AWT?
recognizes it?...thanx dave

---

### Post by Arup on 2009-07-27
[http://www.64bitjungle.com/ubuntu/finally-sun-release-64-bit-browser-plugin-support-for-jre-almost/](http://www.64bitjungle.com/ubuntu/finally-sun-release-64-bit-browser-plugin-support-for-jre-almost/)

Download latest from Sun site and install following the instructions listed on the link above. The one from repos is quite old.

---

### Post by kostkon on 2009-07-27
> **Arup said:**
> Download latest from Sun site and install following the instructions listed on the link above. The one from repos is quite old.
No, its not; it's the latest version, as [you can see]("http://packages.ubuntu.com/hardy-updates/sun-java6-jre").

---

### Post by kostkon on 2009-07-27
Then you need to open a terminal and give:
```
sudo update-java-alternatives -s java-6-sun
```
to set the Sun Java as the default JVM in your system.

---

### Post by Arup on 2009-07-27
> **kostkon said:**
> No, its not; it's the latest version, as [you can see]("http://packages.ubuntu.com/hardy-updates/sun-java6-jre").

Thanks, it seems they have updated it for both Jaunty and Hardy.

---

