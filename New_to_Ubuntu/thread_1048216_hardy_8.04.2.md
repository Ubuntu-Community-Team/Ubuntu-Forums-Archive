---
title: "hardy 8.04.2?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by mdewet on 2009-01-23
What is the terminal command for seeing the current version of Hardy that is on my machine?  I want to see if I am using 8.04.2, and I saw the command in another thread, but for the life of me I can't seem to find the post..

---

### Post by Kobalt on 2009-01-23
Just navigate to System > Admin. > System monitor. You can see your Ubuntu version from the system tab.

---

### Post by mdewet on 2009-01-23
thanks, It only shows hardy 8.04..does this mean I dont have 8.04.2 or is the information in the system monitor insufficient?

---

### Post by mdewet on 2009-01-23
I found it
```
muerte@muerte:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

muerte@muerte:~$ 

```

now I'm wondering how I can upgrade to 8.04.2?  The update manager says that my system is up to date, but I'm still on 8.04.1..is it not supposed to be automatic?

---

### Post by Kevbert on 2009-01-23
Try
```
lsb_release -a
```

---

### Post by snowpine on 2009-01-23
As long as you regularly run the update manager, your system will be up to date. No need to worry about whether you are running 8.04.2 or not.

Each version number is basically a "snapshot" of what's on the Live CD at that moment.

---

### Post by gjoellee on 2009-01-23
> **mdewet said:**
> I found it
```
muerte@muerte:~$ cat /etc/issue
Ubuntu 8.04.1 \n \l

muerte@muerte:~$ 

```now I'm wondering how I can upgrade to 8.04.2?  The update manager says that my system is up to date, but I'm still on 8.04.1..is it not supposed to be automatic?

Just update your system like you normally do. Ubuntu is rolling release, which means that you don't have to do a clean install for every release. However to move between larger versions you can use:
```
update-manager -d
```, if it upgrades successfully you should just have updated your system, and not lost any of your files

---

### Post by snowpine on 2009-01-23
> **gjoellee said:**
> However to move between larger versions you can use:
```
update-manager -d
```, if it upgrades successfully you should just have updated your system, and not lost any of your files

Just to be clear, 'update-manager -d' would upgrade the system to 8.10, not 8.04.2, correct?

---

### Post by achase79 on 2009-01-23
you may have to activate the Hardy-Updates repository

---

### Post by Jorge_C on 2009-01-23
If you run the update manager and it says your system is up to date, then it is.

Basically, Ubuntu 8.04.2 is Ubuntu 8.04 (or Ubuntu 8.04.1) but with updates already applied, that is, if you did a clean Ubuntu 8.04 install, you would get a huge amount of updates the first time you ran the update manager. If you did a clean Ubuntu 8.04.1 install, you'd get much less updates to download after install, and if you installed 8.04.2, you'd have just a few things to update.

All in all, don't worry, your system is updated as long as the update manager says so.

---

### Post by Kevbert on 2009-01-24
> **snowpine said:**
> Just to be clear, 'update-manager -d' would upgrade the system to 8.10, not 8.04.2, correct?

Yes, that will allow you to update to 8.10 rather than 8.04.2 even if you only normally update to the latest long term release (LTS) via the Upgrade Manager.
It should be possible to update from 8.04.1 to 8.04.2 via terminal with
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jimmy the saint on 2009-01-24
The 8.04.2 is just a snapshot of the current releases.  It is only relevant if you are doing a fresh install.  It is reflected in the iso that you download and install from, in that when you do the fresh intall you already have a lot of updates installed so you don't have to download/install 100's of updates after you perform the installation.  On a pre-existing installation, you have (hopefully) been installing these updates a little bit at at a time as they become available, so you automatically have the point release.

Easier than you thought, huh!

---

