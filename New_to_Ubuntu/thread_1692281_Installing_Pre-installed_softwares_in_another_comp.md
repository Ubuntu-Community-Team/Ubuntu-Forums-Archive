---
title: "Installing Pre-installed softwares in another computer"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-02-21
I have some useful softwares installed in my computer. My friend does not have internet connection. Is there a way to install those softwares in his computer in Ubuntu 10.04?

---

### Post by Ghost_Mazal on 2011-02-21
A program called aptoncd (not sure of the spelling) can help with that. You create an burnable iso on the pc that has the apps installed on and can then restore (install) it on the pc that doesn't have the apps.

You must be running the same version of Ubuntu though. Both must be on 32bit or 64bit.

---

### Post by RobikShrestha on 2011-02-21
Thanks for the reply. I will try it.

---

### Post by RobikShrestha on 2011-02-22
Suppose I have installed single software through internet ie software manager. Can I transfer that single software to another computer without iso?

---

### Post by bodhi.zazen on 2011-02-22
> **RobikShrestha said:**
> Suppose I have installed single software through internet ie software manager. Can I transfer that single software to another computer without iso?

aptoncd is probably your best option.

You can install the .deb , but you will also need to install any dependencies as well.

---

### Post by RobikShrestha on 2011-02-22
Suppose I have installed single software through internet ie software manager in my ubuntu 10.04. Can I transfer that single software to another computer with ubuntu 10.04 without using iso file?

---

### Post by gandaran on 2011-02-22
> **RobikShrestha said:**
> Suppose I have installed single software through internet ie software manager. Can I transfer that single software to another computer without iso?

yes, you can copy all the downloaded single or multiple packages in /var/cache/apt/archives to a flash/pen drive then put them in the same place on the second computer
install them just like you installed in the first computer.
there no need to do this for a single application, you just double click the .deb package to install.

---

### Post by RobikShrestha on 2011-02-22
Thanks, the comments were really helpful!

---

### Post by cariboo on 2011-02-22
I'm not sure exactly what you're getting at, but all downloaded packages are stored in /var/cache/apt/archives, you can copy them from there to some sort of removable storage media, then copy them to  a second computer.

---

### Post by komputes on 2011-02-22
What you want to install is a .deb file and not a iso file. If that computer is offline, it may run into problems if it needs to download dependencies. Projects such as aptoncd and other projects try to tackle. There is no way I know which is simple like a windows executable or an apple dmg file.

Other projects:
[http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/](http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/)
[http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html](http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html)
[http://launchpad.net/pd]("https://edge.launchpad.net/pd")
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by cariboo on 2011-02-22
Please don't create multiple threads on the same subject. I have merged your two threads.

---

