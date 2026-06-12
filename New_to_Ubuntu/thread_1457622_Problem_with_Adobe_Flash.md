---
title: "Problem with Adobe Flash"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Krayzee Studios on 2010-04-18
I "supposedly" installed Adobe Flash today on my ubuntu machine. I tried to load sites like : Youtube,Viddler,Hulu, and many different flash game websites. All inform me to install Adobe Flash Player. Has anyone else had a problem like this? Please help.

Thanks,
Krayzee

---

### Post by Temposs on 2010-04-18
How did you install it?

---

### Post by Krayzee Studios on 2010-04-18
I went to [this link]("http://get.adobe.com/flashplayer/") and downloaded the .deb package.

---

### Post by tom66 on 2010-04-18
Have you restarted your web browser?

---

### Post by Krayzee Studios on 2010-04-18
Yep, Twice.

---

### Post by Temposs on 2010-04-18
Uninstall what you installed by typing into the terminal:

```
sudo apt-get remove adobe-flashplugin
```

Then, install flash from the Ubuntu repository:

```
sudo apt-get install flashplugin-installer
```

---

### Post by Krayzee Studios on 2010-04-18
_**sudo apt-get remove flashplugin-nonfree**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libdns35 libnss3-dev cvs libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


_**sudo apt-get install flashplugin-installer**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-installer has no installation candidate
chris@r00t:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-installer has no installation candidate

---

### Post by Temposs on 2010-04-18
I modified my instructions. Please try again.

---

### Post by Krayzee Studios on 2010-04-18
The first one worked, and the second one says:
_**sudo apt-get install flashplugin-installer**_
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer
chris@r00t:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer

---

### Post by sandyd on 2010-04-18
do
```

sudo dpkg --purge --force-all adobe-flashplugin
```

---

### Post by Temposs on 2010-04-18
Ohhh, you're running Ubuntu 8.04. That would explain why flashplugin-installer doesn't work. So, you do this:

```
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

---

### Post by Krayzee Studios on 2010-04-18
> **Temposs said:**
> Ohhh, you're running Ubuntu 8.04. That would explain why flashplugin-installer doesn't work. So, you do this:

```
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Trying this at the moment. If this does not work, I will try carlee's advice.

[U][B]
EDIT: [/B][/U]**Yes! Finally it worked thank you sooooo much!!!**

---

