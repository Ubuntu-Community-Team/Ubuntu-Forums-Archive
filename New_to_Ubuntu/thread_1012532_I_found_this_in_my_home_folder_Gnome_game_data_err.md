---
title: "I found this in my home folder Gnome game data errors"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by badfps on 2008-12-15
#!/bin/sh
set -e
# Automatically added by dh_gconf
if [ "$1" = remove ] || [ "$1" = upgrade ]; then
	gconf-schemas --unregister aisleriot.schemas blackjack.schemas glchess.schemas glines.schemas gnect.schemas gnibbles.schemas gnobots2.schemas gnometris.schemas gnomine.schemas gnotravex.schemas gnotski.schemas gtali.schemas iagno.schemas mahjongg.schemas same-gnome.schemas 
fi
# End automatically added section
# Automatically added by dh_pysupport
if which update-python-modules >/dev/null 2>&1; then
	update-python-modules -c  gnome-games-data
fi
# End automatically added section


More Gnome game data errors while trying to install things:
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





Help in noob terms i am new to ubuntu =(
thank you

---

### Post by Shhnap on 2008-12-15
Maybe I don't have an experienced eye...that shell script looks ok to me. Is it causing problems? What is going wrong here?

---

### Post by badfps on 2008-12-15
well when ever i try to download new things it always says Gnome game data error thing and some times my theme i have is gone and after 5 seconds it it logs out by it's self and I log in to find my theme working fine. I have to do this every time i log on ubuntu.
:sad:	:sad::confused::confused:

---

### Post by Shhnap on 2008-12-15
Ok, I don't know how to help with this problem but I would reccomend putting the output the following commands here:

lsb_release -rd
uname -a
apt-cache policy gnome-games-data

To do this just open a terminal (Applications -> Accessories -> Terminal) and type those commands in as you see them.

---

### Post by ellgor on 2008-12-16
Hi,

It looks like gnome-games hasn't completely been loaded, open a terminal and type in the following:

sudo apt-get -f install

when you press enter a load of code will whiz by until the issue has been resolved, this should cure your problem, hope this of help.

Regards, Ellgor.

---

### Post by Michael.Godawski on 2008-12-16
Try this
first

 	

 	```
sudo apt-get clean
sudo apt-get autoclean
``` 
If this does not work 
run this
 	

 	```
sudo mv /var/lib/dpkg/info/gnome-games-data.prerm /home
``` 
By moving the Pre Removal Script you should be able the de-install and reinstall the gnome-games-data.

---

