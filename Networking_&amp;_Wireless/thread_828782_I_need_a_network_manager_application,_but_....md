---
title: "I need a network manager application, but ..."
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Alberto2 on 2008-06-14
Hello,
Due to some misworking I uninstalled **wicd**, the last and only network manager I had in my Kubuntu 8.04 (Debian based).
So, now I cannot connect to the Internet any longer.
My question is: how can I install wicd again (or another network manager, even by command line) if I can't connect to the Web? I have got a Knoppix Live CD. Can I use it in order to solve this problem?
Best Regards

---

### Post by Blackneto on 2008-06-14
you can try to manually config your network using the info here:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

then you will be able to download what you need.

---

### Post by lswb on 2008-06-14
If you used originally used apt-get or synaptic to install wicd, it may still be cached on your system. Have you tried to reinstall it with synaptic? Even though you will get the usual info box about xxx bytes need to be downloaded, it won't actually need to connect to the internet or download anything if the package is cached locally. The default package cache directory is /var/cache/apt/archives. In a terminal try

  ls /var/cache/apt/archives/*wicd*

and see if there are any results, if prints out something like

  /var/cache/apt/archives/wicd_1.4.2-1_all.deb

then you should be good to go with a reinstall from synaptic.

Note that if you selected "Mark for complete removal" option when you uninstalled wicd, IIRC it removes the cache copy also.

---

