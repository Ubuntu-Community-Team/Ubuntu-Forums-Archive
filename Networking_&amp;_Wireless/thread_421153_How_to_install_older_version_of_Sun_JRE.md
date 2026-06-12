---
title: "How to install older version of Sun JRE?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by almightybunghole on 2007-04-24
Hi all,

I need to install Sun JRE version 1.4.1 - is there an easy way to do this, if so, how do I do it???

Thanks!

George

---

### Post by spd106 on 2007-04-25
It should be easy enough, go here [http://java.sun.com/products/archive/](http://java.sun.com/products/archive/), choose the version you want and download the .bin. After that chmod +x to make it executable and then run it to install.

---

### Post by almightybunghole on 2007-04-25
> **spd106 said:**
> It should be easy enough, go here [http://java.sun.com/products/archive/](http://java.sun.com/products/archive/), choose the version you want and download the .bin. After that chmod +x to make it executable and then run it to install.
Hi spd106, yes that was what I thought, and what I tried in fact. What happened is that the installer extracted a load of directories and all seemed well; however Firefox still prompts me to install a JVM so I guess it's not aware that one has been installed. Do I need to set a JVM environment variable somewhere to tell it to use the JVM I just installed?
TIA.

George

---

### Post by spd106 on 2007-04-25
I think this page will answer question [http://plugindoc.mozdev.org/faqs/java.html](http://plugindoc.mozdev.org/faqs/java.html)

I am not very familiar with this area so I don't know of any workarounds, sorry.

---

### Post by dksau on 2007-04-25
after a lot of trouble trying to install java on 6.06 I desided to try 7.04 since I understood java was now included with that version.  I think I had to wait for an update but after that here is how java wa sucsessfully installed.  Enable all possible repositories. then go to add and remove sofware under applications in that list find and select both java applets and then just follow on screen instructions.  Good Luck

---

### Post by almightybunghole on 2007-04-26
> **dksau said:**
> after a lot of trouble trying to install java on 6.06 I desided to try 7.04 since I understood java was now included with that version.  I think I had to wait for an update but after that here is how java wa sucsessfully installed.  Enable all possible repositories. then go to add and remove sofware under applications in that list find and select both java applets and then just follow on screen instructions.  Good Luck

Problem is that I need a specific version of the JVM, the new version isn't compatible with the application I need it to run. The latest version I can run is 1.4.1 or maybe an early 1.4.2.

---

