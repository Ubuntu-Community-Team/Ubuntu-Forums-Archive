---
title: "ubuntu restricted extras and skipping flash"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by methodmarvel on 2008-12-05
I'm trying to work out if there is a way to install ubuntu-restricted-extras without flashplugin-nonfree. 

eg: (not real code)
sudo apt-get install ubuntu-restricted-extras MINUSflashplugin-nonfree

is it something like that maybe?

---

### Post by WinterMadness on 2008-12-05
i assume you would have to install everything individually

---

### Post by conscious on 2008-12-05
Method 1.
a. Install ubuntu-restricted-extras. It will pull a number of packages, including flashplugin-nonfree.
b. Remove flashplugin-nonfree. Ubuntu-restricted-extras will have to be removed, but other packages will still be installed.

Method 2.
a. Look up the list of packages at [http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)
b. Install only the ones you need.

---

### Post by jenkinbr on 2008-12-05
In synaptic, search for and mark the package ubuntu-restricted-extras and conferm the extra markings.  Now search for flashplugin-nonfree and uncheck that.  This should also unmark ubuntu-restricted-extras.

---

### Post by NewJack on 2008-12-05
You could probably just uninstall flashplugin-nonfree through synaptic after installing the restricted extras.  I don't think it would mess up the rest of the stuff installed with the extras.

---

