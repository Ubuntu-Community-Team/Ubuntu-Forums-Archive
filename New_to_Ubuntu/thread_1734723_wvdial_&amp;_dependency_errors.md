---
title: "wvdial &amp; dependency errors"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-20
I downloaded the deb package for gnome-ppp (for Ubuntu 10.4), copied it to the desktop, double clicked to install and got this message:

[COLOR=#ff0000]Error: Dependency is no satisfiable: wvdial[/COLOR]

Then I downloaded the deb package for wvdial (for Ununtu 10.4) copied it to the desktop, double clicked it and got this message:

[COLOR=#ff0000]Error: Dependency is no satisfiable: libuniconf4.6[/COLOR]
 
How do I go about getting all of the dependencies to make gnome-ppp work and how and in what order to I install them . . . or am I barking up the wrong tree? Thank you again for your help

---

### Post by mörgæs on 2011-04-20
[http://ubuntuforums.org/showpost.php?p=10697032&postcount=7](http://ubuntuforums.org/showpost.php?p=10697032&postcount=7)

---

### Post by jtarin on 2011-04-20
> **TCMGO said:**
> I downloaded the deb package for gnome-ppp (for Ubuntu 10.4), copied it to the desktop, double clicked to install and got this message:

[COLOR=#ff0000]Error: Dependency is no satisfiable: wvdial[/COLOR]

Then I downloaded the deb package for wvdial (for Ununtu 10.4) copied it to the desktop, double clicked it and got this message:

[COLOR=#ff0000]Error: Dependency is no satisfiable: libuniconf4.6[/COLOR]
 
How do I go about getting all of the dependencies to make gnome-ppp work and how and in what order to I install them . . . or am I barking up the wrong tree? Thank you again for your help

Use the package manager Synaptic....that's  what it's for.

---

### Post by lkraemer on 2011-04-20
You are making this way too hard......

You need to download wvdial, and the following dependencies for 10.04,
or whatever version you have installed......and get the 32 or 64 bit debs
to match your installed version.......then install via Synaptics........
realizing you don't have Ethernet or Wifi.....available yet on Ubuntu and
are trying your best to get wvdial installed and configured to get Dialup Working......

wvdial & dependencies:  (ALL are .deb files)
```

libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

```

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive, & then to Ubuntu subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```

**OR** you can go to **SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES**
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install wvdial from the CDR.

**ZIT ZOT!  What was so hard?**


OH, forget trying Gnome-PPP until you get wvdial working..........
REF:  [http://ubuntuforums.org/showthread.php?t=1734651&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1734651&highlight=wvdial)


And Posting #2 here:
[http://ubuntuforums.org/showthread.php?t=1727388](http://ubuntuforums.org/showthread.php?t=1727388)

would have led you to Posting #3 here:
[http://ubuntuforums.org/showthread.php?t=1634580&highlight=dial+modem+setup](http://ubuntuforums.org/showthread.php?t=1634580&highlight=dial+modem+setup)

which would have led you through the complete process, that you will/should now start.

Good DETAILED instructions are easy to find.......FOLLOWING them is HARD!

In 15 minutes you will be online......Good Luck!

lk

---

