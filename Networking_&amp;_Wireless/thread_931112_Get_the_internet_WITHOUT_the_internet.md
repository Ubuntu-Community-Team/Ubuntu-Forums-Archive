---
title: "Get the internet WITHOUT the internet"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by firecracker37 on 2008-09-26
Howdy, trying to set up my wireless card.  I am trying to get my Atheros AR5007EG wireless card working.  I have seen several suggestions about downloading stuff to get it to work.  All the downloads are written out as Linux commands, with no way to download it from windows and transfer it over the the linux side (at least it doesn't sound so easy to someone as clueless as me).

The issue is, I can't plug into a wired router, my building provides me with a free wireless connection, and therefore, there is no where to plug into.  I am dual booting Linux and Windows Vista, my linux box can read the information in my windows partition, so if I can download the files I need, and then boot up linux and install the stuff, that would probably work.  Thank you guys for any help you can provide.

---

### Post by Hyper Tails on 2008-09-26
install ndiswrapper first

```
sudo apt-get install ndisgtk
```

if you use 64 bit go here

[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

if 32 bit go here

[http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

then exact it and open it in ndis wrapper by it's inf file

like this topic

[http://ubuntuforums.org/showthread.php?t=815467](http://ubuntuforums.org/showthread.php?t=815467)

hope this help ;)

---

### Post by doug-M on 2008-09-27
I'm assuming that you are hoping to add packages such as:
sudo apt-get install ubuntu-restricted-extras

Here are some links that might help. You might try first adding your install CD as the repository and see if you can install from there

Ubuntu - installing packages from cd
[http://lists.evolt.org/archive/Week-of-Mon-20080303/193780.html](http://lists.evolt.org/archive/Week-of-Mon-20080303/193780.html)

Install Applications in Ubuntu without Internet 
[http://planetoss.com/detail.php?id=13](http://planetoss.com/detail.php?id=13)

Ubuntu without Internet Connection or Full package CD/DVDs
[http://roshan18.wordpress.com/2007/05/30/ubuntu-without-internet-connection-or-full-package-cddvds/](http://roshan18.wordpress.com/2007/05/30/ubuntu-without-internet-connection-or-full-package-cddvds/)

Update or Install Applications on Debian/Ubuntu Without an Internet Connection
[http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)

Get Ubuntu Repositories on DVD
[http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html](http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html)

---

### Post by firecracker37 on 2008-09-27
Alright, the ndiswrapper was going to be a gigantic hastle to install without an internet connection, so I called around and found a buddy with a traditional router to get the connection.  After I installed the ndiswrapper, my wireless card came to life and I'm posting this cable free :)

Thanks for the help, and now that I can surf the net in Ubuntu, I'm excited to start learning more about it.

---

