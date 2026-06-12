---
title: "amarok wont install"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by allsys3 on 2008-12-21
when trying to install amarok i get this message.


amarok:
 Depends:
 amarok-xine but it is not going to be installed or
	amarok-engine
  Depends: kdelibs4c2a (>=4:3.5.8-1) but 4:3.5.8-0ubuntu3.4 is to be installed
 Depends: libgpod3-nogtk  but it is not installable or
 	libgpod3  but it is not installable
  Depends: libmp4v2-0 (>=1:1.6dfsg) but 1:1.5.0.1-0.3 is to be installed
 Depends: libmtp7  but it is not installable
  Depends: libruby1.8 (>=1.8.6.111) but 1.8.6.36-1ubuntu3.3 is to be installed

---

### Post by redseventyseven on 2008-12-21
Hello,

Some more information would be useful. Are you trying to install amarok using a package manager (or the command line), or are you trying to install amarok using an installer you downloaded from the net?

---

### Post by allsys3 on 2008-12-21
ive tried rom the terminal as well as the synaptic package manager with the same results.

---

### Post by IamReck on 2008-12-21
You got a can not install error when installing Amarok in the Package manager?

When you select "amarok" a window should pop up, and you have to select "Mark" to mark all the other packages that are needed to install it.

---

### Post by redseventyseven on 2008-12-21
OK, well it looks here from the error messages as though the amarok package is expecting newer versions of the packages upon which it depends than the Ubuntu repository is able to provide.

What version of Ubuntu are you running? Is it possible that you're trying to get amarok from a newer repository than the one that's being maintained for your particular version? Can you try installing an older version of amarok?

---

### Post by allsys3 on 2008-12-21
when I tried installing through Applications/Add/Remove I got this message.

Cannot install 'amarok'

This application conflicts with other installed software. To install 'amarok' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


When I go to synaptic package manager I get the  error message noted 

in my First post.

---

### Post by allsys3 on 2008-12-21
Im pretty sure im runnung gutsy.how do i get an older version o amarok to try?

---

### Post by redseventyseven on 2008-12-22
Looks like you're not the only one: [https://answers.launchpad.net/ubuntu/+source/amarok/+question/38416](https://answers.launchpad.net/ubuntu/+source/amarok/+question/38416)

Have a read through the above link, and see if any of the suggestions made there help.

By the way, how long have you been using Ubuntu? If you've installed the system within the last few weeks then I'm surprised you have gutsy installed as it's already over a year old and it's coming to the "end of its life", i.e. as of April 2009 it will no longer continue to be supported and the repositories will cease to be maintained.

If you've not saved lots of work on your system yet then I would suggest a fresh install of one of the newer releases - Hardy which has long term support lasting to April 2011 or Intrepid which is the latest version.

---

### Post by zirtik on 2009-01-26
Hi,
When you install a fresh system, you should do the following before installing any packages using synaptic. Open a terminal and type:

sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Once these steps complete, try installing Amarok or any other software. I hope this helps.

---

### Post by Firestem4 on 2009-01-26
maybe this will help.

---

### Post by Firestem4 on 2009-01-29
Can you enter this and post the output? (I recently had a similar problem and someone helped me figure it out).

```
apt-cache show amarok
```

---

### Post by abn91c on 2009-01-29
Look at this [http://www.kubuntu.org/news/amarok-2.0.1.1](http://www.kubuntu.org/news/amarok-2.0.1.1)

---

### Post by Firestem4 on 2009-01-29
> **abn91c said:**
> Look at this [http://www.kubuntu.org/news/amarok-2.0.1.1](http://www.kubuntu.org/news/amarok-2.0.1.1)

the problem is he has an unmet dependency thats causing him not being able to install Amarok. Otherwise normal installation should work.

---

### Post by abn91c on 2009-01-29
> **Firestem4 said:**
> the problem is he has an unmet dependency thats causing him not being able to install Amarok. Otherwise normal installation should work.
when 2.0 game trouble I removed it completely using the purge options,  including all amarok related files in Adept then reinstalled 1.4 then used the kubuntu guide

---

### Post by Firestem4 on 2009-01-29
Anytime i have an issue, most cases purge doesnt help me. I'm trying to resolve a wierd kopete issue and purge didnt help. so *shrug*

---

