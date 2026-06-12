---
title: "quick ubuntu-minimal question"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by earthpigg on 2008-12-03
if i do a clean install, and just choose ubuntu-minimal... and then do sudo apt-get ubuntu-desktop, will that accomplish **exactly **the same thing as installing ubuntu normally?

or would that even work? will ubuntu-minimal detect my network and connect, etc?

for the sake of learning, if i wanted to go from ubuntu-minimal to a full fledged gui desktop what steps would i need to take?

---

### Post by skymera on 2008-12-03
Yes.

Ubuntu Desktop will install everything that a standard install has.

I'd too like to know how to get to a basic GNOME desktop.
I believe you'll need xserver, gnome-core and some others.

---

### Post by earthpigg on 2008-12-03
thanks, skymera.

it would be interesting and educational to go from ubuntu-minimal to ubuntu-desktop by taking baby steps.

first get x.
then, i guess, pick a window manager.
then pick a base desktop enviornment.
then pick sound manager.
then a video card driver.

etc.

---

### Post by skymera on 2008-12-03
I'm guessing so yes. Sounds like a good plan.

Try to avoid ubuntu-desktop and gnome-desktop as they will install a lot of junk.

Tell me how it goes and if it's worth doing in future.

---

### Post by earthpigg on 2008-12-03
ok, i will.

and yes, ill have to avoid the meta packages... (why the hell can't i uninstall evolution without uninstalling ubuntu-desktop metapackage again? lol...)

---

### Post by _sAm_ on 2008-12-03
I have uninstalled evolution without removing the gnome-desktop. Just read about the packages in Synaptic so you pick the right one.

Here is two guides about what you want:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

---

### Post by loomsen on 2008-12-03
> will ubuntu-minimal detect my network and connect, etc?

Make sure you're connected by wire and dhcp is enabled in your network. This even works out of the BIOS, networking isn't hard to set up.


Step by Step:

1.) Get a netinstall iso image.

vvvvA) Either visit [www.instalinux.com](www.instalinux.com) and chose a distro, but none of the metapackages. This will generate a 10MB sized iso you can burn/create a USB startup from or so.

vvvvB) I'd recommend [unetbootin. Basically the same as instalinux, but it offers even more distros and options to chose from, yet being pretty simple.](https://sourceforge.net/project/showfiles.php?group_id=222386)

2.) Make sure you feel comfortable in a shell

3.) Pull one of the mentioned meta-packages in. I use to choose between ubuntu-minimal and ubuntu-standard, plus gnome-core or gnome-common.

4.) Get further modules/drivers/what you want, and enjoy a lightweight system you KNOW! Hence most of the pkges are chosen by YOU, you get another feeling for your system as well.



5.) Try and mind HowTos tweaking anything, you will do that yourself as far as you'd like. And if you don't know how, time will tell. So, don't try and tweak your sys to death.

---

### Post by earthpigg on 2008-12-03
awesome, loomsen.

is there a concise list of metapackages for ubuntu floating around anywhere that you know of?

ie: things 'below' ubuntu-desktop, and above 'ubuntu-minimal'?

---

### Post by loomsen on 2008-12-03
Yep, ubuntu-standard :)

Open up you synaptic and sort by sections. 

