---
title: "Totally New To Ubuntu"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Tsujimoto on 2011-05-16
Hey guys, I'm completely fresh to Ubuntu. Got it this morning and I was wondering if there was a guide to all my questions? I am a windows user and this is totally new to me. I have no idea what I'm doing, so please help me. I like how fast Ubuntu is, but I'd like to figure it out. Thanks. :)

---

### Post by howefield on 2011-05-16
Hi and welcome to the forum.

You can download a free booklet from here to start you off..

[http://ubuntupocketguide.com/index_main.html](http://ubuntupocketguide.com/index_main.html)

And of course, post all your questions here.

---

### Post by Tsujimoto on 2011-05-16
Okay, sounds like a plan. Also, I have a specific question. It's about Java, I like to play games using it and I'm wondering, how do I download it? :o I'm using chromium, btw.

---

### Post by howefield on 2011-05-16
You have a choice here to either use the open source version of Java or Suns version which is proprietary.

For the open source version, go to System > Administration > Synaptic Package Manager and press the reload button just to ensure that you have the current package lists.

Then search for openjdk-6-jre and the icedtea6-plugin packages. Click the check box to the left of the package name and select Mark for Installation, if you are asked about accepting dependancies, accept them and then click apply.

For Suns version of Java, you will need to enable the Partner repository, to do this from Synaptic Package Manager, select the Settings menu and choose Repositories, then from the Other Software tab, check mark Canonical Partners, close and press the reload button.

You then want to install sun-java6-jre and sun-java6-plugin (accept any dependancies that you are offered).

Here's a link that might help..

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by aeiah on 2011-05-16
edit: ignore me

---

### Post by clhsharky on 2011-05-16
Tsujimoto


> It's about Java, I like to play games using it and I'm wondering, how do I download it?
Install ( ubuntu-restricted-extras ) in software center.
It installs flash,java,codex.


Sharky

---

### Post by Tsujimoto on 2011-05-16
> **howefield said:**
> You have a choice here to either use the open source version of Java or Suns version which is proprietary.

For the open source version, go to System > Administration > Synaptic Package Manager and press the reload button just to ensure that you have the current package lists.

Then search for openjdk-6-jre and the icedtea6-plugin packages. Click the check box to the left of the package name and select Mark for Installation, if you are asked about accepting dependancies, accept them and then click apply.

For Suns version of Java, you will need to enable the Partner repository, to do this from Synaptic Package Manager, select the Settings menu and choose Repositories, then from the Other Software tab, check mark Canonical Partners, close and press the reload button.

You then want to install sun-java6-jre and sun-java6-plugin (accept any dependancies that you are offered).

Here's a link that might help..

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Thanks, this really helped. I'm completely new, keep in mind. Was a Windows user for years and years, so this is all weird to me. Thankyou!

---

### Post by Tsujimoto on 2011-05-16
> **clhsharky said:**
> Tsujimoto



Install ( ubuntu-restricted-extras ) in software center.
It installs flash,java,codex.


Sharky

Also, this has answered my questions on other things such as flash,codex, etc. Thanks Sharky.

---

