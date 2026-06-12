---
title: "vmware 3.0 how do i uninstall in 9.10"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by jwflammer on 2009-11-08
ok I am new to ubuntu and i love it f^&% windows :)! But my GF is not fond, so i tried both Virtualbox and Vmware and VB is way better so plez help i need to uninstall Vmware and i dont know how.

---

### Post by noelvh on 2009-11-08
you should be able to run
```
sudo apt-get remove *package name*
```
So how did you install VMware? did you install from the repos or a deb file, well the command should work.

Noel

---

### Post by jwflammer on 2009-11-08
i use the sudo bash vmware-3.0.bunble

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package

thats what i got trying your option :(

---

### Post by noelvh on 2009-11-08
did you try 
sudo apt-get remove vmware-3.0.bunble

---

### Post by jwflammer on 2009-11-08
same thing 

john@the-laptop:/$ sudo apt-get remove vmware-3.0.bunble
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware-3.0.bunble

i dont know what to do and at this point i really dont want to start all over again :) but hey will get it

---

### Post by noelvh on 2009-11-08
So how did you install this? and is it really installed?

Noel

---

### Post by jwflammer on 2009-11-08
thanks yeah its really installed!! i did 

john@the-laptop:~/Downloads$ gksudo bash ./VMware-Player-3.0.bundle

and an installer app pop's up and i pressed next to install and well every time i redo this step in terminal it says 

ExtractingExtracting VMware Installer...done.

why wont it uninstall i don't see it in the ubuntu software center

---

### Post by jwflammer on 2009-11-08
ok i tried running it and now it wont even open :( more problems i still have hidden folders for the program and other items within menus that say vmware. idk i just want all of it gone !!

---

### Post by noelvh on 2009-11-08
Well that install method is above me. There could be an uninstaller in that file but I do not install using that method. I stick to .deb files as I know how to control them. 

I am sorry.

Noel

---

### Post by jwflammer on 2009-11-08
its ok ill figure this bitch out lol thanks any way ill confide in you later :) ty

---

### Post by bacardiandwatermelon on 2009-11-08
I did a super quick search and found this for uninstalling vmware 2... it may be the same...
```
**Uninstalling Source Installs**

 VMware Server installs with the web management console:

sudo vmware-uninstall-mui.pl

VMware Server installs from source may be removed by running the following command:

sudo vmware-uninstall.pl

If you experience problems during the uninstall, remove ~/.vmware and retry the steps above. 
You may also wish to remove your virtual machines by removing /var/lib/vmware. It is also recommended that you remove 
```The info was here..
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by jwflammer on 2009-11-08
ok cool i got it :)!!!!! yeah what i did is do a search for vmware and well it came up with a log file and in that file was a lot of crap so i did a find text and in there was a product name and its name was vmware-player-3.0.0.2093.....something and omg i got it to uninstall with

sudo bash vmware-installer -u vmware-player-3.0.0.203739

and a pop up screen came forth and i just fallowed the steps ya!! i got it to uninstall

---

### Post by noelvh on 2009-11-08
Cool!!! Glad you got it.

Noel

---

### Post by ehlenfeld on 2009-12-20
Having same problems and stumbled upon this solution;

open terminal and navigate to where vmware is located [/etc/vmare/]. You should see the installer script located there.

enter: sudo vmware-installer --uninstall-product vmware-player

you should see this
All configuration information is about to be removed. Do you wish to
keep your configuration files? [no]:

vmware player should be removed now. this worked for me but not sure how you installed yours (I used the default installations ).

Good luck!

---

