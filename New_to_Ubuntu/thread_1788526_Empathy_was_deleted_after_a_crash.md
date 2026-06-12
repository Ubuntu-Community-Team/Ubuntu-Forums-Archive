---
title: "Empathy was deleted after a crash"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by knokkels on 2011-06-22
Hello, 
I am on Ubuntu 11.04.
Just now I was chatting on Empathy, when it disconnected. 
I tried starting it up again, but failed as it wasn't installed on my system. However, after a successful logoff attempt, the system apparently recovered from a crash as described in this bug report: [https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/697095?comments=all](https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/697095?comments=all) 
This is my situational sketch: [https://bugs.launchpad.net/policykit-1-gnome/+bug/697095/comments/139](https://bugs.launchpad.net/policykit-1-gnome/+bug/697095/comments/139)


knokkels@knokkels:~$ sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 empathy : Depends: libcamel-1.2-23 (>= 3.0) but it is not installable
           Depends: libcamel-1.2-23 (< 3.1) but it is not installable
           Depends: libebook1.2-10 (>= 3.0.2.1) but 2.32.2-0ubuntu2 is to be installed
           Depends: libedataserver1.2-14 (>= 3.0.2.1) but 2.32.2-0ubuntu2 is to be installed
           Depends: libgck0 (>= 2.91.1) but it is not installable
           Depends: libgcr-3-0 (>= 2.91.4) but it is not installable
           Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not installable
           Recommends: nautilus-sendto-empathy but it is not going to be installed
           Recommends: telepathy-indicator but it is not installable
E: Broken packages


After this I tried fixing the broken packages:
* Via Synaptic Package Manager: Failed
* Using:
sudo apt-get update
to update your package list.

sudo apt-get autoclean
to clean up any partial packages.

sudo apt-get clean
to clean up the apt cache.

sudo apt-get autoremove
will clean up any unneeded dependencies.
If while doing this you can identify the broken package this code will very forcefully remove it.


I did not use the latter, as I am not sure which package name is applicable.
sudo dpkg --remove -force --force-remove-reinstreq package name

Any assistance would be greatly appreciated

Greetz

Knokkels

---

### Post by jtarin on 2011-06-22
What version of Ubuntu? Have you done a recent upgrade?
Try removing Empathy through Synaptic and choose "complete removal". Look in your /home/user folder for any folders connected with empathy.....might be a hidden file ".empathy".....I would recommend you rename it as a backup and then reinstall empathy.

---

### Post by wildmanne39 on 2011-06-22
Hi, You should run a disk check by opening disk utility and make sure you do not have any hard drive errors, and proceed from there, I was helping someone with this same problem and after 3 days we could not get it fixed because the person had lost data in a corrupted file.

---

### Post by knokkels on 2011-06-23
> **jtarin said:**
> What version of Ubuntu? Have you done a recent upgrade?
Try removing Empathy through Synaptic and choose "complete removal". Look in your /home/user folder for any folders connected with empathy.....might be a hidden file ".empathy".....I would recommend you rename it as a backup and then reinstall empathy.
Ahh, edited my startpost. Ubuntu 11.04
Also yesterday i did a synaptic complete removal of empathy. I did forget to delete/rename .empathy though. 
Will do that as well.

---

### Post by knokkels on 2011-06-23
> **wildmanne39 said:**
> Hi, You should run a disk check by opening disk utility and make sure you do not have any hard drive errors, and proceed from there, I was helping someone with this same problem and after 3 days we could not get it fixed because the person had lost data in a corrupted file.
[s]Doing that right now, so far so good.[/s]

There is nothing wrong with my disk/filesystem

---

### Post by sathgarcia on 2011-07-01
found this --> [http://askubuntu.com/questions/40459/how-to-install-empathy-3-x](http://askubuntu.com/questions/40459/how-to-install-empathy-3-x) but it didnt really worked with mine.

so here is what i did...

sudo add-apt-repository ppa:telepathy/ppa

sudo apt-get install gnome-common gettext libglib2.0-dev gtk-doc-tools libxml2-dev libtelepathy-glib-dev libmissioncontrol-client-dev libtelepathy-farsight-dev libx11-dev libgtk2.0-dev libcanberra-gtk-dev libgstreamer-plugins-base0.10-dev libebook1.2-dev libnotify-dev libunique-dev libgnome-keyring-dev

if it will return "E: Unable to locate package libmissioncontrol-client-dev", remove the package and continue with the rest.


locate for this files... download and install
=============================================
libtelepathy2_0.3.3-1_i386.deb
libmissioncontrol-client0_4.60-1_i386.deb
libtelepathy-dev_0.3.3-1_i386.deb
libmissioncontrol-client-dev_4.60-1_i386.deb

sudo apt-get -f install


in my home pc, below where required... but in my office pc, it was not except the one listed last
=======================================================
libedataserver1.2-14_3.0.2.1-0ubuntu1_i386.deb
libcamel-1.2-23_3.0.0-1_i386.deb
libebook1.2-10_3.0.2.1-0ubuntu1_i386.deb
libgcr-3-0_3.0.3-2_i386.deb
libgck0_3.0.3-2_i386.deb
libgnome-control-center1_3.0.1.1-1_i386.deb

finally...
sudo apt-get install empathy


hope this will help you, as this helps me... i got ubuntu 11.04 ... happy googling :D

---

### Post by CaptainMark on 2011-07-01
have you added the empathy/telepathy ppa, i did and had exactly this same problem, 
i removed the empathy ppa
uninstalled:
empathy-common
nautilus-sendto-empathy
empathy

and then reinstalled them throught synaptic in the above order, if you havent used the ppa then it may not work for you

---

### Post by knokkels on 2011-07-01
> **sathgarcia said:**
> found this --> [http://askubuntu.com/questions/40459/how-to-install-empathy-3-x](http://askubuntu.com/questions/40459/how-to-install-empathy-3-x) but it didnt really worked with mine.

so here is what i did...

sudo add-apt-repository ppa:telepathy/ppa

sudo apt-get install gnome-common gettext libglib2.0-dev gtk-doc-tools libxml2-dev libtelepathy-glib-dev libmissioncontrol-client-dev libtelepathy-farsight-dev libx11-dev libgtk2.0-dev libcanberra-gtk-dev libgstreamer-plugins-base0.10-dev libebook1.2-dev libnotify-dev libunique-dev libgnome-keyring-dev

if it will return "E: Unable to locate package libmissioncontrol-client-dev", remove the package and continue with the rest.


locate for this files... download and install
=============================================
libtelepathy2_0.3.3-1_i386.deb
libmissioncontrol-client0_4.60-1_i386.deb
libtelepathy-dev_0.3.3-1_i386.deb
libmissioncontrol-client-dev_4.60-1_i386.deb

sudo apt-get -f install


in my home pc, below where required... but in my office pc, it was not except the one listed last
=======================================================
libedataserver1.2-14_3.0.2.1-0ubuntu1_i386.deb
libcamel-1.2-23_3.0.0-1_i386.deb
libebook1.2-10_3.0.2.1-0ubuntu1_i386.deb
libgcr-3-0_3.0.3-2_i386.deb
libgck0_3.0.3-2_i386.deb
libgnome-control-center1_3.0.1.1-1_i386.deb

finally...
sudo apt-get install empathy


hope this will help you, as this helps me... i got ubuntu 11.04 ... happy googling :D
Thanks, this helped. I was well on my way getting on top of this problem, mostly by deleting offending lines in sources.list, which helped. Then it installed again, but locked up frequently. I have good hopes with your additional packages that won't happen again.

---

