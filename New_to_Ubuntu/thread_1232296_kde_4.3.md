---
title: "kde 4.3"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-08-05
how do i install kde4.3?i am using kde4.2 at the moment.

---

### Post by mgranet on 2009-08-05
You can enable the backports repository. Not sure if 4.3 final has been pushed yet, though.

EDIT: You'll probably have to use Synaptic. KPackageKit has a bug that prevents some updates from installing, and I think backports is one of those updates.

---

### Post by fooman on 2009-08-05
it has been released:

[http://kde.org/announcements/4.3/index.php](http://kde.org/announcements/4.3/index.php)

to install,  add the repos to your /etc/apt/sources.list file.  open the file with root priviledges for editing by running the following command in a terminal (applications > accessories > terminal).  type or copy/paste:

```
gksudo gedit /etc/apt/sources.list
```when it opens,  add (copy/paste) the following lines to the bottom of the file:

```
## kde 4.3
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu jaunty main
```then save and close the file.  after that run the following to upgrade:

```
sudo apt-get update && sudo apt-get upgrade
```if kde is not installed,  you can install the latest with this command:

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

edit:  btw,  i did get an error about "kubuntu-docs" during the installation.  when it was complete,  i went into synaptic and removed the kubuntu-docs package.  all seemed fine after that.

hope that helps.

---

### Post by stonecoldjha on 2009-08-05
i did exactly as you instructed me,but when i logged into kde,i found it corrupted,the kicker panel was at the bottom as it should be,but when i clicked it the menu showed up from the top,moreover windows do not have window borders,and Kwin doesnt kick in.

---

### Post by mgranet on 2009-08-05
It's not unheard of for a backports repo or a PPA to hose your system. I guess I should have mentioned that risk sooner. My bad. 

It's probably fixable though. Did you try a full restart?

---

