---
title: "Problem Installing Software Center Or Synaptic"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by YummyOlives on 2011-04-13
Hi
Having serious problems with the installation of these two softwares : following is the error when installing software centre or synaptic through the Terminal :

sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate



Thanks for any sort of assistance

---

### Post by vivek.pandey on 2011-04-13
first of all why at all you are trying to install synaptic or software center? they come along preinstalled

---

### Post by Enigmapond on 2011-04-13
Navigate to System/Administration/Synaptic Package Manager

There you go... ):P

---

### Post by earthpigg on 2011-04-13
> first of all why at all you are trying to install synaptic or software center? they come along preinstalled

> Navigate to System/Administration/Synaptic Package Manager

i don't think it will be that easy. there is definitely something wonky going on with his system.

this is what he sees:

> **YummyOlives said:**
> 

```
sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package synaptic is not available**, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

**E: Package 'synaptic' has no installation candidate**
```


this is what he ***should*** see:

```
[chris: ~]$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**synaptic is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```

or the standard message indicating that the package (synaptic) can be updated. but certainly **not** messages indicating that there is no such package as synaptic.

can you do us a favor, and run this command:

```
sudo apt-get update
```

and then try installing synaptic?


if that doesn't work, we will need more details. is this a command line only install, or an ubuntu server install, or regular ubuntu? does your system otherwise function? are you connected to the internet, at all ("ping -c 3 google.com" to check) do you have gnome or X installed at all? does update manager work? any idea of what could have happened leading up to this issue?

---

### Post by computerandu on 2011-04-13
> **YummyOlives said:**
> Hi
Having serious problems with the installation of these two softwares : following is the error when installing software centre or synaptic through the Terminal :

sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate





Thanks for any sort of assistance


Try sudo apt-cache search synaptic

then choose the appropriate synaptic package

I hope this will help you

---

### Post by YummyOlives on 2011-04-13
Ok first of all thanks for replying !

the reason i am trying to install software center or synaptics is beacuse i uninstalled them :)))

why ?

beacuse Wine screwed up ! I uninstalled wine and try to start the software center to reinstall Wine BUT guess what software Center will not start !

Then - i uninstalled software center from the terminal , thinking that i will be able to install it via terminal again BUT no , that error shows up !

NEXT - i try to start synaptic , it wont start either ! i uninstalled it as well ! LOL

==> AND now i am trying to re-install both packages , so yea i had them installed beforehand but Wine screwed up everything. 

Rest of the Linux seems fine to me as far as i see.

TRIED ::

1) sudo apt-get update

Result::

sudo apt-get update
E: Type ‘ain’ is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.

2) sudo apt-cache search synaptic

Result::

sudo apt-cache search synaptic
cpad-common - common files to support the Synaptics cPad driver kernel modules
cpad-kernel-dev - kernel header for the Synaptics cPad driver
cpad-kernel-source - source for the Synaptics cPad driver
gpointing-device-settings - configuration tool for pointing devices
gsynaptics - configuration tool for pointing devices (transitional package)
muon - package manager for KDE
tpconfig - touchpad device configuration utility
xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org server
sessioninstaller - APT based installer using PackgeKit's session DBus API


-------------------------------------

No Software Center Or Synaptics installed right now ! Nothing in the system>Admin Panel either.

Wine = :-x

Everyone please enjoy some  = :popcorn:

---

