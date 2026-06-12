---
title: "Made a mess installing medibuntu"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by kwinsw on 2009-04-07
Hi,

I wonder if anyone could help. I installed Ubuntu 8.10 last week - first experience of Linux - and have been mucking about with it since. However, I followed this tutorial here to install Skype:

[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

Clearly, I have done something wrong as Skype is not installed and now the Synaptic Package Manager is broken. When I try to install any package I get the error:

"An error occurred: 
The following details are provided:
E:type '--2009-04-07' is not known online 1 in source list  /etc/apt/sources.list.d/medibuntu.list
E:The list of sources could not be read.
E:_cache->open() failed, please report"

I'd be very grateful if someone can tell me how to point the package manager back to the correct sources (I'm guessing this is what's wrong, right?).

Many thanks

Karl

---

### Post by GOROSSI on 2009-04-07
post the contents of your sources.list file located in etc/apt 

it will open in text editor under accersories

---

### Post by Elfy on 2009-04-07
Hi I would delete the file and start again, although there is something in learning how to fix it :)

The file should look similar to (likely not jaunty though )


> ## Medibuntu - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free


If you do 

```
cat /etc/apt/sources.list.d/medibuntu.list
```

It doesn't - at least one line is wrong 

Either edit the file 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

and remove the offending lines, or delete it and start again

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Then redo the steps to add the repo

[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

---

### Post by ibuclaw on 2009-04-07
Try pulling the sources from the Medibuntu site again, overwriting the medibuntu.list file:
**sudo wget [noparse]http://www.medibuntu.org/sources.list.d/intrepid.list[/noparse] -O /etc/apt/sources.list.d/medibuntu.list**

And get the key/update:
**wget -q [noparse]http://packages.medibuntu.org/medibuntu-key.gpg[/noparse] -O- | sudo apt-key add - && sudo apt-get update**

Install skype should be simple thereafters:
**sudo apt-get install skype**

Regards
Iain

---

### Post by kwinsw on 2009-04-07
Here it is:

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by GOROSSI on 2009-04-07
sorry thought that file would have the edited sources in :) it's late lol

if you do what forestpixie said and delete the medibuntu.list 

then add the repo from [https://help.ubuntu.com/community/Medibuntu#Adding]("https://help.ubuntu.com/community/Medibuntu#Adding")

there is a specific page line for each version of ubuntu

As im guessing you added the repo line from the page you gave which is for 7.04 not 8.10 so it's quite old.

As for skype generally ive always found the .deb on the skype site runs better

---

### Post by kwinsw on 2009-04-07
Thanks everyone. I'll try that out and post the results here.

"As im guessing you added the repo line from the page you gave which is for 7.04 not 8.10 so it's quite old."

I think I changed feisty to ibex: last time I try and get smart before I know what I'm really doing.

Thanks again

---

### Post by kwinsw on 2009-04-07
Thank you: seems to have worked fine. The package manager now opens no problem and I've been able to install Skype. 

Forgive me for asking a stupid question, but what exactly did i just do? Synaptic Package Manager simply points to an online location, is that correct? So when you choose to install a package it goes online and downloads that package from whatever online site you've specified as its source. I had managed to point it at an invalid source and you helped me point it at the right one again. Am I even warm?

---

### Post by Elfy on 2009-04-07
Yep you are warm :)

The sources lists point at the repos and install coem from them

Your error was caused by malformed lines - check you first post - the lines should all start with either deb or deb-src - your file had '--2009-04-07' in a line

---

### Post by kwinsw on 2009-04-07
Well, at least I understood the concept - now I just have to put it into practice without breaking my PC. ;0)

Thank you again.

---

