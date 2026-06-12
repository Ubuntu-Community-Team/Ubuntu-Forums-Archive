---
title: "back up"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by pramodmmuraly on 2009-02-27
i m working on ibex.i want to back up all the applications currently i ve installed now on the system on a cd or something.is there any option.so ican retrieve all the downloaded application from cd if i m re installing the system.i can't access internet frequently thats y.somebody plz help me on this issue

---

### Post by pedro_orange on 2009-02-27
You can use the -d flag on apt-get to just download and not install.

```
sudo apt-get install -d package-name
```

Or you can check the /var/cache/apt/archives folder to see if they're still there. 

Or you can re-download them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by binbash on 2009-02-27
search for : remastersys at forums

---

### Post by ushills on 2009-02-27
Consider aptoncd, [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/).

You can install through synaptic.

It copies all your installed apps that are not part of the install cd to a cd.

---

### Post by Michael.Godawski on 2009-02-27
hi,

yes have a look at remaster sys:


[LIST]
[*][http://ubunturesources.ub.ohost.de/remastersys.html](http://ubunturesources.ub.ohost.de/remastersys.html)
[/LIST]

---

