---
title: "Please help eror message when try to do any thing like download programs etc"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by jamessquashgod on 2009-03-10
PLEASE HELP
I am totally new to ubuntu so could you please reply , if you can in non crazy mumbo jumbo ubuntu talk , thanks

so,,,,, whenever i try to update my system or download a program using add/remove i get an error message 
'E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem E:_cache->open()failed,please report'

Can someone please tell me what i have done and what i can do to solve the problem

thankyou

---

### Post by taurus on 2009-03-10
Close down update manager, add/remove, or synaptic first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get **upgrade**
```

---

### Post by Dileeshvar on 2009-03-27
hello I tried the commands given by you still
I got these messages 


"Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/Ubuntu-Studio%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081028)_dists_intrepid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

---

### Post by mlentink on 2009-03-27
Could we have a look at your software sources?
Please go to Applications>Accessories>Text-editor
Open up the file /etc/apt/sources.lst
Copy all the text, and post it here

---

### Post by Dileeshvar on 2009-03-27
# added by the release upgrader
deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main main main main main multiverse multiverse restricted restricted restricted restricted universe
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

---

### Post by mlentink on 2009-03-27
Please try the following: 
change these lines:
```
# added by the release upgrader
deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (2008102:cool:]/ intrepid main main main main main multiverse multiverse restricted restricted restricted restricted universe
```into:
```
# added by the release upgrader
# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (2008102:cool:]/ intrepid main main main main main multiverse multiverse restricted restricted restricted restricted universe
```You can do this by typing the following code into the terminal (Applications>Accessories>Terminal):
```
gksudo gedit /etc/apt/sources.lst

```this will open up the text-editor with the privileges required to open this system file

Save the file, exit the text-editor.

Now type the following into terminal:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get **upgrade**
```If you you run into problems, please let us know

---

### Post by Dileeshvar on 2009-03-27
Hi I did what you said it doesnt affect any thing 
getting same old error as before !! :(

---

### Post by Bourlog on 2009-03-27
Same problem here :-(

---

### Post by mlentink on 2009-03-27
Sorry. This is as far as my knowledge goes. 


Anyone?

In another running [thread]("http://ubuntuforums.org/showthread.php?t=1108178"):

```
sudo apt-get install -f
```

---

### Post by Dileeshvar on 2009-03-28
hey thanks a lot mlentink
I did work !!
actually after editing and making it as a comment
I then restarted the system and now everything is perfect !!

Thanks again :)

---

### Post by zvacet on 2009-03-28
@ **Dileeshvar**

In system>admin>software sources>updates check **important security updates** and refresh.

---

### Post by Dileeshvar on 2009-03-29
Ya done :)

---

