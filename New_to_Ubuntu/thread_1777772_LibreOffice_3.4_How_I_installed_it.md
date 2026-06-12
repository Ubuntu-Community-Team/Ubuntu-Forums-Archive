---
title: "LibreOffice 3.4: How I installed it"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Kakym on 2011-06-08
Set out my notes below which hopefully should help anyone wishing to install 3.4.

First I downloaded and installed Axel, the blurb hooked me and it appeared to work well.

AXEL
=====
Axel is a command line based tool that really accelerates your download speeds on Linux by over 20 times your current download speed (the one which you get while you download using wget or firefox). Now let us see how axel manages to accelerate your downloads and how you can start using it on your system.

sudo apt-get install axel

REMOVE EXISTING LIBREOFFICE
===========================
The first thing you have to do is remove LibreOffice 3.2 or OpenOffice - whichever you have installed in your system. To do that, open the terminal and execute the command given below.

For LibreOffice:

sudo apt-get remove libreoffice*.*

For OpenOffice:

sudo apt-get remove openoffice*.*

DOWNLOAD
==========
Now, download LibreOffice 3.4.

For 32-bit:

axel [http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86/LibO_3.4.0_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86/LibO_3.4.0_Linux_x86_install-deb_en-US.tar.gz)

Also for UK:
axel [http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86/LibO_3.4.0_Linux_x86_helppack-deb_en-GB.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86/LibO_3.4.0_Linux_x86_helppack-deb_en-GB.tar.gz)

axel [http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86/LibO_3.4.0_Linux_x86_langpack-deb_en-GB.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86/LibO_3.4.0_Linux_x86_langpack-deb_en-GB.tar.gz)

For 64-bit:

axel [http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86_64/LibO_3.4.0_Linux_x86-64_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.4.0/deb/x86_64/LibO_3.4.0_Linux_x86-64_install-deb_en-US.tar.gz)

EXTRACT
=========
Using the Terminal extract the package you have downloaded.

For 32-bit:

tar -xvf LibO_3.4.0_Linux_x86_install-deb_en-US.tar.gz
tar -xvf LibO_3.4.0_Linux_x86_langpack-deb_en-GB.tar.gz
tar -xvf LibO_3.4.0_Linux_x86_helppack-deb_en-GB.tar.gz

For 64-bit:

tar -xvf LibO_3.4.0_Linux_x86-64_install-deb_en-US.tar.gz

DEBS INSTALLATION - I installed the 32 bit version
==================
Using the Terminal, navigate into the folder you have extracted and execute the following commands to install LibreOffice 3.4: [Tip I type ls to list the folders and then copy the folder I require and paste with obviosuly cd in front of it to access the required folder]

cd LibO_3.4.0rc2_Linux_x86_install-deb_en-US
cd DEBS
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb

LibreOffice 3.4 should now be installed.

UK Files:
cd LibO_3.4.0rc2_Linux_x86_langpack-deb_en-GB
cd DEBS
sudo dpkg -i *.deb

cd LibO_3.4.0rc2_Linux_x86_helppack-deb_en-GB
cd DEBS
sudo dpkg -i *.deb

Unity does not appear to pick up the installation so you have to create your own launcher. The program files on my system were located: /opt/libreoffice3.4/program and the icon files were located at: /usr/share/icons/hicolor/48x48/apps

Now whether its worth doing all of the above for 3.4 is another matter!

---

### Post by Steeperton on 2011-06-08
Surely this is quicker/easier?
```
 sudo add-apt-repository ppa:libreoffice/ppa
 sudo apt-get update
 sudo apt-get upgrade
```

---

### Post by EgoGratis on 2011-06-08
> **Steeperton said:**
> Surely this is quicker/easier?
```
 sudo add-apt-repository ppa:libreoffice/ppa
 sudo apt-get update
 sudo apt-get upgrade
```

There is no LibreOffice 3.4 in this PPA at this moment. You have to do it manually for now if u want to use it!

---

### Post by frankbooth on 2011-06-08
> **steeperton said:**
> surely this is quicker/easier?
```
 sudo add-apt-repository ppa:libreoffice/ppa
 sudo apt-get update
 sudo apt-get upgrade
```

;)

---

### Post by Kakym on 2011-06-08
Yes I tried the quick way first; but still ended up with 3.3.2. Therefore because I had a few minutes to spare I did it the long way... and discovered axel, which I quite like!

No doubt the ppa will soon have the updated files and I think its far better to have your software managed by the repository because, for example, computer janitor will try and remove your hard work of installing 3.4.

---

### Post by Steeperton on 2011-06-08
> **Kakym said:**
> Yes I tried the quick way first; but still ended up with 3.3.2. Therefore because I had a few minutes to spare I did it the long way... and discovered axel, which I quite like!

No doubt the ppa will soon have the updated files and I think its far better to have your software managed by the repository because, for example, computer janitor will try and remove your hard work of installing 3.4.

Good point! Maybe I should have checked first! :p

---

