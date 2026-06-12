---
title: "Problems with installing compiz"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Djalmahal on 2009-03-10
Hi,

I;m just trying to set up a new laptop of a friend and in order to enable compiz I checked synaptic and it all seemed there. If I type ccsm the output is

The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found

If I type 
pazpazon@jojo:~$ sudo aptitude install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

In preferences compiz config settings manager doesn't show up

What to do???

Thanks 
Andreas

---

### Post by joenieburg on 2009-03-10
install
Compiz configuration settings manager
u can find it in your synaptics
(compizconfig-settings-manager)

---

### Post by Djalmahal on 2009-03-10
I typed in 
pazpazon@jojo:~$ sudo aptitude install compizconfig-settings-manager

The reply to which is


Couldn't find any package whose name or description matched "compizconfig-settings-manager"

Which is rather strange

So, what to do??

THanks
Andreas

---

### Post by Djalmahal on 2009-03-10
Ok, just booted up and it installed it

---

### Post by joenieburg on 2009-03-10
when u are in terminal mode i like to use the TAB button.
just type in
sudo apt-get install compiz and then hit the tab button twice in a row
this is what u can get:
jeroen@ubuntufvzpb2j:~$ sudo apt-get install compiz
compiz                             compiz-fusion-bcop
compiz-bcop                        compiz-fusion-plugins-extra
compiz-compcomm-plugins-main       compiz-fusion-plugins-main
compizconfig-backend-gconf         compiz-fusion-plugins-unsupported
compizconfig-backend-kconfig       compiz-gnome
compizconfig-settings-manager      compiz-gtk
compiz-core                        compiz-kde
compiz-dev                         compiz-plugins
compiz-extra                       compiz-wrapper
jeroen@ubuntufvzpb2j:~$ sudo apt-get install compiz

But I see u have got it already

---

