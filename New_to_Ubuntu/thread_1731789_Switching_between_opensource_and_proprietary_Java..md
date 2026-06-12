---
title: "Switching between opensource and proprietary Java."
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Son Of Nova on 2011-04-17
Hey there! I've just recently become a member of the linux community (ubuntu 10.10) to reap the benefits that open source presents. In other words I'm a noob. My current issue is that the icedtea plug-in that I have running in chrome (and four other browsers) crashes often. So to remedy this I'd managed to install sun java from another web source in the hopes that this might perform better.

Problem is chrome is still using icedtea for java applications.

How can I get chrome to use sun java instead?

Do I have to uninstall icedtea? (then re-install sun java?)

Many thanks to all who take the time to help me with my hapless noobage!

---

### Post by duanedesign on 2011-04-18
Open a Terminal and run the command:

```
sudo apt-get purge openjdk-6-jre openjdk-6-jre-headles
```

---

### Post by kostkon on 2011-04-18
Give the following command, then restart your browsers
```
sudo update-java-alternatives -s java-6-sun
```
More info [here]("http://help.ubuntu.com/community/Java").

---

