---
title: "Upgrading Software"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-01-22
Hey all,

It's been manifested to me that I am in dire need of upgrading one of my programs (specifically, MuseScore), but I can't for the life of me figure out how to get the newest stable version. I am running Jaunty 64bit.

When I go to Applications > Add/Remove and try to install mscore, it says it's already installed.  So I've typed ```
sudo apt-get remove
``` and retried from Add/Remove, but I get the same version.  I've done the same thing with "purge".

I've tried installing the .deb file of the package from SourceForge, and it appeared to install successfully (I did this while 0.9.4 was still installed).  I then clicked on MuseScore under Applications, but 0.9.4 still started up (except this time with errors that say ```
Error loading plugin
usr/share/mscore-0.9/plugins/tuning.js line 30:
ReferenceError: QColor is not defined
```((I also got one for "colorstones.js"))

Then I "sudo apt-get remove"'d mscore again, and reinstalled the 0.9.5 .deb package.  MuseScore was not listed under Apps > Sound/Video, and was not recognized by typing "mscore" in the Terminal.

I went to the MuseScore website and a link said "There are ready-to-install packages for Ubuntu 8.04+ in the "universe" repository, and for 7.10 in the "universe" Backports repository. The packages provided are often older versions than the current stable version.Please consult your favorite package manager for the "mscore" package, or click [here to install directly from your browser]("http://musescore.org/apt")."  I don't know what the former half of that means, but clicking there to install directly from my browser sounded easy enough, so I clicked it, but I got an alert saying that "mscore was already installed on this system" when MuseScore was installed (I thought it would have upgraded).  

I just tried it again with MuseScore NOT installed, and it looked like it went through the correct motions of installing it, but when I opened it, lo and behold, 0.9.4 haunts me yet again with the same errors as above.

I am at a complete and utter loss of how to upgrade to 0.9.5.  Please assist. T____T;

---

### Post by Wataru8675 on 2010-01-22
Oh, I forgot ONE MORE thing I tried. @_@

I went to System>Administration>Synaptic Manager and found the mscore packages.  I clicked on the box next to them and saw an option "mark for upgrade," but it was greyed out...  My only options were to reinstall or remove.

---

### Post by myth1914 on 2010-01-22
If you are seeing the upgraded version of the package, I would assume the repository is enabled.  Have you run an apt-get update after purging the old version?  Then apt-get install?

---

### Post by Wataru8675 on 2010-01-22
I purged mscore, updated, and re-installed mscore.  I'm still getting v 0.9.4 with the same errors listed.

---

### Post by halitech on 2010-01-22
I did a little digging and found this in the Ubuntu Stable info on the download page:
```
The packages provided are often older versions than the current stable version
```

If you want the latest, look here:

[https://launchpad.net/~mscore-ubuntu/+archive/ppa](https://launchpad.net/~mscore-ubuntu/+archive/ppa)

warning from their site:
> You can update your system with unsupported packages from this untrusted PPA by adding ppa:mscore-ubuntu/ppa  to your system's Software Sources

---

### Post by Wataru8675 on 2010-01-22
v 0.9.5 should be stable by now...  I mean, it's the one that they advertise on their website (if you go to musescore.com and look at the top, there's a big box to download it, and it's on almost every page), plus someone on the MuseScore forum told me to download it, and it was a pretty hands-down answer.  I'll try this, but there should be some way I should be able to legitimately update it, shouldn't there? >.o?

---

### Post by Wataru8675 on 2010-01-22
And, also, Halitech... Which of the 25 packages do I download? @_@?  I don't know what any of the package names mean...

---

### Post by halitech on 2010-01-22
Generally, developers will have a newer version then what is in the repos due to the testing that Ubuntu because they want to make sure it is stable for Ubuntu users. If MuseScore released their latest version too late for Ubuntu to test it properly then it will stay as v0.9.4 until Ubuntu 10.04 comes out.

If you follow the info in the link I provided, it will show how to get the updated version direct from MuseScore.

---

### Post by thunk77 on 2010-01-22
Hello,

(This is an optional step, i prefer doing it like this so as to keep things clean!)

First of all go to Synaptic and completely remove the application (Mark for Complete Removal)
Remove all versions of the program including the ones you installed manually. Then look for any related packages on the left pane (Automatic Remove). Purge them also.

(Adding Repositories is kinda tricky especially if you haven't done so before, so if you don't feel comfortable about doing something, ask first and don't do hasty moves)

Go to:

[HTML]https://launchpad.net/~mscore-ubuntu/+archive/mscore-stable[/HTML]

First navigate the page. See what you can understand from it. Look around. Maybe you won't need help at all ;)

click on "Not using Ubuntu 9.10 (Karmic)?"
Extra info will be displayed. Choose from the dropdown box "Jaunty 9.04"

Open "Software Sources" from the menu (System - Administration - Software Sources)
Go to the tab "Third Party Software". Click on "Add"

Copy the first line of the PPA. You'll find it is:

```
deb http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu jaunty main
```

Then repeat once again for the second line:

```
deb-src http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu jaunty main
```

Then you have to import the key.

open a terminal and enter

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3A258030
```

It will return sth like key imported..so you can skip the next step

ALTERNATIVE METHOD (A lot more time consuming:)

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESd3qDQEEAKqv5Ue0pr/euRACUv3YOrSY4gO5lycirpmjvatOQr+LEjgG8jbKn6ei5O2g
6MqvITKt4G2Y1pJomEFaxnqQbr7hUUiSR7zn8pRTvuiq1rIdiMg5Iw61tFo08QVSzLAuurkO
J+ucfrM9nHYf9vsl+SGfDtqaClgJunuuVdpfuXOrABEBAAG0O0xhdW5jaHBhZCBQUEEgbmFt
ZWQgbXNjb3JlLXN0YWJsZSBmb3IgTXVzZVNjb3JlIE1haW50YWluZXJziLYEEwECACAFAknd
6g0CGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRCPZgUaOiWAMFkRA/sHVu9v/sUe6ex7
8emFDUEtZYbxJpFWgtFiGD0WAR753CMGlgbmeKvgHtcTGCeBP47Q5bU4+/K5f7g1DInuF76r
WM6RmvdyQJ7rhJu0ry2LF3seb3K8sjlg/YzJxpO6aemcbZ885WBg5VCllqMOk+VSS3O9Z/nJ
o9/tmdqqjoK5dA==
=MCVQ
-----END PGP PUBLIC KEY BLOCK-----
```

Copy the above to your text editor and save it on your desktop as mscore.key

Then on Software Sources click on the "Authentication" tab and then click on the "Add Key" button.

Navigate to your desktop (/home/Username/Desktop) and import the file you created previously (mscore.key) and hit close

It will ask you to update the repositories, so update!

After all this you can once again fire up synaptic and install the application again. I think you will find the version is 0.9.5

Voila!

---

### Post by Wataru8675 on 2010-01-22
Da ha!  Thank you Thunk77. @_@  I haven't used Synaptic until now, but now that I've got a handle on how it works a little bit, I should be set for any future needs.

Thank you thank you thank you thank you thank you. :D

---

### Post by thunk77 on 2010-01-22
Cool :) 

Glad I could help

Regards

---

