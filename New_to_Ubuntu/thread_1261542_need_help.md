---
title: "need help"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2009-09-08
i need help upgrading my pidgin  instant messager could anybody help me

---

### Post by cranecreek on 2009-09-08
Try this.

```
apt-get upgrade
```

I think that upgrades all old packages so use with care

---

### Post by pyrofreak99 on 2009-09-08
i mean to the latest package so i can use webcam and such

---

### Post by cranecreek on 2009-09-08
Then go to [www.pidgin.im](www.pidgin.im) and download the newest version.

---

### Post by pyrofreak99 on 2009-09-08
allright im having problems with this

---

### Post by Excedio on 2009-09-08
Copy and paste these codes into a terminal. Applications > Accessories > Terminal

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
``````
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```After doing this, open Update Manager, check for updates, and then install the newly available Pidgin packages.

---

### Post by tacantara on 2009-09-08
If you run into a problem doing this through Terminal, you can download the packages from [http://www.getdeb.net/release/4743](http://www.getdeb.net/release/4743).  There are 4 .deb files to download, those are:

pidgin (560.8 kB)
libpurple0 (1.7 MB)
libpurple-bin (105.2 kB)
pidgin-data (7.3 MB)

I downloaded the files to my desktop.  Next, I uninstalled the existing Pidgin by marking for removal in Synaptic.  Next, I installed the supporting packages (I believe in this order) - pidgin-data, libpurple0, and libpurple-bin.  Then I installed the pidgin file.  If the sequence here is wrong, start with another support package.  The dependencies have to install in a certain order for the rest of the install to go correctly.  It only took about 5 minutes to download and execute this procedure.

---

