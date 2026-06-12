---
title: "Update problem in Jaunty"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by halovivek on 2009-04-28
HI
I have updated jaunty last week. From the release of testing i am using jaunty for more than 6 months. Last week i have updated the jaunty after 3 weeks from internet. I do have one doubt. after update i selected the nearest server for me is India in package manager. It told me that 54 updates to be installed and it asked me to do partial upgrade. I clicked ok. But nothing happened. I don't know what is the problem in update. or it is doing just like that. Packages are there to be downloaded and to be installed. but nothing happened and the window closes as it is. How to solve this problem?

---

### Post by kansasnoob on 2009-04-28
> **halovivek said:**
> HI
I have updated jaunty last week. From the release of testing i am using jaunty for more than 6 months. Last week i have updated the jaunty after 3 weeks from internet. I do have one doubt. after update i selected the nearest server for me is India in package manager. It told me that 54 updates to be installed and it asked me to do partial upgrade. I clicked ok. But nothing happened. I don't know what is the problem in update. or it is doing just like that. Packages are there to be downloaded and to be installed. but nothing happened and the window closes as it is. How to solve this problem?

I've personally had nothing but trouble with partial upgrades.

But let's back up a bit.

Would you please post the output from terminal of:

```
cat /etc/issue
```

---

### Post by talsemgeest on 2009-04-28
> **halovivek said:**
> HI
I have updated jaunty last week. From the release of testing i am using jaunty for more than 6 months. Last week i have updated the jaunty after 3 weeks from internet. I do have one doubt. after update i selected the nearest server for me is India in package manager. It told me that 54 updates to be installed and it asked me to do partial upgrade. I clicked ok. But nothing happened. I don't know what is the problem in update. or it is doing just like that. Packages are there to be downloaded and to be installed. but nothing happened and the window closes as it is. How to solve this problem?
I had the same problem, but a ```
sudo apt-get update
``` ```
sudo apt-get upgrade
``` ```
sudo apt-get dist-upgrade
``` fixed everything up nicely.

---

### Post by halovivek on 2009-04-29
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade


it went fine again. As you said it may have some broken packages.
Thanks for you all.

---

### Post by talsemgeest on 2009-04-29
Glad to have helped. :)

---

