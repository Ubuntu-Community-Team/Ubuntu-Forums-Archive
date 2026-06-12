---
title: "Uninstalling avast4workstation-1.3.0?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by st4 on 2009-04-15
For some reason it wasn't working so I decided to install clamav instead. But I can't find avast in either the add/remove programs or the Synaptic Package Manager.

---

### Post by zvacet on 2009-04-15
Did you install it with **deb** file or **tar.gz**? If you install it from tar gz how you did it?

---

### Post by Twitch6000 on 2009-04-15
open the terminal and type sudo apt-get remove nameofprogram

That will remove it.

---

### Post by st4 on 2009-04-15
> **Twitch6000 said:**
> open the terminal and type sudo apt-get remove nameofprogram

That will remove it.I always get this message,

bill@bill-desktop:~$ sudo apt-get remove avast4workstation1.3.0
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avast4workstation1.3.0
bill@bill-desktop:~$

---

### Post by st4 on 2009-04-15
> **zvacet said:**
> Did you install it with **deb** file or **tar.gz**? If you install it from tar gz how you did it?I did it with tar gz, from [this page.]("http://www.avast.com/eng/download-avast-for-linux-edition.html")

---

### Post by zvacet on 2009-04-16
Did you read **install file**?That is a place where is described how to install and uninstall Avast.In short if you install it as described then uninstall 

```
 ./lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh uninstall
```

---

