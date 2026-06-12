---
title: "Nothing appears after ading Software Source!"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-24
I had a repository entered ([the jaunty ones linked here]("https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive")) from my isp.

They semed to be failing so I deleted them and re-added them by adding the correct ATP path **but** they don't appear in the **Third Party Software** tab of **Software Sources** after I add them.

They seem to work when I close and reload (when prompted) as the iinet entries say either **hit** or **done** in the report.

When I go to add Applications and choose **Third Party** (not Canonical) the list just shows up blank. Under **Origin** in Synaptics, there doesn't appear to be an iinet listing either. I am assuming it would show up there if it worked.

Any ideas?

---

### Post by pytheas22 on 2009-04-24
Whenever you update your sources list, you need to run this command for the changes to take effect:
```

sudo apt-get update
```

(This is the same command that gets run when you see the graphical prompt about reloading the sources list.)  Give that a try and see if it helps.  If it still doesn't work, please post the output of:
```

cat /etc/apt/sources.list
```

---

### Post by smileyguy on 2009-04-24
Something seemed to happen when i ran [FONT=monospace]
[/FONT]sudo apt-get update
and the output was:[FONT=monospace]
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) jaunty Release.gpg
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) jaunty/main Translation-en_AU                     
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) jaunty Release                                    
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) jaunty/main Packages                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release.gpg     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty-security/multiverse Sources
Reading package lists... Done

[COLOR=Red]**which seemed to show the correct iinet source** but it still didn't appear under **Software Sources**.

The second command resulted in output below which again seems to show what I want - just doesn't appear in the **Software Sources** gui. I'll restart to double check but have done that before![/COLOR] 

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty restricted main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security restricted main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) jaunty main
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) jaunty main
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) jaunty main
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) jaunty main

[/FONT]

---

### Post by pytheas22 on 2009-04-24
hmmm, it looks like the extra repositories exist in your sources list correctly (I'm assuming it's the iinet.net.au stuff).  Perhaps it's just a bug with the GUI application.  Are you able actually to install packages from the third-party repositories, even though they don't appear in the GUI?

---

### Post by smileyguy on 2009-04-25
Under Applications ? Add Remove I can install them from the **Canonical Maintained** **Applications** but when I choose B Third Party Applications it seems to be blank, even after restarting Add/Reomve Apps

If I change it back to Canonical and restart it then the canonical ones appear.

---

### Post by pytheas22 on 2009-04-25
Try using Synaptic Package Manager (under System>Administration) to install your packages.  You don't need to specify a repository in Synaptic; it will search all repositories by default.  Can you find your package there?

If not, please let me know what exactly you're trying to install and what kind of computer you have (32-bit or 64, and which version of Ubuntu) and I'll see if it works on my machine.  It's possible that there's a problem with the repository itself.

---

### Post by smileyguy on 2009-04-26
Not trying to install anything in particular, just trying to see what's in that repository as it doesn't count as part of my download (provided by my isp). It's getting to "that time" of the month for download limits and I thought it a good way to experiment with packages.

---

### Post by pytheas22 on 2009-04-26
I added that repository and can't find any packages in it either.  It's possible that it doesn't contain anything or that there's some other problem, I guess...

---

### Post by EmilyRose on 2009-04-29
I'm having a similar problem - the only software/applications listed in add/remove are the basic open-source ones available. Absolutely NO third party apps at all. I have the following listed & checked in system/administration/software sources/third party:


[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[http://planet76.com/repositories/](http://planet76.com/repositories/) ./
[http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
[http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main (Source)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) Jaunty free non-free

I also have all the boxes checked under "Ubuntu Software" and am downloading from the Main Server... 

Now, they are indeed available via synaptic package manager, but its a much more bulky program to try and sort through and find new apps to try. Yes, if I know I want/need to download X I can get it, but if I'm just looking for a new game or something, its a PITA...

---

### Post by pytheas22 on 2009-05-02
**EmilyRose**: since Synaptic doesn't have this problem, it's possible that it's a bug in the Add/Remove Programs application (the binary is called 'gnome-app-install').  You may want to [file a bug report]("https://help.ubuntu.com/community/ReportingBugs").

---