### Post by Enigmapond on 2011-04-13
Well you can get the package for Software Centre here..
[http://packages.ubuntu.com/maverick/software-center](http://packages.ubuntu.com/maverick/software-center)

And see this thread regarding Synaptic....

[http://ubuntuforums.org/showthread.php?t=235798](http://ubuntuforums.org/showthread.php?t=235798)

But I'm sure there must be an easier way..??

---

### Post by earthpigg on 2011-04-13
well uninstalling software center was a silly thing to do.

using 10.10 maverick on 32-bit ubuntu? 

[http://packages.ubuntu.com/maverick/synaptic](http://packages.ubuntu.com/maverick/synaptic)

download the i386 version, at the bottom, to your desktop. double click on it, and gdebi will tell you that dependancies are not met. follow the links, manually find and install those dependancies. 

if gdebi is also uninstalled, 

sudo dpkg -i ~/Desktop/synaptic_0.63.1ubuntu14_i386.deb

---

### Post by YummyOlives on 2011-04-13
@enigmapond 

not sure what to do there ! 

@earthpig

double clicking =  software index is broken  :confused:

---

### Post by Enigmapond on 2011-04-13
Same thing you do with the other suggestion. Scroll to the bottom of the page and you will see a small box with "All Architectures" or if there is more than 1 version listed, download the "i386" version deb file and double click it and it will automatically install as long as you have gdebi installed...which you should. If not, open a terminal and do:

```
sudo apt-get install gdebi
```

---

### Post by YummyOlives on 2011-04-13
OK

 after running this cmd in terminal :: 

 sudo dpkg -i ~/Desktop/synaptic_0.63.1ubuntu14_i386.deb

i have the synaptic package manager in the system>admin>

BUT as i open the synaptic package manager i get the following ::

E: Type ‘ain’ is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


:confused:

---

### Post by Enigmapond on 2011-04-13
You have to 1st download the deb files for both software centre and synaptic.....it's like trying to start a car before the engine is in.. :)

---

### Post by coffeecat on 2011-04-13
> **YummyOlives said:**
> 
BUT as i open the synaptic package manager i get the following ::

E: Type ‘ain’ is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


You have a bad line 3 in /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list. Post the contents of that file and someone will tell you how to edit it so that you don't get that error. Alternatively, disable the ubuntu-wine-ppa-maverick repository. Now that you've got Synaptic installed, you can do that in Synaptic, Settings menu > Repositories > Other software tab.

---

### Post by YummyOlives on 2011-04-13
> **Enigmapond said:**
> Same thing you do with the other suggestion. Scroll to the bottom of the page and you will see a small box with "All Architectures" or if there is more than 1 version listed, download the "i386" version deb file and double click it and it will automatically install as long as you have gdebi installed...which you should. If not, open a terminal and do:

```
sudo apt-get install gdebi
```


thanks for the reply, did as u advise BUT all i get is an error box 

''Software Index is Broken :

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'. ''


:confused:

---

### Post by Enigmapond on 2011-04-13
Sorry for your problems but...at this point, if it were me. I would just re-install Ubuntu. You seem to have created a lot of issues by what you did. The easiest way is to back up your important files and in 30mins...all will be solved with a fresh, squeaky clean install... :)

Good Luck!

---

### Post by earthpigg on 2011-04-13
waiting on results of 

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```


> **Enigmapond said:**
> Sorry for your problems but...at this point, if it were me. I would just re-install Ubuntu. You seem to have created a lot of issues by what you did. The easiest way is to back up your important files and in 30mins...all will be solved with a fresh, squeaky clean install... :)

Good Luck!

nah, we're still making progress. but, ya, he certainly could do that if he chooses.

---

### Post by Enigmapond on 2011-04-13
> **earthpigg said:**
> 
nah, we're still making progress. but, ya, he certainly could do that if he chooses.

Oh definitely, push on. What doesn't destroy an OS, makes it stronger...I just have very little tolerance.. LOL

Cheers!):P

---

### Post by YummyOlives on 2011-04-14
progress it is ! :) 

Results:

cat /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
ain

thanks

---

### Post by coffeecat on 2011-04-14
Open terminal:

```
gksudo gedit  /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```Remove that superfluous third line:

```
ain
```

...so that the file looks like this:

```
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
```


Save the modified file, open Synaptic, click on "Reload" and see if it works for you now.

---

### Post by Arand on 2011-04-14
> **YummyOlives said:**
> progress it is ! :) 

Results:

cat /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
ain

thanksEdit that file```
gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```Remove the line containing "ain" and run```
sudo apt-get update
```and possibly```
sudo apt-get install -f
```

- arand

---

### Post by YummyOlives on 2011-04-14
> **coffeecat said:**
> Open terminal:

```
gksudo gedit  /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```Remove that superfluous third line:

```
ain
```...so that the file looks like this:

```
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
```
Save the modified file, open Synaptic, click on "Reload" and see if it works for you now.



Thankyou sir ! that did it ! :popcorn:

Now i can open the synaptic package manager ... One last Query ! 

How to install the software center from here !

thanks a gazillion peeps :D

---

### Post by YummyOlives on 2011-04-14
Ok software center found in the list BUT get the following error while marking for installation ::

''could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.Make sure that all required repositories are added and enabled in the preferences.

software-center:

Package software-center has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list''

:confused: sorry for the extra headache

---

### Post by coffeecat on 2011-04-14
A dependency error often means that  you have enabled 3rd party repositories that have brought in packages that conflict with whatever you are trying to install, or conflict with a dependency. What 3rd-party repositories have you enabled apart from ubuntu-wine-ppa-maverick?

Synaptic is telling me (in Maverick) that software-center conflicts with gnome-app-install and software-store. Neither of these are listed as being in the Ubuntu repositories (I;ve never heard of them anyway) but have you installed either from another repository? If you have, they will be listed as being installed in Synaptic. If you have, uninstall them.

**EDIT**: a quick google shows that the gnome-app-install package gave you the old Add/Remove utility which was replaced by Software Centre. Software Store looks like an early version of Software Center. Did you manually install a deb of software-store?

---

### Post by YummyOlives on 2011-04-14
> **coffeecat said:**
> A dependency error often means that  you have enabled 3rd party repositories that have brought in packages that conflict with whatever you are trying to install, or conflict with a dependency. What 3rd-party repositories have you enabled apart from ubuntu-wine-ppa-maverick?

Synaptic is telling me (in Maverick) that software-center conflicts with gnome-app-install and software-store. Neither of these are listed as being in the Ubuntu repositories (I;ve never heard of them anyway) but have you installed either from another repository? If you have, they will be listed as being installed in Synaptic. If you have, uninstall them.

**EDIT**: a quick google shows that the gnome-app-install package gave you the old Add/Remove utility which was replaced by Software Centre. Software Store looks like an early version of Software Center. Did you manually install a deb of software-store?


i am really sorry , i dont really know how to respond here ! i havent installed anything manually apart from what the update manager suggests ! 

I had both, synaptic manager and software-center running along side before with no problems ! Problems started when i manually uninstalled both packages via terminal !

New to linux! Apologies ..:(

---

### Post by coffeecat on 2011-04-14
No apologies necessary. :) We all had to learn at one time.

Apart from what I have already suggested, I don't know what else you can do. Did you check in Synaptic to see if gnome-app-install and/or software-store have crept in there somehow?

Otherwise, as someone else suggested, you may want to think about re-installing Ubuntu. If you can't re-install Software Centre then something is very wrong. Write it off against experience - you've learnt a few things - and re-install. It'll be quicker than trying to repair a system with a number of problems.

---

### Post by YummyOlives on 2011-04-15
Thanks alot for the help! 

I think i  would keep current version of Ubuntu since i am able to install every other package from synaptics !  its the same as the software center .

Cheers !

---

