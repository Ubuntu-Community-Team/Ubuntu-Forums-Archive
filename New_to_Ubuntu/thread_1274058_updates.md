---
title: "updates"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by bindu arya on 2009-09-24
whenever i try to install updates it shows error like this.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Please help me as possible as soon..

---

### Post by wojox on 2009-09-24
Open the terminal and paste:

```
dpkg --configure -a
```

---

### Post by dje on 2009-09-24
> **wojox said:**
> Open the terminal and paste:

```
dpkg --configure -a
```

It would need to be:
```
sudo dpkg --configure -a
```
as it requires root permissions ;)

dje

---

### Post by bindu arya on 2009-09-24
> **dje said:**
> It would need to be:
```
sudo dpkg --configure -a
```as it requires root permissions ;)

dje

Thanx a lot :)

---

### Post by muteXe on 2009-09-24
Just out of interest, *why* is it telling you to type this? What has actually gone wrong with dpkg?

---

### Post by nothingspecial on 2009-09-24
From man dpkg >  dpkg --configure package ... | -a | --pending
	      Reconfigure an unpacked package.	If -a or  --pending  is  given
	      instead  of  package, all unpacked but unconfigured packages are
	      configured.

	      Configuring consists of the following steps:

	      1. Unpack the configuration files, and at the same time back  up
	      the  old	configuration  files,  so that they can be restored if
	      something goes wrong.


---

### Post by muteXe on 2009-09-24
Thank you.  No linux boxes at my work to look at the man pages :(

Edit: Ooooh but i have just found this: [http://linuxmanpages.com/](http://linuxmanpages.com/)

---

### Post by nothingspecial on 2009-09-24
Just type man whatever into google. They are all on the internet.

edit: ooohh but I`ve just seen your edit.

---

