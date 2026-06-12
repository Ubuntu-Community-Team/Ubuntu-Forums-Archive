---
title: "rubyripper will not install"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by spiral the dog on 2010-07-22
Hi try to install rubyripper followed the code but after first line it comes up with

add-apt-repository: command not found
then if i put in the next line its says

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

what should i do next 

when i put the last line it says

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rubyripper-gtk

should i run sudo apt-cdrom then what?

help!  
oh running on ubuntu 9.04

---

### Post by Elfy on 2010-07-22
Moved to support forum.

Open Software Sources - System - Admin menu.

Remove the tick from the cdrom box, close and reload.

---

### Post by spiral the dog on 2010-07-24
hi
it is still saying
after the first line

sudo: add-apt-repository: command not found

then after second line
reading package list

then third line

sudo apt-get install rubyripper-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rubyripper-gtk

so still can not get it

---

### Post by oldos2er on 2010-07-24
add-apt-repository only works in Karmic (9.10) and later versions. You'll need to manually add it via menus System, Administration, Software Sources, Other Software, Add; or edit /etc/apt/sources.list (gksu gedit /etc/apt/sources.list).

---

### Post by spiral the dog on 2010-07-25
hi ok thanks what do i type in the apt line?
in the third party software then click add ?

I need talking to like a child with these thing still learning

Tez

---

### Post by realzippy on 2010-07-25
Ok,so do that:

Open terminal,type:

```
gksudo gedit /etc/apt/sources.list
```

the sources list will appear where you have to paste in (at the end e.g,does not matter):

[B]deb [http://ppa.launchpad.net/nikil.mehta/ppa/ubuntu](http://ppa.launchpad.net/nikil.mehta/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/nikil.mehta/ppa/ubuntu](http://ppa.launchpad.net/nikil.mehta/ppa/ubuntu) jaunty main [/B]

close the file saving changes.
Back to terminal,type:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CCE60C6A

```

then:

```
sudo apt-get update
```

then

```
sudo apt-get install rubyripper-gtk
```

---

### Post by spiral the dog on 2010-07-25
ok i have done that all went fine i think
but it is still not in applications
????

---

### Post by AlphaLexman on 2010-07-25
Type:
```
Alt-F2
```
to open the 'Run Application' dialog and type:
```
rrip_gui
```

---

### Post by realzippy on 2010-07-26
> **spiral the dog said:**
> ok i have done that all went fine i think
but it is still not in applications
????

It should be in Applications/Sound&Video/Rubyripper.
If not (strange?),test what *AlphaLexman* suggested:

```
rrip_gui
```

---

### Post by spiral the dog on 2010-07-28
many thanks to you all its worked, now a lot of ripping to do....

---

