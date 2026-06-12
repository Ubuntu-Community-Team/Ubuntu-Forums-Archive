---
title: "Ndiswrapper Problems"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by dcast on 2007-10-22
Hi, I booted up yesterday and my wireless card was not working, apparently ndiswrapper was broken somehow. I dpkg-reconfigure ndiswrapper and that did not help, I removed it and reinstalled it. When I run "ndiswrapper" in the terminal I am told that it is not a command, how ever "sudo apt-get install ndiswrapper-source" says that ndiswrapper is installed. Any help? thanks, Dcast.

---

### Post by MegaJim on 2007-10-22
I would try

```
$sudo apt-get remove ndisgtk
```

If its not there, first run an 

```
$sudo apt-get autoremove
```

to get rid of any bits of mess, then install it using

```
$sudo apt-get install ndisgtk
```

now if you try to run ndiswrapper and it still can't find it, there's likely a problem with your paths, check the output of 

```
$which ndiswrapper
```

```
$echo $PATH
```

```

$sudo updatedb
$locate ndiswrapper

```

if which returns command not found but locate does return a path for ndiswrapper, then try executing it using an absolute path, e.g.

```
$/usr/sbin/ndiswrapper
```

Hopefully it should now work and you can install your windows driver.

---

### Post by kevdog on 2007-10-22
Kind of do as the previous poster suggested.  When you find the directory ndiswrapper is directed, just make sure that the directory (like /usr/bin) is in your PATH variable.  I believe the PATH variable is set in your .bashrc or .bash_profile or .profile files

---

### Post by dcast on 2007-11-03
Thanks for your replies, I got it working. Dcast

---

