---
title: "Installing Pidgin 2.54"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Mr.Glenmore on 2009-01-17
Hi all,
I just got rid of Pidgin 2.43 to install a newer Version.Is there a Way to explain how to do this(step by step)?
Thanks for any help

---

### Post by drs305 on 2009-01-17
Version 2.52 is currently in Synaptic. I would recommend using the ubuntu-tested version in the repositories unless you have a need for a specific feature not available in this version. That applies to just about all linux software.

System, Administration, Synaptic Package Manager. Click inside the right pane, type "pidgin'. Right click, Mark for Installation, Mark, then click on the Apply button in the top menu.

---

### Post by Arabica Bean on 2009-01-17
Or if you're familiar with the terminal

```
sudo apt-get install pidgin
```
then enter in your password

---

### Post by binbash on 2009-01-17
download the debs from [http://www.getdeb.net/](http://www.getdeb.net/)

remove pidgin : 

sudo apt-get remove pidgin

go to the folder you have downloaded the debs : 

sudo dpkg -i *.deb

---

