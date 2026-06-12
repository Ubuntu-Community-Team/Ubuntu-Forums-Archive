---
title: "Installation issues broken packages and gnome game data"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by badfps on 2008-12-14
rohit@ubuntu:~$ sudo apt-get install -f
[sudo] password for rohit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-games-data (1:2.24.1.1-0ubuntu1) ...
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Warning: /usr/share/gconf/schemas/blackjack.schemas could not be found.
Warning: /usr/share/gconf/schemas/glchess.schemas could not be found.
Warning: /usr/share/gconf/schemas/glines.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnect.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnibbles.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnobots2.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnometris.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnomine.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotravex.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotski.schemas could not be found.
Warning: /usr/share/gconf/schemas/gtali.schemas could not be found.
Warning: /usr/share/gconf/schemas/iagno.schemas could not be found.
Warning: /usr/share/gconf/schemas/mahjongg.schemas could not be found.
Warning: /usr/share/gconf/schemas/same-gnome.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-games-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
rohit@ubuntu:~$ sudo dpkg --configure -a
Setting up gnome-games-data (1:2.24.1.1-0ubuntu1) ...
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Warning: /usr/share/gconf/schemas/blackjack.schemas could not be found.
Warning: /usr/share/gconf/schemas/glchess.schemas could not be found.
Warning: /usr/share/gconf/schemas/glines.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnect.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnibbles.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnobots2.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnometris.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnomine.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotravex.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotski.schemas could not be found.
Warning: /usr/share/gconf/schemas/gtali.schemas could not be found.
Warning: /usr/share/gconf/schemas/iagno.schemas could not be found.
Warning: /usr/share/gconf/schemas/mahjongg.schemas could not be found.
Warning: /usr/share/gconf/schemas/same-gnome.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-games-data
rohit@ubuntu:~$

---

### Post by Michael.Godawski on 2008-12-14
Try this
first

```
sudo apt-get clean
sudo apt-get autoclean
```If this does not work 
run this
```
sudo mv /var/lib/dpkg/info/gnome-games-data.prerm $HOME
```By moving the Pre Removal Script you should be able the de-install and reinstall the gnome-games-data.

---

### Post by badfps on 2008-12-14
i tryed to reinstall gnome game data but it says 


i have already a more later version of it:confused:

---

