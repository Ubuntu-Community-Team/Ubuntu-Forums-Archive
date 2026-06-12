---
title: "Ubuntu 8.04 LTS get logged out minimizing Firefox 3.0.11"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2009-07-03
Hi all, 

I'm having a serious issue in my system. Event I reported in launchpad.net as bug. But nobody is replying. First of all let me tell all , I'm very new to linux. But I love Linux. Problem facing is this. Please help me for this.

I'm using
Description:	Ubuntu 8.04.2
Release:	8.04
Kernal version : 2.6.24-24-generic,
Firefox :3.0.11 Steps to Reproducing the Bug
 1. Open the firefox with more tabs
2. Switch between different tabs. around 10 to 20 times by clicking using mouse.
3.  Minimize the firefox after doing the step 2.
4. Try to maximize the firefox.
5. System will log out.
 If  any more information required please ping me back. This bug is very much disappointing me using Ubuntu.


[https://bugs.launchpad.net/ubuntu/+bug/392786](https://bugs.launchpad.net/ubuntu/+bug/392786)


 Regards,
Vipin Balakrishnan.

---

### Post by sadaruwan12 on 2009-07-03
Well I'm using the same LTS as you are for some time but I never has this kind of problem (In IE8 I did). Did you tried removing Firefox and reinstalling it.

---

### Post by vipin.balakrishnan on 2009-07-03
Hi,

Thank you for replying. I didn't try to remove firfox. But I Install Opera. It is working fine in Opera. But when i tried to google it with this issue i found some links which has same issue.
[http://ubuntuforums.org/showthread.php?t=483966](http://ubuntuforums.org/showthread.php?t=483966)

Best Regards,
Vipin Balakrishnan

---

### Post by sadaruwan12 on 2009-07-03
There are issues like this 'cos Linux is learning and learning is Linux. But geting back to your problem opera is OK but try this open the terminal and type

```
sudo apt-get purge firefox
```

now after finishing this restart Ubuntu and install it again. After that see if the same problem comes.

---

