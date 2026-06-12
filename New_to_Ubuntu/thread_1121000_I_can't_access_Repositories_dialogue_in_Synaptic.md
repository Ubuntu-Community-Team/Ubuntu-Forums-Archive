---
title: "I can't access Repositories dialogue in Synaptic"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by camaron1 on 2009-04-09
Hay guys, I hope you can help here. 

I followed this instructions from *Ubuntu Kung fu* in order to speed up my computer:
I installed **prelink** and pasted in the terminal:

gksu gedit /etc/default/prelink

Right after this I went to **Synaptic**, to Settings and then Repositories to add a new one and I can't access the Repositories dialogue, It just doesn't open. Following the author advise (in case something went wrong) I backtracked by pasting in the terminal:

sudo prelink -ua

and uninstalled **prelink**. Still nothing happened. Then I reinstalled **Synaptic** and still the same.
Please help!!

I'm on Intrepid 64 bits****

---

### Post by taurus on 2009-04-09
Can you modify /etc/apt/sources.list with a text editor?

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by FreewheelinFrank on 2009-04-09
I had a similar problem after an update. I removed some packages that synaptic said were no longer necessary, then could not access Settings>Repositories.

I had to reinstall a package. I can't remember what it was now, but I think it must have been software-properties-gtk.

Check that that one is installed in synaptic.

---

### Post by camaron1 on 2009-04-09
> **taurus said:**
> Can you modify /etc/apt/sources.list with a text editor?

```
gksudo gedit /etc/apt/sources.list
```

Yes I checked that and it is fine, but it is not good enough obviously, plus I can't change what kind of updates i wan't (universe, multiverse...)

---

### Post by camaron1 on 2009-04-09
Anyone there?

---

### Post by camaron1 on 2009-04-10
I'm still hoping someone could help me here....

---

### Post by drs305 on 2009-04-10
Can you successfully run:
```

sudo apt-get update

```
Post any error messages.

Can you access the Repository list via System, Administration, Software Sources?

You might try uninstalling the app completely with:
```

sudo apt-get purge prelink

```

---

### Post by camaron1 on 2009-04-10
Thank DRS 305 for answering:

sudo apt-get update gives this message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

This didn't happen before.

And no, I can't access Software sources via Administration (though I have to admit that I didn't even think of it

Any idea?

---

### Post by camaron1 on 2009-04-10
Sorry, forgot to say that I ran sudo apt-get purge prelink but still the same

---

### Post by drs305 on 2009-04-10
You can add that key by running the first command, then run the apt-get commands again. The first commands add the security key that launchpad introduced a month or so ago as an added security feature to protect the packages they maintain.
```

gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220 
gpg --export --armor 6AF0E1940624A220  | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade

```

It appears that APT may be working, just not the gui upgrade system, since all you got was the key error and not more. Let us know what happens when you run upgrade. You might try reinstalling synaptic via command line if apt works:
```

sudo apt-get install --reinstall synaptic

```

---

### Post by oldos2er on 2009-04-10
You can ignore the GPG error for now; it shouldn't interfere with any package manager functions.

 Can you run
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```
in a terminal, and post the output here?

---

### Post by camaron1 on 2009-04-10
> **drs305 said:**
> You can add that key by running the first command, then run the apt-get commands again. The first commands add the security key that launchpad introduced a month or so ago as an added security feature to protect the packages they maintain.
```

gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220 
gpg --export --armor 6AF0E1940624A220  | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade

```

It appears that APT may be working, just not the gui upgrade system, since all you got was the key error and not more. Let us know what happens when you run upgrade. You might try reinstalling synaptic via command line if apt works:
```

sudo apt-get install --reinstall synaptic

