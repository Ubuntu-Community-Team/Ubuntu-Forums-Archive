---
title: "kdm or gdm (or xdm) for minimal install CD of ubuntu"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-11-17
Greetings,

I'm experimenting with using the minimal install CD to install ubuntu 9.04 on my dell mini 9 (9.10 has problems with my wireless driver that I know how to fix with the full install, but not with the minimal. I'll try that at a later time).  I'd like to install XFCE and Firefox and install applications as I need them instead of having a lot of programs installed for me that I don't need or can't even use (such as anything involving CDs or DVDs - the netbook doesn't have a drive).

I know a lot of people will just think "well, uninstall the programs...", but I'm trying to install as little as possible to both maximize my tiny hard drive space (16 GB solid state drive) and preserve my limited CPU power (Intel Atom with a gig of RAM), as well as avoiding the amount of time it takes to go through each program and uninstall it separately.

Any ideas on which display manager I should use, and why you would choose it?

Thanks,
Red

---

### Post by Simian Man on 2009-11-17
I'd recommend SLim but, unfortunately, I heard Ubuntu ditched it from the repos.  It is simple, light, and easy to theme.

---

### Post by Redmage913 on 2009-11-17
Also, is there anything I need to keep in mind when manually installing every program instead of using an application suite like Xubuntu?

---

### Post by decoherence on 2009-11-17
> **Simian Man said:**
> I'd recommend SLim but, unfortunately, I heard Ubuntu ditched it from the repos.  It is simple, light, and easy to theme.

Oh my god, so they did! Damn I loved Slim.

---

### Post by Bjalf on 2009-11-17
SLiM.

I use this script after a CLI only install from the alternate CD:
```
#!/bin/sh

gui=xorg
de="xfce4-session xfdesktop4 xfce4-panel xfce4-utils xfce4-settings xfce4-mixer xfce4-datetime-plugin"
wm="xfwm4 xfwm4-themes"
themes="gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-xfce xfce4-icon-theme tango-icon-theme tango-icon-theme-common"
guiutils="menu gksu synaptic xfce4-terminal mousepad software-properties-gtk thunar thunar-volman"
utils="galculator tuxcmd tuxcmd-modules"
web="firefox thunderbird"
games="aisleriot gnome-mahjongg glchess gnomine glines gnobots2 same-gnome gnometris gtali gnotski"
sound="alsa-base alsa-utils"
misc=
slim=slim_1.3.0-2_i386.deb

sudo aptitude update
sudo aptitude -y safe-upgrade

sudo aptitude -y install --without-recommends $gui $de $wm $themes $guiutils $utils $web $games $sound $misc

if test ! -d ~/install
then
    mkdir ~/install
fi
if test ! -e ~/install/$slim
then
    cd ~/install
   wget http://mirrors.kernel.org/ubuntu/pool/universe/s/slim/$slim
fi
sudo dpkg -i ~/install/$slim 2>&1 | sed -n 's/[ ]*Package \([^ ]*\) is not installed\./\1/p' | sed -e :a -e 'N;s/\n/ /;ta' > ~/install/slimdepends
if test -s ~/install/slimdepends
then
    sudo aptitude -y install --without-recommends `cat ~/install/slimdepends`
    sudo dpkg --configure slim
fi
sudo dpkg --configure -a
```

---

### Post by Redmage913 on 2009-11-17
Forgive me, I should have clarified that I am not all that proficient when dealing with command-line, and have no idea how to use scripts.

Should I copy that script to my thumbdrive, copy it over (i'm guessing to the home directory?), and execute it?

I'm sorry for asking, but I would need more detail before I could carry out the script involving SLiM.

---

### Post by Bjalf on 2009-11-17
If you just want SLiM installed, then this script will do the trick:```
#!/bin/sh

slim=slim_1.3.0-2_i386.deb

[B]cd ~
[/B]wget http://mirrors.kernel.org/ubuntu/pool/universe/s/slim/$slim
sudo dpkg -i ~/$slim 2>&1 | sed -n 's/[ ]*Package \([^ ]*\) is not installed\./\1/p' | sed -e :a -e 'N;s/\n/ /;ta' > ~/slimdepends
if test -s ~/slimdepends
then
     sudo aptitude -y install --without-recommends `cat ~/slimdepends`
     sudo dpkg --configure slim
fi
```Save the script as *whatever.sh* and run it with ```
sh whatever.sh
``` or give it execute permissions and run it with ```
./whatever.sh
```Run it from your home directory, I think it can be run from anywhere you have write permissions.

The shell gets the SLiM package with wget, tries to install with dpkg, installs any missing packages that slim depends on (saved in the file *slimdepends*), and then configures slim.

The rest was just to install xorg, xfce and lots of other programs.

Edit:
The SLiM package is actually from Jaunty: [http://packages.ubuntu.com/jaunty/slim](http://packages.ubuntu.com/jaunty/slim)
Because it is installed with dpkg, it could well happen that dpkg spews error messages about missing packages that slim depends on. The very long line with sed constructs takes those error messages and orders them nicely for use with aptitude.

Whoops, missed a *cd*.

---

### Post by Redmage913 on 2009-11-17
Well, I'm installing 9.04 Jaunty, so shouldn't it still be in that repository? Do I still need the script?

---

### Post by Bjalf on 2009-11-18
> **Redmage913 said:**
> Well, I'm installing 9.04 Jaunty, so shouldn't it still be in that repository? Do I still need the script?
Oops, I missed that when I read your post  :oops:

I believe that SLiM is still in the old repos, they just dropped it from Karmic.
Just install it with ```
sudo aptitude -y install --without-recommends slim
```

---

