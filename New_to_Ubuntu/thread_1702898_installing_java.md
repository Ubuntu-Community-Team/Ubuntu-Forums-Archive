---
title: "installing java?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by mick_86 on 2011-03-08
any ideas how i can install java to ubuntu so i can use online applications that require it?

---

### Post by danjahner on 2011-03-08
There is a community doc with that info, which includes the browser plug-in installation. 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by stchman on 2011-03-08
> **mick_86 said:**
> any ideas how i can install java to ubuntu so i can use online applications that require it?

Yes, enter the following in a terminal:

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

This works for 32 and 64 bit.

Remember for Lucid and later you need to enable the "Partner" repository.  Java stuff was moved to this repository.

---

### Post by cap10Ibraim on 2011-03-08
note that if you already installed ubuntu restricted extras this will install also the jre required to run the applications

---

### Post by stchman on 2011-03-08
> **cap10Ibraim said:**
> note that if you already installed ubuntu restricted extras this will install also the jre required to run the applications

The restricted extras package installs the openJDK plugin.  Yes, that one works, but the SUN/Oracle one is better.

---

