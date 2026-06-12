---
title: "cannot finalize installation of OpenOffice 3.0.1"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by al.adab on 2009-05-13
can you please help (I'm on Ubuntu 9.04): 

I'm following the directions given at [http://ubuntuforums.org/showthread.php?t=1054126;](http://ubuntuforums.org/showthread.php?t=1054126;)

The name of the Linux Deb file I extracted onto my Home folder ("Daniele) and copied onto Desktop is *OOO310_m11_native_packed-4_en-US.9399*;

The first command *sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb* went through fine; 

I can't understand the second command (as given at the thread mentioned above). I tried *sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb* and I got the following message: 

[I]dpkg: error processing /home/daniele/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/daniele/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9376_all.deb[/I]

I tried to replace the final bit with *9399* (instead of *9376*) but it didn't work either...

What am I doing wrong? Thanks for your help!

---

### Post by fooman on 2009-05-13
if you are using 9.04....isn't openoffice 3.0.1 already installed by default?

what do you have under applications > office ?

AFAIK there should be openoffice apps pre-installed there and they should be version 3.0.1.

---

### Post by al.adab on 2009-05-13
I removed the pre-installed version of OO.org (problems with OO.org extensions dealt with in other posts). I then tried to download 3.0.1 through the *sudo apt-get install* procedure, but the version I got turned out to be even more buggy (to the extent that it failed to deal with normal text processing like copy&paste). I'm now trying to re-install it again by following the directions given at [http://ubuntuforums.org/showthread.php?t=1054126](http://ubuntuforums.org/showthread.php?t=1054126) to see if it's a better option...

---

### Post by fooman on 2009-05-13
well.  if you want to try the latest 3.1 version,  it is available from the launchpad ppa repos.

to install,  just add the repos to your apt sources list.  then use synaptic or apt-get to install.

here is a quick how-to if you want to try:

you first need to add the repositories to the sources.list file.  so open a terminal and type or copy/paste the following:

```
 gksudo gedit /etc/apt/sources.list 
```when it opens, add (copy/paste) the following lines to the bottom of the file:

```
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main
```*save* and then close the file.

next, add the PGP key so you do not see any errors about untrusted repositories.  use this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xd2bb86e0ebd0f0a43d4db3a760d11217247d1cff
```then in a terminal, run:

```
 sudo apt-get update && sudo apt-get upgrade
```if openoffice is already installed,  it should upgrade to the 3.1 version.  if it is not already installed,  try this in a terminal to install the entire openoffice suite:

```
 sudo apt-get install openoffice.org
```hope that helps.

---

### Post by al.adab on 2009-05-13
Thanks for your help. Really appreciated.

Well, it worked, the 3.1.0 version is there...flashy and everything, I have to say but...I just tried to create a document and save it. The word text processor seems to be ok now...

...when I try to save it, though, the dialogue looks somewhat buggy and slow: 

1) the folder list looks initially incomplete
2) it then gradually complete itself if I click on it or if I wait for some 10/20 secs. 

I tried to go to Tools>Options>Open/Save Dialogues and tick it off, but (unlike its predecessors) nothing changes in terms of save dialogue...

---

