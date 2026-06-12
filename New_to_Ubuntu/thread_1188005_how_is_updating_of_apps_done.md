---
title: "how is updating of apps done"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by ws.venkateswaran on 2009-06-15
**how is updating done** 			
 			 			 		   		 		 		hi guys

have been using windows till about a month ago and have shifted to ubuntu 8.10... so just give a few guidelines on updating..

am not sure whether my update manager is functioning. everytime i run it it checks and says the system is up to date. till now i have not had a single update done by the update manager.

how is updating of apps done in ubuntu.. can anyone give a brief intro

if this question has been asked many times before can you just guide me to the posted replies

thanks

---

### Post by reeseslover531 on 2009-06-15
try from the command line these two commands
```
sudo apt-get update 
```
```
sudo apt-get upgrade 
```

That is the command line version of the update manager.

---

### Post by hayden92 on 2009-06-15
In case you don't know how to get to the command line:
Applications->Accessories->Terminal

You can also do this the graphical way by opening the update manager and clicking on "check"

---

### Post by ws.venkateswaran on 2009-06-15
ya i have done both..

while using terminal using the apt command i get lots of lines of codes and something like 2 upgraded 0 installed.. etc..

while using update manager there is no information.... the check option does not show me any available updates .. it just checks repos and thats it.. does it mean there are no updates to any of the apps that i have installed

what i dont understand is why is the update manager not teling me about new updates to firefox and other apps.. 

how do i check whether i have the latest of all the software.

thanks again

---

### Post by reeseslover531 on 2009-06-15
those two commands should have been what to do to check if you have the latest stuff.

---

### Post by ws.venkateswaran on 2009-06-15
Ign file: intrepid/main Translation-en_IN
Get:1 file: intrepid Release.gpg [189B]
Ign file: intrepid/universe Translation-en_IN
Ign file: intrepid/multiverse Translation-en_IN
Ign file: intrepid/restricted Translation-en_IN
Get:2 file: intrepid-updates Release.gpg [189B]
Ign file: intrepid-updates/main Translation-en_IN
Ign file: intrepid-updates/universe Translation-en_IN
Ign file: intrepid-updates/multiverse Translation-en_IN
Ign file: intrepid-updates/restricted Translation-en_IN
Get:3 file: intrepid-security Release.gpg [189B]
Ign file: intrepid-security/main Translation-en_IN
Ign file: intrepid-security/universe Translation-en_IN
Ign file: intrepid-security/multiverse Translation-en_IN
Ign file: intrepid-security/restricted Translation-en_IN
Get:4 file: intrepid Release [65.9kB]
Get:5 file: intrepid-updates Release [51.2kB]
Get:6 file: intrepid-security Release [44.0kB]    
Reading package lists... Done  


this is wat i get after apt-get update... what does this mean

---

### Post by alphacrucis2 on 2009-06-15
> **ws.venkateswaran said:**
> ya i have done both..

while using terminal using the apt command i get lots of lines of codes and something like 2 upgraded 0 installed.. etc..

while using update manager there is no information.... the check option does not show me any available updates .. it just checks repos and thats it.. does it mean there are no updates to any of the apps that i have installed

what i dont understand is why is the update manager not teling me about new updates to firefox and other apps.. 

how do i check whether i have the latest of all the software.

thanks again

In your System Administration software sources. Click on the updates tab and check that you have security, recommended, proposed and backports enabled. That doesn't mean to say that you will for example get firefox 3.5 unless a specific backport to 8.10 is done. In some cases if you want application version x which isn't in the repos. You can still probably get the updated version (provided the necessary dependencies can be met) by installing from a PPA, install a prepared deb package, or as a last resort compiling the program from source. As a newbie, if there is a particular program version you want that doesn't seem to be in the repos then ask on the forum for help.

---

### Post by halitech on 2009-06-15
sudo apt-get update only checks to see if there are any new packages, you need to do the sudo apt-get upgrade to actually see if there are any and install them

---

### Post by ws.venkateswaran on 2009-06-15
the options (security, recommended, proposed and backports .) in the software sources are greyed out... how do i enable them..

and this is what i get after an apt-get upgrade command
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

.. does it mean all the apps are updated fully

---

### Post by alphacrucis2 on 2009-06-15
> **ws.venkateswaran said:**
> the options (security, recommended, proposed and backports .) in the software sources are greyed out... how do i enable them..

and this is what i get after an apt-get upgrade command
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

.. does it mean all the apps are updated fully

Normally yes. The fact that those options you mention are greyed out seems a little odd. On the Ubuntu Software tab of the same program. What server have you selected? Are the options on that tab greyed out too? It should have asked you for the admin password. If it didn't then try accessing the same thing via System Administration Synaptic package manager. Then settings repositories. Is it still greyed out?

---

### Post by ws.venkateswaran on 2009-06-15
its solved now:p

i have been using a repo dump that i store in my desktop.
so i had not checked any of the software sources in       download from internet option-- instead i just use third party software

once i checked them update manager is working wonderfully. thanks a lot to everyone 

one more problem.. seems some errors in upgrading and only partial upgrade is possible.  why is that . is it a problem

---

### Post by alphacrucis2 on 2009-06-15
> **ws.venkateswaran said:**
> its solved now:p

i have been using a repo dump that i store in my desktop.
so i had not checked any of the software sources in       download from internet option-- instead i just use third party software

once i checked them update manager is working wonderfully. thanks a lot to everyone 

one more problem.. seems some errors in upgrading and only partial upgrade is possible.  why is that . is it a problem

Possibly because a package is in the repos that doesn't have all dependencies met. One option is to wait a couple of days and try again.

---

