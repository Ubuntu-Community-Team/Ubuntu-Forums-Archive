---
title: "Broadcomm B43 ALWAYS asks for CD...install problems..."
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Dav_Criv on 2008-05-08
Hello, I am running into a problem when i try to install the firmware for the Broadcomm B43 wireless ....i dont know why it is doing this...any help on this would e appreciated!!! Ill explain:
When i try to download the firmware either through the terminal, synaptic package manager, or through hardware drivers it ALWAYS askes me to insert the Ubuntu CD. This is the output i get using the terminal:

$ sudo aptitude install b43-fwcutter 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 
The following packages are unused and will be REMOVED:
libawn0 
The following NEW packages will be installed:
b43-fwcutter 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/15.8kB of archives. After unpacking 61.4kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)' in the drive '/cdrom/' and press [Enter].

Why does it do this?? 
When I insert the Ubuntu CD (Which i downloaded from unbuntu website) it still askes me to insert the 8.04 _Hardy Heron_ - Release i386 (20080423) CD.....I dont think this matters but I named the CD Ubuntu 8.04...which isnt the same as what linux askes me to insert....i dont beleive this matters....but i dont know. In any case i cant even download the firmware without me being asked to insert the CD.
Has anyone else run into this problem???
any help would be great,
Thank you,
Dav_Criv

---

### Post by Ayuthia on 2008-05-08
**EDIT:  Please read Kevdog's post (#3) before doing this.  We should make sure that we understand why it is happening in the first place.**

The easiest way is to go into /etc/apt/sources.list and comment out that CD.  Just look for a line that starts with deb cdrom and place a # in front of it.  To edit the file:
```
gksu gedit /etc/apt/sources.list
```

Before you do it, you can make a backup copy of the file (in case something odd happens):
```
cp /etc/apt/sources.list ~/sources.backup
```

What this will do is hide that CD.  It should no longer ask you for the CD.  If you need the CD, I would just add it again instead of removing the #.  I think that renaming the CD might have done it because it looks for the name.

---

### Post by kevdog on 2008-05-08
Can you post your /etc/apt/sources.list?  Just want to confirm this is the problem.

---

### Post by Dav_Criv on 2008-05-10
:guitar: Thank you very much....placing a # in front of the deb CDROM eliminated the problem....
I installed the firmware and the wireless network detects other networks but for some strange reason it wont connect now?? Any ideas??

---

### Post by Ayuthia on 2008-05-10
Can you post your lspci -nn and lshw -C network?  It would help us see what your wireless card is and what that hardware is using.

If you have encryption, try turning it off to see if you can connect without it.  If this is the issue you might check out post #30 [here]("http://ubuntuforums.org/showthread.php?t=779754&page=3").

Otherwise, you might try a different channel (maybe 1, 5, or 6).

---

