---
title: "Network Manager on Ubuntu 5.04?"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by ifrflyer on 2005-04-21
Anyone successfully running Network Manager on ubuntu 5.04? I tried to install today following the instructions on this page:

[http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/) 

But it was borked from the getgo. I've got everything working again after a drama but I would like to try network manager as I hear great things. If you have experience and tips ion installation and running, could you please post them here? 

Thanks in advance

---

### Post by Ozitraveller on 2005-04-22
[QUOTE=ifrflyer]Anyone successfully running Network Manager on ubuntu 5.04? I tried to install today following the instructions on this page:

[http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/) 

But it was borked from the getgo. I've got everything working again after a drama but I would like to try network manager as I hear great things. If you have experience and tips ion installation and running, could you please post them here? 

Thanks in advance[/QUOTE]

WOW that's awesome! 
Top of the weekend TODO list!
Which repository is it in?

EDIT : Sorry I should have read more and not look at the pictures! I found the repository.

 :-)

---

### Post by benplaut on 2005-04-22
[QUOTE=ifrflyer]Anyone successfully running Network Manager on ubuntu 5.04? I tried to install today following the instructions on this page:

[http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/) 

But it was borked from the getgo. I've got everything working again after a drama but I would like to try network manager as I hear great things. If you have experience and tips ion installation and running, could you please post them here? 

Thanks in advance[/QUOTE]

not working for me either  ](*,)

---

### Post by jonny on 2005-04-22
**Warning.  This package might hose your system.**
Installing these packages killed my network access and prevented me from logging in normally through Gnome.  I had to use a command line on tty1 to uninstall network-manager-gnome, libgcrypt7 and network-manager to bring things back to life.

If you're not confident that you could do this yourself, you shouldn't try to install network manager.  It's too dangerous.

---

### Post by benplaut on 2005-04-22
[QUOTE=jonny]**Warning.  This package might hose your system.**
Installing these packages killed my network access and prevented me from logging in normally through Gnome.  I had to use a command line on tty1 to uninstall network-manager-gnome, libgcrypt7 and network-manager to bring things back to life.

If you're not confident that you could do this yourself, you shouldn't try to install network manager.  It's too dangerous.[/QUOTE]

OK, getting rid of it  :???:

---

### Post by notzac on 2005-04-23
It didn't hose my system, but here's the error message that I got when I tried to run it from the command line with 'sudo NetworkManager'

```
** (process:18431): CRITICAL **: file NetworkManagerDevice.c: line 379 (nm_device_unref): assertion `dev != NULL' failed
```

..which is a shame really, because it'd be a really handy tool to have. Oh well, guess that you can't win them all.

---

### Post by eberth on 2005-05-05
HI i just installed network manager and it messed up everything, the login, no wireless connection, etc.. so i want to go back :(, how can i uninstall it????

---

### Post by jonny on 2005-05-06
Open a terminal session (if you can't even login properly, do ctrl-alt-F1 to get a command line) and enter this:```
sudo apt-get remove network-manager-gnome libgcrypt7 network-manager
```All will then be well.

---

### Post by gururise on 2005-05-13
Anyone get this awesome app to work on Hoary?

---

