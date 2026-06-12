---
title: "how do you update openoffice.org?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by libihero on 2009-03-06
i have the openoffice.org 2.0, and the 3.0 came out... how do i update it?

---

### Post by borneux on 2009-03-06
either uninstalling openoffice.org 2 and installing openoffice.org 3 or add your repository.

if you don't have a fast internet connection, the best way is to uninstall openoffice.org 2 first.
you can do that by 
 sudo apt-get remove openoffice*.*

then download openoffice.org 3 and extract it into a folder and from gnome-terminal in the DEBS folder type : 
 sudo dpkg -i *.deb

i tried this one and so far it works. for more detailed information you can actually do a quick google :

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

[http://monespaceperso.org/blog-en/2009/02/19/installing-openofficeorg-3-on-ubuntu-810/](http://monespaceperso.org/blog-en/2009/02/19/installing-openofficeorg-3-on-ubuntu-810/)

---

### Post by howefield on 2009-03-06
Easy step by step....

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by nachos99 on 2009-03-06
i just did this a few hours ago to update my openoffice. 

basically the same thing described by howefield's post.

all i did was add the following software sources in synaptic pkg manager 

since i use 8.04 - 
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

if using 8.10 change it to /ubuntu intrepid main at the ends

hit refresh, let it update, then close.

after a little while the update manager asked to install office updates.

did not have to uninstall the older openoffice and the new one seems to be working well so far.

according to calc ([http://ubuntuforums.org/showthread.php?t=1011681&highlight=upgrade+openoffice](http://ubuntuforums.org/showthread.php?t=1011681&highlight=upgrade+openoffice)), the uninstall is needed for installing "the official openoffice.org debs from their website. It shouldn't be needed for the ppa debs.... The official openoffice.org website debs will not cleanly upgrade from Ubuntu and when you upgrade to a new version of Ubuntu it also will not cleanly upgrade until you remove those debs. This means you have to remove all the Ubuntu openoffice.org packages before installing the official debs and then before you upgrade Ubuntu you need to remove the official debs first. The official debs also do not include any of the integration and extra bug fixes that are in the Ubuntu version. The Ubuntu version has many extra bugfixes and features since it uses Go-OO (ooo-build)."

---