[[img]http://www.ubuntu-pics.de/thumb/6724/screenshot_08_JvyVU6.png[/img]](http://www.ubuntu-pics.de/bild/6724/screenshot_08_JvyVU6.png)

These are available metapackages. But note, after your installation it won't look like this.
You'll just get a shell login.

So, before you run your insta, better think again what you might need from the shell, or what you should make easily accessible or so.

For example, I have a directory I can easily access from a shell. Before installing a new OS (I install/maintain friends OS' a lot too) I make sure to place everything useful into that dir. Like for example my sources.list, my trusted.gpg key file, my bash_aliases, some custom packages and so on. So from the shell I have everything easily available.

This might take some installs, but you will notice what to do better next time, which packages to pull in and so on simply by the essential means of missing tools.

[color=blue]You'd probably want to pull in ubuntu-standard and gnome-core. [/color]

HINT: You'll be prompted what will happen before any installation is processed, and asked to confirm. So simply run 
sudo apt-get install <metapackagename>
and see what it would do to your sys.

> 
docter[~] sudo apt-get install gnome
Reading package lists... Done
Building dependency tree      
------------SNIP------------
------------SNIP------------
0 upgraded, 221 newly installed, 0 to remove and 0 not upgraded.
Need to get 189MB of archives.
After this operation, 724MB of additional disk space will be used.
Do you want to continue [Y/n]? 


So if you're unsure if you prefer gnome-core or gnome-common, pull both in and look what would happen for each. Just hit **n** to abort.

---

### Post by Joeb454 on 2008-12-03
> **earthpigg said:**
> (why the hell can't i uninstall evolution without uninstalling ubuntu-desktop metapackage again? lol...)

You can.

Just don't use aptitude. I believe ```
sudo apt-get remove --purge evolution
``` should work.

Either way, I know I don't have it on my system (I'll even provide a screenshot if you want). :)

---

### Post by earthpigg on 2008-12-03
thanks again, loomsen.

related question: the most exhaustive set of official ubuntu repos with the most packages available is the set of studio edition repos, right?

---

### Post by loomsen on 2008-12-03
Humm, can't tell you that tbh... I usually just uncomment what is to be uncommented in the default sources.list and add my custom.list to /etc/apt/sources.list.d/custom.list

Here's my actual custom.list (but it's more like a dynamic list, sometimes I feel like deleting sth, other times I stumble upon a list and add parts of it to mine)

This one, however, is the one I'm using atm:
```

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
#KeyFetch: http http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ intrepid free non-free
deb-src http://packages.medibuntu.org/ intrepid free non-free
deb http://packages.medibuntu.org/ intrepid-staging non-free free
deb-src http://packages.medibuntu.org/ intrepid-staging free non-free

# _Kernel_ & gimp
deb http://ppa.launchpad.net/c-korn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/c-korn/ubuntu intrepid main

# _PackageKit_
deb http://ppa.launchpad.net/packagekit/ubuntu intrepid main

# 		shame compiz
# wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
# deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./
# 		compiz PPA
# deb http://ppa.launchpad.net/compiz/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main

# 		gmusicbrowser
deb http://squentin.free.fr/gmusicbrowser ./

# 		GNOME Do
# deb http://ppa.launchpad.net/do-core/ubuntu intrepid main

# 		gscrot
deb http://ppa.launchpad.net/gscrot/ubuntu intrepid main
deb-src http://ppa.launchpad.net/gscrot/ubuntu intrepid main

# 	Opera (finally 64 bit support!)
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --fingerprint 6A423791
# gpg --armor --export 6A423791| apt-key add -
#KeyFetch: http http://deb.opera.com/archive.key
# _Opera_
deb http://deb.opera.com/opera/ sid non-free

# 		Cairo
# deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock

#		NETWORK MANAGER
deb http://ppa.launchpad.net/network-manager/ubuntu intrepid main

#		INKSCAPE
deb http://ppa.launchpad.net/towolf/ubuntu intrepid main

# _Gwibber_
deb http://ppa.launchpad.net/gwibber-team/ubuntu intrepid main

# 		PulseAudio Fixes & Adobe Flash - Preview Packages (psyke83)
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main

# _WebKit_
deb http://ppa.launchpad.net/webkit-team/ubuntu intrepid main
deb http://ppa.launchpad.net/stemp/ubuntu intrepid main

# _SMPlayer_
deb http://ppa.launchpad.net/themono/ubuntu intrepid main

# _Picard (client MusicBrainz)_
deb http://ppa.launchpad.net/phw/ubuntu intrepid main

# _Mupen64+_
deb http://ppa.launchpad.net/phobie/ubuntu intrepid main

# _Rosegarden_ _Ardour_
deb http://ppa.launchpad.net/volans/ubuntu intrepid main

# _Gammu__Geeqie__GSynaptics_
deb http://ppa.launchpad.net/nijel/ubuntu intrepid main

# _Cairo Composite Manager_
# deb http://ppa.launchpad.net/gandalfn/ubuntu hardy main universe multiverse restricted

# _DCraw_
deb http://ppa.launchpad.net/bruce89/ubuntu/ intrepid main universe multiverse restricted

# _PlayDeb_
# deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
deb mirror://www.getdeb.net/playdeb-mirror/intrepid/// intrepid/

# _Exaile_
# deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main

# _FluxBox_
deb http://ppa.launchpad.net/r0rschach/ubuntu intrepid main

# 		Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/

# 		Ubuntu Tweak
#deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
#deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

## Intrepid Themes
deb http://ppa.launchpad.net/kwwii/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kwwii/ubuntu intrepid main

## Google
deb http://dl.google.com/linux/deb/ stable non-free

## Additional
deb http://ppa.launchpad.net/mvo/ubuntu intrepid main

# Empathy/Telepath
#deb http://ppa.launchpad.net/telepathy/ubuntu intrepid main
#deb-src http://ppa.launchpad.net/telepathy/ubuntu intrepid main

```

This should provide anything you need. 

For instance, one common mistake is to pull ALSA, ESD, OSS and PULSE.

One of them will work just as well. I'm using pulse atm, so I pulled the plugins in I make use of (i.e. I don't use schroedinger for instance, so I don't need the respective gstreamer-libschroedinger plugin. This is a simple example, tho shows how to handle things. I try and read many manuals from installed packages as well, rather than installing more and more. You'd be surprised how many powerful packages you prlly already have installed without knowing.)

Oh, and try and get used to making excessive use of <TAB> for auto completion in your shell. In the meanwhile I'm hitting TAB nearly after every single letter I type in. If you hit TAB, but completion isn't unique, just hit TAB again to get a list of possible values.

> 
[color=red]docter[~][/color] in
in                      insserv                 interdiff
includeres              install                 intltool-extract
info                    install-docs            intltoolize
infobrowser             installed_alternatives  intltool-merge
infocmp                 install-info            intltool-prepare
infokey                 installkernel           intltool-update
infotocap               install-menu            invest-chart
init                    install-sgmlcatalog     invoke-rc.d
initctl                 installwatch            
insmod                  instmodsh               
[color=red]docter[~][/color] in


Just typed in and hit TAB twice in this example.


*edit*
[Had a similar discussion recently here, maybe you want to take a look at too.](http://ubuntuforums.org/showthread.php?t=1000024)

---

### Post by earthpigg on 2008-12-03
thanks for the tips.

and yeah, i meant to say mediabuntu ;)

im familiar with adding things to my sources.list so i wont be using yours, but you answered my question and then some.

---

### Post by earthpigg on 2008-12-03
one final question,

what part/package of 8.10 was able to pick up my wireless that 8.04 likely did not have?

---

### Post by bhadotia on 2008-12-03
> **earthpigg said:**
> one final question,

what part/package of 8.10 was able to pick up my wireless that 8.04 likely did not have?

Post the output of:
```
sudo  lshw -C network
```
and we'll try to tell.:popcorn:

---

### Post by earthpigg on 2008-12-03
soon as i get home i will ;)

---

### Post by earthpigg on 2008-12-04
```
ep@ep-laptop:~$ sudo  lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:62:cb:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ed:e2:3e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:fd:52:94:20:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ep@ep-laptop:~$ 

```

:)

edit: awesome thread btw, learning a lot... thanks folks!

---

### Post by bhadotia on 2008-12-04
You have the intel 3945 wi-fi card (same as mine). The driver (iwl3945) for it is now a part of the linux kernel. But prior to Intrepid (more exactly in the linux kernel 2.6.24 and before), the  driver came as a seperate package but it was installed by default if the card was detected (as it was available in the installation CD). I don't know why you had a problem with your wi-fi card not being detected mine was always detected (7.10 through 8.10). If, of course, you were trying to do a minimal install then you might have had problem because you need to install the firmware (iwl-3945-ucode) manually (even if udev has detected the card).

---

### Post by earthpigg on 2008-12-04
so, anything with 2.6.24 should detect my wifi card?

for example, an up to date 8.04 install?

---

### Post by bhadotia on 2008-12-05
> **earthpigg said:**
> so, anything with 2.6.24 should detect my wifi card?

for example, an up to date 8.04 install?

No, it actually depends on the udev version of the distro you are using. But any ubuntu (and among the distros I have tried Mandriva, Fedora, Arch Linux, Suse, PCLOS)will detect your wifi card.

---

