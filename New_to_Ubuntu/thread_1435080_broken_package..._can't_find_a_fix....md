---
title: "broken package... can't find a fix..."
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Fizz.LeChat on 2010-03-21
I've been trying periodically to get my brand new Brother printer working for the last 2 years... Nuff said about that! Instead I've been using it as a copier... Tried again to install the printer driver and the system broke... 

I tried to use synaptic to fix broken packages but I get this error:

E: The package mfc230ccupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Then synaptic closes... :(

I've tried to remove the package with no luck...

I've tried to re-install with no luck... 

Always get the same error when I click on package:

Could not open 'mfc230ccupswrapper-1.0.1-1.i386.deb'
The package might be corrupted or you are not allowed to open the file. Check permissions of the file.

Well I've downloaded the file several times, and the permissions are ok! So I tried something else:

mbg@mbg-desktop-8:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc230ccupswrapper needs to be reinstalled, but I can't find an archive for it.
mbg@mbg-desktop-8:~$ 

The file is in my downloads but won't open...
***************************************
Then I try:

mbg@mbg-desktop-8:~$ sudo apt-get clean
mbg@mbg-desktop-8:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc230ccupswrapper needs to be reinstalled, but I can't find an archive for it.
mbg@mbg-desktop-8:~$ 
******************************************
Then I try as suggested elsewhere:

mbg@mbg-desktop-8:~$ sudo dpkg --remove -force --force-remove-reinstreq mfc230ccupswrapper
dpkg: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
mbg@mbg-desktop-8:~$ sudo dpkg --remove -force --force-remove-reinstreq mfc230ccupswrapper-1.0.1-1.i386.deb
dpkg: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
mbg@mbg-desktop-8:~$ 

So I guess there must be a typo somewhere...
******************************************

and when I try to run synaptic I still get:

E: The package mfc230ccupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Then synaptic closes... :(
**************************************
I tried the update manager:

Update manager suggested it would force removal of the package and after working for awhile gave this message:

Package in an inconsistent state
The package 'mfc230ccupswrapper' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

And then it closed...

Any ideas??? Please??? Anyone...?

Thanks.


Fizz.

---

### Post by NightwishFan on 2010-03-21
Perhaps try:
```
dpkg --purge *packagename*
```

This happened to me with PPA Nvidia drivers and I never find a cure. This may work, though I have no broken packages to test it on.

---

### Post by plucky on 2010-03-21
Try this [link](http://ubuntuforums.org/showpost.php?p=8986930&postcount=12)


Then if that works,try installing the drivers using **Synaptic Package Manager**

Open Synaptic and search for **mfc-230c** and you should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
``` You have to install both,and then add a new printer,and your driver will now be available for your printer.


Good Luck

---

### Post by Trandre on 2010-03-21
I had a simular package problem. Then I ran sudo apt-get update it stated that i had conflict in this and that line in the status document. So i open the status document and deleted the string which was broken and presto it work after a sudo apt-get update. had to do the same thing in the available file.

Here are the strings that helped me:
[http://ubuntuforums.org/showthread.php?t=1430660](http://ubuntuforums.org/showthread.php?t=1430660)
[http://ubuntuforums.org/showthread.php?t=1434436](http://ubuntuforums.org/showthread.php?t=1434436)

Trandre

---

### Post by Fizz.LeChat on 2010-03-21
> **NightwishFan said:**
> Perhaps try:
```
dpkg --purge *packagename*
```

This happened to me with PPA Nvidia drivers and I never find a cure. This may work, though I have no broken packages to test it on.

*************************
Thanks, I tried it and got this:

mbg@mbg-desktop-8:~$ sudo dpkg --purge mfc230ccupswrapper
dpkg: error processing mfc230ccupswrapper (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mfc230ccupswrapper
mbg@mbg-desktop-8:~$ 

So that didn't work... :(  Anyone else have a suggestion?

---

### Post by NightwishFan on 2010-03-21
Perhaps reinstall as suggested? I assumed you tried that though. One of the posters above advised you manually remove it from the registry. I have heard reports along that line that worked.

[http://ubuntuforums.org/showpost.php?p=3412016&postcount=10](http://ubuntuforums.org/showpost.php?p=3412016&postcount=10)

---

### Post by Trandre on 2010-03-21
Try to run this and post what you get
```
sudo dpkg-reconfigure-a
```

Trandre

---

### Post by Fizz.LeChat on 2010-03-21
> **plucky said:**
> Try this [link](http://ubuntuforums.org/showpost.php?p=8986930&postcount=12)


Then if that works,try installing the drivers using **Synaptic Package Manager**

Open Synaptic and search for **mfc-230c** and you should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
``` You have to install both,and then add a new printer,and your driver will now be available for your printer.


Good Luck

Thank you Plucky!!! The first part worked!!! Now I have my system back and the update manager worked for almost 40 minutes updating the system. It was overdue... ;) Now for the second part, re-installing the Brother drivers, I don't know if I want to go through that again or just send it to the recycling bin with the price tag still on it... We'll see after dinner... I'll be back! ;)

---

### Post by Fizz.LeChat on 2010-03-21
> **Trandre said:**
> Try to run this and post what you get
```
sudo dpkg-reconfigure-a
```

Trandre

The main problem has already been solved but I was curious about this command... This is what I got from a cut&paste:

mbg@mbg-desktop-8:~$ sudo dpkg-reconfigure-a
[sudo] password for mbg: 
sudo: dpkg-reconfigure-a: command not found
mbg@mbg-desktop-8:~$

---

### Post by NightwishFan on 2010-03-21
```
sudo dpkg-reconfigure -a
```

---

### Post by Fizz.LeChat on 2010-03-21
> **plucky said:**
> Try this [link](http://ubuntuforums.org/showpost.php?p=8986930&postcount=12)


Then if that works,try installing the drivers using **Synaptic Package Manager**

Open Synaptic and search for **mfc-230c** and you should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
``` You have to install both,and then add a new printer,and your driver will now be available for your printer.


Good Luck

Well Plucky, as I said, the first part worked, ALL packages have been fixed with the link at the beginning of your post! Thank you very much!!!

As for the second part, I installed the packages, added the printer, and curiously it doesn't show up with a "lsusb" but when I try to print a test page it spits out part of the graphic with an I/O error... I'm putting it out with the recycling... Should have gotten another HP but the Brother was cheaper, at least it seemed cheaper at the time... 

Thanks to all of you for the help!! I really appreciate it! That's a community.  :)  This is SOLVED!!

---

### Post by Fizz.LeChat on 2010-03-21
> **NightwishFan said:**
> Perhaps reinstall as suggested? I assumed you tried that though. One of the posters above advised you manually remove it from the registry. I have heard reports along that line that worked.

[http://ubuntuforums.org/showpost.php?p=3412016&postcount=10](http://ubuntuforums.org/showpost.php?p=3412016&postcount=10)

Thanks for the Linux Adventures link... Very interesting! I'll keep it handy and send others!
Excellent source for Debian Beginners: [http://www.linuxadventures.net/](http://www.linuxadventures.net/)

---

