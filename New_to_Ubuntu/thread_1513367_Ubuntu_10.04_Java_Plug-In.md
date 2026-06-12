---
title: "Ubuntu 10.04 Java Plug-In"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Keener29 on 2010-06-19
Hi all,

I'm attempting to install Java for Google Chrome.
"apt-cache search sun-java" in the terminal shows all my java plugins and jre for Java 6 and they all installed properly. Google Chrome has plugins turned on but websites don't recognize it.

Thank you,
Keenan

---

### Post by ankit singh on 2010-06-19
```
sudo update-java-alternatives -s java-6-sun
```This will replace openjdk with sun java, in other words  sun java will become the default java for ur system.:guitar:

---

### Post by gandaran on 2010-06-19
you have installed the sun-java6-jre, did you also install the sun-java6-plugin?
and if you have openjdk-java installed I recommend to remove it, no need for two javas installed.

---

