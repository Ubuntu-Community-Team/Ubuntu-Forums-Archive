---
title: "dpkg returned error code (1)"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by ingo on 2006-11-25
Hi,

I did something very clever ](*,) in that I farted around with a few firewalls available through the repositories. All of a sudden ssh wouldn't work anymore so I removed them again. ssh still didn't work. So I removed everything they left behind, in particular /etc/fiaif/

I then came across firestarter and thought it had my name written all over it. Well, it tried to install fiaif as well and adept of course then told me that the installation would not work. So I turned to the shell and on manual install of fiaif I get the following:

> Errors were encountered while processing:
 fiaif
E: Sub-process /usr/bin/dpkg returned an error code (1)
ingo@dicker:~$
I tried apt-get install -f, apt-get upgrade, apt-get remove fiaif, apt-get autoremove, apt-get clean and I don't know what else. I think adept tells me it needs that /etc/fiaif folder (which I successfully got rid off so that ssh would work again, which it does).

Now I have a non-perfect system and am still without a firewall. I googled error code (1) but got stuck. Anybody out there with a clue to what is going on? 

Pointers to which way to turn much appreciated.

Cheers

---

### Post by Spano on 2006-11-25
I would try 
```
sudo apt-get --purge remove fiaif firestarter
```
then 
```
sudo apt-get install firestarter
```
which should also pull in fiaif as a dependency.
You could also try opening Synaptic > Edit > Fix Broken Packages

---

### Post by ingo on 2006-11-25
Nice one spano! that did the trick. I was trying to make sense of the man apt-get page, especially the purge command but couldn't get it to work.


Thanks a lot for your help!

---

### Post by Spano on 2006-11-25
Excellent. Where is the Capitol of Beer?

---

### Post by ingo on 2006-11-25
munich :)

---

### Post by Matt Heath on 2006-12-09
Hi I'm also getting this error code, and trying to do the above isn't helping.  When i enter "apt -f install" i get the following:
```
matt@matt-heath:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts libthai0
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7932kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103953 files and directories currently installed.)
Preparing to replace firefox 1.5.dfsg+1.5.0.3-0ubuntu3 (using .../firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mozilla-firefox', which is the diverted version of `/usr/bin/mozilla-firefox'
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
So I tried 
```
matt@matt-heath:/var/cache/apt/archives$ sudo apt-get --purge remove  /var/cache /apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package

```
and ```
matt@matt-heath:/var/cache/apt/archives$ sudo apt-get --purge remove firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb

```
Which couldn't find the file. So I tried
```
matt@matt-heath:/var/cache/apt/archives$ sudo apt-get clean

```
Which removed the .deb file that seemed to be causing the trouble. But when I ran```
 sudo apt-get -f install 
``` again, it had the same output as before and recreated the .deb.

The same error one message comes up if i try to install updates with synaptic. Also doing either of these causes the problem I had [here]("http://ubuntuforums.org/showthread.php?p=1862682#post1862682") to re-emerge. 
PLease can someone help me.

---

### Post by ingo on 2006-12-09
Just checked your other thread and it seems pretty adventurous!

A good way of finding out about where and which packages are on your box is "locate". First bring your database up to date with 

sudo updatedb

That'll take a while. Then do

locate firefox

The output should put some light on what is where on your box and which packages you should purge. Personally, I would remove all traces of firefox from your system (apart from what is in your home directory), install from here [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/) a

HTH

---

### Post by Matt Heath on 2006-12-09
:cry: I'm horribly out of my depth. I ran "locate" and it gave a HUGE list of firefox places. Whenever I tried to purge or remove any part of it it said i couldn't because yelp and  gnome-app-install depend on firefox. So I purged yelp and gnome-app-install and then firefox and tried to re-install firfox with this [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) script. 
But part way through it went wring and gave me ```
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mozilla-firefox', which is the diverted version of `/usr/bin/mozilla-firefox'
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on firefox; however:
  Package firefox is not installed.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on firefox (>= 1.5); however:
  Package firefox is not installed.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on firefox; however:
  Package firefox is not installed.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 1.5.dfsg+1.5.0.8-0ubuntu0.6.06); however:
  Package firefox is not installed.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 yelp
 ubuntu-desktop
 firefox-gnome-support
Previous command did not complete successfully. Exiting.

```

---

### Post by Matt Heath on 2006-12-09
FIXED! i ran "uninsall" script from her then installed again and it seems fine

---

### Post by troseph on 2007-06-30
Ok.. I am getting something along the same lines that is frightening. When I install any application or library I get the following:
```

Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tristandoyle on 2008-06-02
I use a Dell Inspiron 710m

When I try to install or update packages I encounter this error:

sudo apt-get install avidemux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
avidemux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-applets-data (2.22.2-0ubuntu1) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-panel-data (1:2.22.2-0ubuntu1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.22); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.23); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up eog (2.22.2-0ubuntu1) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.22.2-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.22.1.1-0ubuntu3) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.22.2-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gdm (2.20.6-0ubuntu2) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.22.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.22); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.23); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gnome-applets-data
 gnome-panel-data
 gnome-panel
 gnome-applets
 eog
 evince
 evolution-common
 f-spot
 file-roller
 gcalctool
 gdm
 gedit-common
 gedit
 seahorse
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

