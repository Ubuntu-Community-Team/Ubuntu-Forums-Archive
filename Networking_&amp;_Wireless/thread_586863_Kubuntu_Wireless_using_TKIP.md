---
title: "Kubuntu Wireless using TKIP"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by DWTebriel on 2007-10-22
Hey everyone,

I currently need to use a WPA Enterprise connection using TKIP in order to connect to my university's wireless network. I know the option was available in Gnome's iteration of the gui network manager. However the Kubuntu iteration is absent, even in Gutsy.

I have found the following website saying that a new version of knetworkmanager is available that does have that option available in the GUI, located [here]("http://liquidat.wordpress.com/2007/09/20/knetworkmanager-with-tkipaes-ccmp-support-and-gnome-220/").

However I am unsure as to how to install this new version into Kubuntu. If anyone can help me out, I would greatly appreciate it. :)

---

### Post by DWTebriel on 2007-10-27
No one knows how? :(

---

### Post by kevdog on 2007-10-27
First you need to install the subversion package.  

sudo aptitude install subversion

This will allow you to download from svn archives (kind of like cvs if you know what that is).

Then to download the svn sources:
svn co svn://websvn.kde.org/branches/extragear/kde3/network/knetworkmanager/

If that doesnt work try this:

svn co svn://websvn.kde.org:443/branches/extragear/kde3/network/knetworkmanager/

Again the address url for the svn download isnt really enumerated on the page you refer to so Im kind of guessing.

If you get the sources checked out the instructions about how to compile and install them are located in the INSTALL file.  If you need more help with this let me know.

Make sure you have the following packages installed:
sudo aptitude install build-essential linux-headers-`uname -r`

---

### Post by DWTebriel on 2007-10-27
Thanks for the direction. I went ahead and read some of the kde documentation which was a great help to me. I went ahead and installed everything required for kubuntu kde compiling in general. Somewhat overkill I know, but running configure 50 billion times and hunting for libraries is a pain. :D

Here's what I installed:

[FONT="Lucida Console"]sudo aptitude install build-essential cdbs debhelper cmake libxml2-dev libxslt1-dev libbz2-dev libclucene-dev librdf-dev shared-mime-info libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev libxext-dev libjpeg-dev libpng-dev subversion libsm-dev libxinerama-dev libxrender-dev libfontconfig-dev libboost-dev libxcursor-dev doxygen libungif4-dev libdbus-1-dev libgpgme11-dev libssl-dev libgpgme11-dev libasound2-dev kdesdk-scripts libpth-dev libjasper-dev ssh libxine-dev libqimageblitz-dev libqimageblitz4 libglib2.0-dev libxkbfile-dev libenchant-dev libbluetooth-dev network-manager-dev libsmbclient-dev libxcb1-dev libcaptury-dev libxcomposite-dev libxdamage-dev libusb-dev dbus-x11 libqt4-dev libqca2-dev libeigen-dev libstreamanalyzer-dev libsoprano-dev libstrigiqtdbusclient-dev graphviz[/FONT]

After that, I found the correct svn repository:

[FONT="Lucida Console"]svn co svn://anonsvn.kde.org/home/kde/branches/extragear/kde3/network/knetworkmanager[/FONT]

I now have the source in ~/kde/knetworkmanager

I switch to that directory and try to run "./configure", only to get a "no such file or directory" message. I then try to include the extension "./configure.in.in" with a permission denied message. Sudo just says invalid command. I then make the file executable "chmod +x ./configure.in.in" and run it as "./configure.in.in" only to get syntax errors in the file.

[FONT="Lucida Console"]user@computer:~/kde/knetworkmanager$ ./configure.in.in
./configure.in.in: line 1: syntax error near unexpected token `('
./configure.in.in: line 1: `dnl AM_INIT_AUTOMAKE(knetworkmanager, 0.2.1, [email]thoenig@suse.de[/email])'[/FONT]

Any ideas?

---

### Post by kevdog on 2007-10-27
Can you post the contents of that particular directory?  Is there an autoconf or something similar?

---

### Post by DWTebriel on 2007-10-27
Here's the url to the web svn repository.

[http://websvn.kde.org/branches/extragear/kde3/network/knetworkmanager/]("http://websvn.kde.org/branches/extragear/kde3/network/knetworkmanager/")

Also, here is the listing of what is in the folder.

[FONT="Lucida Console"]AUTHORS           COPYING               knetworkmanager.kdevelop  README
ChangeLog         Doxyfile              Makefile.am               src
configure.in.bot  INSTALL               NEWS                      TODO
configure.in.in   knetworkmanager.conf  pics                      vpn-plugins[/FONT]

Thanks for your help, I greatly appreciate it.

---

### Post by kevdog on 2007-10-28
read the INSTALL file first -- like it will tell you how to generate the config file.  Also read the README file if that doesnt answer your question.

---

### Post by DWTebriel on 2007-10-28
I read both the install and readme files. The install file is the same thing that is found everywhere that contains source code.

Just out of curiosity, I downloaded the pidgin source and ran ./configure on its source folder. That ran successfully. I have a theory that the configure script within that kde repository is broken. Or I'm just trying to run a configure script on just knetworkmanager when I can only do it on a larger portion of kde, such the network section or all of kde. I hope I'm wrong though. :confused:

---

### Post by kevdog on 2007-10-28
I dont know -- I wish I did

---

### Post by DWTebriel on 2007-10-28
Thanks for your time, I definitely appreciate it. Nice profile picture by the way.

---

