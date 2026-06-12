---
title: "Error installing Ebox"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by rgotten on 2009-02-11
i am installing ebox and i am getting the following error:

sudo apt-get install “^ebox-.*” 
Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package “^ebox-.*”

I follow the instruction on the website that say:

Using the latest version
To install a newer version of eBox than is included in Ubuntu's repositories add to the file /etc/apt/sources.list this line: 


deb [http://ppa.launchpad.net/juruen/ubuntu](http://ppa.launchpad.net/juruen/ubuntu) hardy main Be sure to run 


sudo apt-get updatebefore installing eBox. 

Any help will be appreciated

rgotten

---

### Post by supersonicdarky on 2009-02-13
perhaps you have incorrectly added the repo line to sources.list? didn't **sudo apt-get update** after adding it?

see if this gives you any results
```
apt-cache search ^ebox
```

---

