---
title: "What is Apparmor..?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-26
What is Apparmor..?What is the use of it..?

---

### Post by bioterror on 2010-10-26
> **getyourkarthick said:**
> What is Apparmor..?What is the use of it..?

[https://apparmor.wiki.kernel.org/index.php/Main_Page]("https://apparmor.wiki.kernel.org/index.php/Main_Page") says:

AppArmor is an effective and easy-to-use Linux application security system. AppArmor proactively protects the operating system and applications from external or internal threats, even zero-day attacks, by enforcing good behavior and preventing even unknown application flaws from being exploited. AppArmor security policies completely define what system resources individual applications can access, and with what privileges. A number of default policies are included with AppArmor, and using a combination of advanced static analysis and learning-based tools, AppArmor policies for even very complex applications can be deployed successfully in a matter of hours.

---

### Post by DooM55 on 2010-10-26
> **getyourkarthick said:**
> What is Apparmor..?What is the use of it..?


i don't know too
:(

---

### Post by endotherm on 2010-10-26
apparmor is a security framework that prevents applications from turning evil. for instance, if I run firefox, and end up on a bad site, the site operator might try to install malware that deletes all my user files. AppArmor places limits on firefox though, preventing it from doing anything I don't want it to do (like accessing files it has no business in, like my documents/pictures/music/etc). that way even if your application is comprimised, it can't hurt anything (or at least not much )

---

### Post by UbuNoob001 on 2010-10-26
bodhi.zazen on here has written a great introduction to Apparmor. He is a great teacher/admin on here. 

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)


also, his other writings on security (securing linux, securing firefox) etc. are not to be beaten. 

good luck!

---

