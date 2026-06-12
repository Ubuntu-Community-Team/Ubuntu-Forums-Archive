---
title: "Enabling Java Web Start"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by RVA Dennis on 2009-02-13
As a forex trader I rely on online trading platforms which are java based. After installing Ubuntu within WindowsXP yesterday against the better judgement of those who answered my prior post questions I updated all package and installed or thought I installed Java and JavaWeb Start from the packages included. 

In trying to log in either from Firefox or using a desktop icon (Java Web Start) nothing happens.

What need I next to get these applications to run?

---

### Post by Xiong Chiamiov on 2009-02-15
First, you can see if you have the proper things installed:
```

whereis javaws

```
If you don't get any output, the java webstart binary isn't installed; I believe it's included in sun-java6-bin.

---

### Post by Bölvaður on 2009-02-15
If it isn't there you can install it with Synapitc (System &#8594; Administrator &#8594; Synaptic Package Manager).

There you have 2 options

1.
install "ubuntu-restricted-extras". Which will also install flash plugin, fonts like new times roman and others you should know and other common things people often uses but isn't installed by default.

2.
installing only java. It has been some time since I did this but I think all you need is: java-common, sun-java6-jre, sun-java6-plugin, sun-java6-bin

I think most of the other dependencies will be installed alongside some of those.

Good luck



Btw with ubuntu 8.10 java is installed by default I think.

---

### Post by RVA Dennis on 2009-02-15
> **Bölvaður said:**
> If it isn't there you can install it with Synapitc (System &#8594; Administrator &#8594; Synaptic Package Manager).

There you have 2 options

1.
install "ubuntu-restricted-extras". Which will also install flash plugin, fonts like new times roman and others you should know and other common things people often uses but isn't installed by default.

2.
installing only java. It has been some time since I did this but I think all you need is: java-common, sun-java6-jre, sun-java6-plugin, sun-java6-bin

I think most of the other dependencies will be installed alongside some of those.

Good luck



Btw with ubuntu 8.10 java is installed by default I think.

Did that as you posted and it works bautifully.

Many thanks

---

### Post by afrodeity on 2010-04-18
i am completely new to java webstart and wondering where the apps are and how to test to see if they run outside the browser...

---

