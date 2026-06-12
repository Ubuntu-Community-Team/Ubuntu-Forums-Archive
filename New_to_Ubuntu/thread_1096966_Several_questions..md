---
title: "Several questions."
date: 2009-03-15
forum: New to Ubuntu
---

### Post by bennis on 2009-03-15
So first off, i screwed up my apache2 install somehow. It had something to do with the torrentflux installing and uninstalling in vain attempts to get it to work. I then found a thread to set apache2 back to it's default settings, and it said to delete the config file. So i did. Now i need a way to remove **all** of the config files, or simply overwrite them. Also, how would one go about making ssh work without having to login first? its terribly obnoxious to have to go to my server every time i restart it and login. An autologin thing would be fine too. Thanks for your help.

---

### Post by KayakJim on 2009-03-15
To completely remove apache and all of it's configuration files 
```

sudo apt-get purge apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 ssl-cert

```
After that has completed, if you need or want to reinstall Apache just change the purge to install and you will be set.

---

### Post by bennis on 2009-03-15
Sweet! Thank you! Trying now, and i'll see if it works.

Edit: So that worked, is there anyway for me to see the torrentflux dependencies? So that i might purge them as well.

---

### Post by KayakJim on 2009-03-15
In general, to completely remove an application (e.g. apache2, torrentflux, etc), use the package name that you specified to install and use it with the purge option like you just did with the Apache2 package.

For example, 
```
sudo apt-get purge torrentflux
```
should completely remove torrentflux. Like before, change the purge to install and that will reinstall torrentflux should you so desire.

You could then run 
```
sudo apt-get autoremove
```
to ensure your cache is clean.

---

