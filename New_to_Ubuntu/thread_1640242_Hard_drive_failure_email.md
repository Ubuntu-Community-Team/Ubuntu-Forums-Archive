---
title: "Hard drive failure email"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by djyoung4 on 2010-12-07
I came across [this HOWTO]("http://www.overclock.net/linux-unix/381933-warned-if-your-hard-drive-about.html") for getting my computer to email me if I have any harddrive problems though the SMART data application.  the problem is the first command gives me this.
```
djyoung4@Daniels-computer:~$ sudo apt-get install mailx smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mailx is a virtual package provided by:
  mailutils 1:2.1+dfsg1-6
  heirloom-mailx 12.4-2
  bsd-mailx 8.1.2-0.20100314cvs-1
You should explicitly select one to install.

E: Package 'mailx' has no installation candidate

```
I tried installing all three different options and none of them work.  does anyone know of a different way to do this.  Any help is greatly appreciated

---

### Post by cariboo on 2010-12-07
I'm not sure on the install of hierloom-mailx, but it sounds like you haven't set it up properly to send email. I would suggest you install postfix, it's in the repositories, it pops up a setup utility as part of the installation process.

---

### Post by SeijiSensei on 2010-12-07
sudo apt-get install bsd-mailx

---

### Post by djyoung4 on 2010-12-08
> **SeijiSensei said:**
> sudo apt-get install bsd-mailx

perfect.  thank you

---

