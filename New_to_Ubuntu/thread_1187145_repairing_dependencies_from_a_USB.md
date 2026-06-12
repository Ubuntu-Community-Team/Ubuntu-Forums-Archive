---
title: "repairing dependencies from a USB?"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by weverall on 2009-06-14
i have a broken dependenciy "libstdc++6-3.3.dev"

and when i follow instructions to repair it, it says i need to insert a CD, but since im runnning ubuntu off a Acer Aspire, i have no CD rom and installed it through a USB, im running the Netbook edition.

is there anyway of repairing this dependency with my USB stick? i have no way of adding a CD rom via USB at the moment.

Any help would be greatly appreciated

Dave

---

### Post by gradinaruvasile on 2009-06-14
System->Administration->Software sources
Do u have ticled all 5 items on the ubuntu softwaretab
and the upper 2 on the updates tab?

---

### Post by weverall on 2009-06-14
i have all those selected ones ticked

cheers for the quick reply

Dave

---

### Post by gradinaruvasile on 2009-06-14
open a terminal
type:

sudo apt-get install -f

---

### Post by weverall on 2009-06-14
ive tried this, 

david@david-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev g++-4.3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  g++-4.3
Suggested packages:
  g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
The following NEW packages will be installed
  g++-4.3
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/4162kB of archives.
After this operation, 9134kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media Change: Please insert the disc labelled
 'Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)'
in the drive ‘/cdrom/’ and press enter

and this is where i always get stuck, i dont have the cd, just the usb

---

### Post by weverall on 2009-06-14
ive tried many things now, even trying to copy all the files from my USB into the /cdrom/ folder on my file storage 

doesnt work, 

its getting annoying as i cant access the add/remove software to install new stuff, and cant upate the system

anyhelp ASAP please please, i can acceess files on another computer if that would help?

Dave

---

### Post by weverall on 2009-06-14
SORTED IT MYSELF


on software sources, i unselected the CD option in the box at the bottom of the first tab

then just ran the apt-get terminal

JOB DONE

---

### Post by unutbu on 2009-06-14
weverall, do you have an internet connection while running Ubuntu on the Acer Aspire?
If so, then click System>Admin>Software Sources and disable the checkbox entitled 
"Cdrom with Ubuntu". You must have the CD-ROM enabled as a software source -- that is why you are getting the message:

Media Change: Please insert the disc labelled
'Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)'

Click the Close button. Then in the terminal type
```

sudo apt-get update
sudo apt-get -f install
```

If that doesn't solve the problem, please post the terminal output. 
[Code tags](" http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") would be appreciated.

If, on the other hand, you do not have an internet connection while running Ubuntu, then
you can use Keryx ([http://keryxproject.org/](http://keryxproject.org/)) to download packages with the necessary dependencies. Keryx can run on Linux, OSX or Windows. It can download the deb packages you need and work out the dependency issues for you. Here are instructions on how to use Keryx: 
[http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

---

