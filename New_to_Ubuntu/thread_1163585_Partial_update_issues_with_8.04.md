---
title: "Partial update issues with 8.04"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by CBHedricks on 2009-05-18
After a lot of trial and error with suggestions for using sudo commands and apt commands to fix this issue I am still having problems with the update manager not being able to do anything other than a 'partial update' recommendation that consistently fails and says that OpenOffice software updates were not able to be installed due to authentication errors.

Other updates appear to install but the update manager constantly re-appears and only does the partial update process again and again.

If anyone could work with me on this issue I would appreciate it.

CB

---

### Post by taurus on 2009-05-18
Post your /etc/apt/sources.list?  Did you happen to add ppa.launchpad.net to your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by CBHedricks on 2009-05-21
Using the commnad you listed out I get error stating "no such directory" and nothing else.  Is there a different directory listing for Ubuntu 8.04 for this same output?

I am still not able to do updates for OpenOffice and other apps.  The update manager is only offering to do partial updates over and over again.

Thanks

---

### Post by CBHedricks on 2009-05-21
Additional erros are now coming up.  It says unable to authenticate some packages and throws up a listing of OpenOffice files and three others related to open office.

Please help.

---

### Post by CBHedricks on 2009-05-22
Ok.. finally got the cat command to work as it should.  Here is the output of cat /etc/apt/sources.list on my notebook...

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

Please let me know if this is the correct output and if I need to change any of the sources.  Additionally some steps for changing them correctly will be appreciated as well.

CB

---

### Post by CBHedricks on 2009-05-22
I get this error when trying to update sources.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

---

### Post by CBHedricks on 2009-05-22
This is a listing of the files it cannot upgrade when it does the 'partial upgrade' that it advises from update manager error messages.

openoffice.org
openoffice.org-base
openoffice.org-base-core
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-filter-mobiledev
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-java-common
openoffice.org-math
openoffice.org-officebean
openoffice.org-report-builder-bin
openoffice.org-style-human
openoffice.org-writer
ttf-opensymbol
uno-libs3
ure

---

### Post by taurus on 2009-05-22
> deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

As you can see from the last line of your /etc/apt/sources.list, you've added a ppa.launchpad.net repo for OpenOffice.  Therefore, you need to install/import the keys for ppa.launchpad.net.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding a PPA to your Ubuntu repositories](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA#Adding a PPA to your Ubuntu repositories)

---

### Post by CBHedricks on 2009-05-22
OK... that is a good tip.  Now would the keys for the OpenOffice repository be in the FTP side of the site or on the home page.  Also is it a generic key that works for all the files the site hosts or just OpenOffice?

Thanks

---

### Post by CBHedricks on 2009-05-22
I found the following on the PPA site...

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iQCVAwUASgmnlWDREhckfRz/AQL4WwP+OqxGOREWH/a6u/JfGRHZPMBC65dD+ufZ
YWtghqO/QIsIWgU1jaGbgwqUn1Nj9Hkq9GBTfAknETewd59GDa8BiHJTATZrvaKZ
kqs16Gucqd+41n9JtdwtcZVYkI9vIS3lT6Jc2ryeSLcsj5IbvJd9HW6Fgjo0Xdrm
4TagQ5KkuFU=
=aFvm
-----END PGP SIGNATURE-----

My attempts to save this using KATE were successful but I can not get the key to import using the software sources applet as the help site suggests.  Every time I try to add the key by navigating to the text file I saved nothing happens.

Is there some kind of format or ending that is expected of this file to work for import?  Forgive me, but from my windows experience it may need a 'ending' to be recognized as a 'key' file.

Thanks
CB

---

### Post by CBHedricks on 2009-05-23
Ok.. got fed up with the whole non-authenticated mess... Removed the PPA that I had for OpenOffice and went with the OpenOffice PPA Scriblers that more closely follows the PGP and PPA guidelines from the examples and it worked.

The URL: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
The source: deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
  (Replace "hardy" with your version name - jaunty, intrepid)

The page as shown in the site I provied by URL more closely follows the video showing how to install the sources and the key.

I removed the other PPA source replaced it with scriblers source and used the copy / paste method to create a text document of the GPG key - installed it as specified and then perfomed partial update.  No errors - removed one package and installed 19 others.

OpenOffice files are updated, additional packages installed and now I do not have the bothersome updates are ready indicatory constantly showing on the top bar.

Thanks for the assistance (with patience) in getting me pointed in the right direction.

CB

---

