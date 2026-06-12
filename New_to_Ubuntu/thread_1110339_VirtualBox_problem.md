---
title: "VirtualBox problem"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-29
I get the error message 

No suitable module for running kernel found

on boot up.

Applying the following solution

sudo /etc/init.d/vboxdrv setup

gives me....

/etc/init.d/vboxdrv: 342: /usr/share/virtualbox/src/vboxdrv/build_in_tmp: not found

What is the problem here....

---

### Post by noelvh on 2009-03-29
I had this issue after a kernel upgrade on my system. With this upgrade the old module will not work. Now with that said I have the version from Sun installed not the one from the repos. So all I did was uninstall it with sudo apt-get remove virtualbox-2.0, then reinstalled it. The reinstall created the new module I needed. If it from the repos I would try to remove it then reinstall it. 

Now I am sure there is a way to make the new module but I have not found one. It was easy to uninstall, and reinstall it.

Noel

---

### Post by dunbrokin on 2009-03-29
Very strange, I cannot find Virtualbox on my system....It was on there before...

---

