---
title: "Grub2: Easier way to modify the scripts?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by melrokz on 2011-08-05
I need a GUI for modifying GRUB 2 settings, especially 
- menu timeout
- removing certain menu entries Eg: menuentry {}
- Grub password
- setting the default OS.

How's the easiest way to do this?

[Please note that I have no idea about programming or scripting.]

---

### Post by amjjawad on 2011-08-05
> **melrokz said:**
> I need a GUI for modifying GRUB 2 settings, especially 
- menu timeout
- removing certain menu entries Eg: menuentry {}
- Grub password
- setting the default OS.

How's the easiest way to do this?

[Please note that I have no idea about programming or scripting.]

```
sudo apt-get update

``````
sudo apt-get install startupmanager -y

```Not sure but guess GRUB Customizer might help too but haven't tried it yet.
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by melrokz on 2011-08-05
Ok, the startup manager solves the timeout and default os.
What it doesn't seem to solve is:
- removing certain menu entries Eg: menuentry {}
- Grub password

which are the main things I'd like to do. Editing grub.cfg is an option, but I'll need to edit it after every kernel update. Also I don't want to try it, since the file tells me not to edit it ;)

Also, I do a runtime kernel modification sometimes:
```
sudo sysctl -w kernel.shmmax=128000000
```
that resets grub.cfg! I need to do that to run Avast antivirus.

Now, how may I proceed?

---

### Post by Matt__ on 2011-08-05
try
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update 
sudo apt-get install grub-customizer


```

---

### Post by melrokz on 2011-08-12
Thanks, guys. Everything's fine, except I can't figure out how to set a grub2 menu password to prevent modification of kernel arguments...

---

### Post by melrokz on 2011-08-20
Please help me set a grub password. How come there is so less demand for this feature? Ubuntu is now used in large companies too, right? There should be some easy way to set a grub menu password... please let me know... or how else will I protect my local system from hackers within the company?

---

### Post by georgemc on 2011-08-20
This might help:

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

Good write up.  Check item 4

The grub manual is here:

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Cheers
George

---

