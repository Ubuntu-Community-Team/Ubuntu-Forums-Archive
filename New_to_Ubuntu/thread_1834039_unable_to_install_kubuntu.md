---
title: "unable to install kubuntu"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by idom on 2011-08-26
I have 10.04 LTS and I want to try out kde now.

I tried to follow 

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) 

and it failed to install kde saying some packages cannot be installed 

screen shot is attached.

idom

---

### Post by LowSky on 2011-08-27
okay?

install it from the terminal, if it will not install it will list the packages that are a problem

```
sudo apt-get install kubuntu-desktop
```

---

### Post by idom on 2011-08-27
> **LowSky said:**
> okay?

install it from the terminal, if it will not install it will list the packages that are a problem

```
sudo apt-get install kubuntu-desktop
```

I tried that and it did not work. 

it gave following messages. 

Thanks for your help

idom 

idom-desktop:~> sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
                   Depends: kde-zeroconf but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: phonon-backend-xine but it is not going to be installed
                   Depends: plasma-desktop but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: apport-kde but it is not going to be installed
                   Recommends: apturl-kde but it is not going to be installed
                   Recommends: dragonplayer but it is not going to be installed
                   Recommends: freespacenotifier but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: hpijs-ppds but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: k3b but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kbluetooth but it is not going to be installed
                   Recommends: kcalc but it is not going to be installed
                   Recommends: kcm-gtk but it is not going to be installed
                   Recommends: kcm-touchpad but it is not going to be installed
                   Recommends: kdebase-plasma but it is not going to be installed
                   Recommends: kdegraphics-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-kresources but it is not going to be installed
                   Recommends: kdepim-runtime but it is not going to be installed
                   Recommends: kdepim-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdesudo but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kopete but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kpackagekit but it is not going to be installed
                   Recommends: kppp but it is not going to be installed
                   Recommends: krdc but it is not going to be installed
                   Recommends: krfb but it is not going to be installed
                   Recommends: ktimetracker but it is not going to be installed
                   Recommends: ktorrent but it is not going to be installed
                   Recommends: kubuntu-firefox-installer but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: kubuntu-notification-helper but it is not going to be installed
                   Recommends: kvkbd but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: network-manager-kde but it is not going to be installed
                   Recommends: okular-extra-backends but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: plasma-widget-facebook but it is not going to be installed
                   Recommends: plasma-widget-kimpanel but it is not going to be installed
                   Recommends: plasma-widget-kubuntu-feedback but it is not going to be installed
                   Recommends: plasma-widget-message-indicator but it is not going to be installed
                   Recommends: plasma-widget-quickaccess but it is not going to be installed
                   Recommends: plasma-widgets-addons but it is not going to be installed
                   Recommends: printer-applet but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: usb-creator-kde but it is not going to be installed
                   Recommends: userconfig but it is not going to be installed
E: Broken packages
idom-desktop:~>

---

### Post by sam_delta on 2011-08-27
Try going into system > administration > software sources, make sure that at least main and universe are checked.

Then in a terminal type the following 2 commands:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

let us know if the problem persists
sam

---

### Post by jerrrys on 2011-08-27
to the OP

i wonder if a sudo apt-get update and/or changing download source would do anything.

---

### Post by idom on 2011-08-27
I tried and it gave the same error.

it is attached in text file.

idom

> **sam_delta said:**
> Try going into system > administration > software sources, make sure that at least main and universe are checked.

Then in a terminal type the following 2 commands:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

let us know if the problem persists
sam

---

### Post by sam_delta on 2011-08-27
try updating your system with```
sudo apt-get upgrade
``` , also try ```
sudo apt-get dist-upgrade
```

try installing kubuntu-desktop after those upgrades

tell us how it goes
sam

---

### Post by idom on 2011-08-27
> **sam_delta said:**
> try updating your system with```
sudo apt-get upgrade
``` , also try ```
sudo apt-get dist-upgrade
```

try installing kubuntu-desktop after those upgrades

tell us how it goes
sam

Thanks for your help , however it did not help. 

sudo] password for idom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
idom-desktop:~> sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and after that it gave the same error

---

### Post by idom on 2011-08-27
Can anybody check if my sources.list is correct 

deb     [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe



deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

does kbuntu need some changes in this ? 

idom
> **idom said:**
> Thanks for your help , however it did not help. 

sudo] password for idom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
idom-desktop:~> sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and after that it gave the same error

---

### Post by kyletstrand on 2011-08-27
Since the dependencies are not met, you could try to build up from the bare minimum and get to the full desktop.  It's a shot in the dark, but it might be worth a shot.

```
sudo apt-get install kde-core
sudo apt-get install kde
sudo apt-get install kubuntu-desktop
```

Try that and see if the errors go away or change.  It KDE-core doesn't install, no sense trying the others.

---

### Post by kyletstrand on 2011-08-27
This is probably a dumb suggestion, but it might not hurt to check.

If you go to your GUI update manager, is there anything in there?  If so, update from there, reboot, and try installing the kubuntu-desktop again.

---

### Post by idom on 2011-08-28
> **kyletstrand said:**
> Since the dependencies are not met, you could try to build up from the bare minimum and get to the full desktop.  It's a shot in the dark, but it might be worth a shot.

```
sudo apt-get install kde-core
sudo apt-get install kde
sudo apt-get install kubuntu-desktop
```

Try that and see if the errors go away or change.  It KDE-core doesn't install, no sense trying the others.

hey I tried couple of things. I commented chrom related repository from my sources.list and I tried

sudo aptitude install kubuntu-desktop 

and it did start properly and now I can run kde

---

### Post by kyletstrand on 2011-08-28
Yay!

---

