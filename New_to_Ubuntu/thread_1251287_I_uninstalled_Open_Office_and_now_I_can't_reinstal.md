---
title: "I uninstalled Open Office and now I can't reinstall it"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Green_Mac on 2009-08-27
In attempting to upgrade from OO 2.4 to OO 3, I've managed to uninstall 2.4.  When I try to reinstall it via Synaptic, I get a box saying "Could not mark all packages for installation or upgrade.  The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences" which doesn't mean a lot to me.  The list of packages goes:

openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
 Depends: openoffice.org-impress but it is not going to be installed
 Depends: openoffice.org-draw but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-report-builder-bin but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed

All suggestions gratefully received!

Mac

---

### Post by Darkwing-Duck on 2009-08-27
Okay try this instead of using synaptic. Open the terminal and use some apt-get commands.
 
```
sudo apt-get remove XXXX --purge package
```
 

Then use:
 
```
sudo apt-get clean
```

After you have finished this you should try and reinstall OO with:
 
```
 
sudo apt-get install XXXX

```
 
Let me know if this helps or if you need any more help! For more information on packages, you can go to the [Ubuntu Packages Site]("http://packages.ubuntu.com/").

---

### Post by Green_Mac on 2009-08-27
> **Wonderly said:**
> Okay try this instead of using synaptic. Open the terminal and use some apt-get commands.
 
```
sudo apt-get remove XXXX --purge package
```
 

Then use:
 
```
sudo apt-get clean
```

After you have finished this you should try and reinstall OO with:
 
```
 
sudo apt-get install XXXX

```
 
Let me know if this helps or if you need any more help! For more information on packages, you can go to the [Ubuntu Packages Site]("http://packages.ubuntu.com/").
Thanks, but is that XXXX an indication that I should put something relevant to OpenOffice there, and if so how do I work out what it is?

---

### Post by scratman on 2009-08-27
I suspect that simply typing openoffice in place of the xxxx would suffice, however for the sake of certainty, I'd recommend following all of the previously stated steps, and the installing Open Office from either Add/Remove Programs or Synaptic Package Manager.

---

### Post by dBuster on 2009-08-27
> **scratman said:**
> I suspect that simply typing openoffice in place of the xxxx would suffice, however for the sake of certainty, I'd recommend following all of the previously stated steps, and the installing Open Office from either Add/Remove Programs or Synaptic Package Manager.

What do you do when your Add/Remove is broken?  I mean it locks up the computer anytime I try to use it.  Synaptic is saying it is installed already however following the instructions at [How to Install OpenOffice.org 3.1 on Ubuntu 9.04]("http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml") it states to use add/remove to complete the installation...

---

### Post by gackt on 2009-08-27
Hey why dont you try to install it mannualy, here is the step:
1. download the file [http://download.openoffice.org/](http://download.openoffice.org/)
2. Extract 
3. sudo apt-get remove openoffice.org-core
4. open terminal and change to extracted dir of open office
5. sudo dpkg –install –force-overwrite ooobasis3.0-*.deb openoffice.org*.deb desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
6. you are done :D

---

### Post by Green_Mac on 2009-08-29
Brilliant!  That's sorted it.  Thanks a lot everyone.

---