```

The key is imported, synaptic reinstalled and everything the same but after running:


*gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk*

the output seems to say something (but not for me, obviously):
[I]
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet  warnings.warn("apt API not stable yet", FutureWarning)
reWarning: apt API not stable yetTraceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateExcept[/I]ion

What is that *distribution template*?

---

### Post by oldos2er on 2009-04-10
What about the output for
```
gksu /usr/bin/software-properties-gtk
```
?

---

### Post by camaron1 on 2009-04-10
> **oldos2er said:**
> What about the output for
```
gksu /usr/bin/software-properties-gtk
```
?

This is it:
[I]
Traceback (most recent call last):
t/__init__.py:18: FutureWarning: apt API not stable yet
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException


[/I]

---

### Post by camaron1 on 2009-04-10
Anyone there able to help?

---

### Post by oldos2er on 2009-04-10
Can you post the output of
```
cat /etc/apt/sources.list
```
?

---

### Post by camaron1 on 2009-04-11
> **oldos2er said:**
> Can you post the output of
```
cat /etc/apt/sources.list
```
?

[PHP]# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081030)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://philip.magicalforest.se/ intrepid extra
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu intrepid main
# deb http://ddeb http://deb.opera.com/opera/ stable non-freeeb.opera.com/opera/ stable non-free
# deb http://deb.opera.com/opera/ stable non-free
# deb http://ppa.launchpad.net/do-testers/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main
deb http://debian.vogelweith.com/ intrepid zgegthemes # Themes of ZgegBlog
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main[/PHP]

Hope it helps

---

### Post by camaron1 on 2009-04-11
Ideas?

---

### Post by drs305 on 2009-04-11
> **camaron1 said:**
> Ideas?

I ran your sources.list and it worked fine.

There was a bug reported earlier in software-properties, so I would try to reinstall it:
```

sudo apt-get install --reinstall software-properties-gtk
``` 
That command updated my software-properties-gtk file and could very well fix your problem.

---

### Post by camaron1 on 2009-04-11
Thanks DRS 305 
I'll do that as soon as I get home from work tonight. I hope it helps

---

### Post by oldos2er on 2009-04-11
This has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+bug/292691](https://bugs.launchpad.net/ubuntu/+bug/292691)

---

### Post by camaron1 on 2009-04-12
> **drs305 said:**
> I ran your sources.list and it worked fine.

There was a bug reported earlier in software-properties, so I would try to reinstall it:
```

sudo apt-get install --reinstall software-properties-gtk
``` 
That command updated my software-properties-gtk file and could very well fix your problem.

Unfortunately it didn't work.


> This has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+bug/292691](https://bugs.launchpad.net/ubuntu/+bug/292691)

The description of the bug is not really quite the same but the actual output of running ***sudo software-properties-gtk*** is, so if it is just a bug after all I suppose there isn't an awful lot I can do. Anyway, If someone sugests me to try something els I'll be glad to try. If no, I'll have to live with it.

---

### Post by WildSioux on 2009-05-13
I had the same error on LinuxMint 7 RC1 (using Jaunty 9.04).  I installed it and had everything running perfectly.  But since I prefer KDE over Gnome, I installed the kubuntu-desktop and removed gnome.  Somewhere along the line, synaptic was removed (the command I used was from here)
> Remove Ubuntu (I copied all of that first code)
[http://psychocats.net/ubuntu/purekde]("http://psychocats.net/ubuntu/purekde")

Restarted and found a few things like synaptic, firefox, and not sure what else now was gone.  So I reinstalled them.  This is where I found that I was unable to open the "Repositories" window in Synaptic.  I clicked on it in the "Settings" tab at the top, it flashed but nothing opened.

I found this thread and reinstalled Synaptic.  I removed "software-properties-gtk" and before I reinstalled it I just tried the "Repositories" again and it OPENED!  However, installing it causes the repositories to not open.

So for me, removing "software-properties-gtk" made it so the repositories window opened.

I don't know what that package does but I don't need it.

---

### Post by DodgingGrunge on 2011-01-08
> So for me, removing "software-properties-gtk" made it so the repositories window opened.

For what it is worth, I was experiencing the same issue with Synaptic in CrunchBang and removing software-properties-gtk resolved it for me as well.

---

